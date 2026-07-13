# Building a custom alarm, because I want something really cool
Using Claude to assist me, because this is new ground for me
## Project Overview
I wanted a unique alarm that was more than just music or a ringtone. I wanted an alarm that could truly get me ready for the day. The base idea was that I would have some music start the alarm, and then have a voice inspired by Jarvis from Iron Man greet me and give me the weather, football scores (when SNF is happening), a daily agenda (from items I have on a calendar for that day), and the news, spoken to me as I'm waking up. I might also add some other pieces, like a clip of Kevin James yelling "Ladies and gentlemen, start your engines", or some more funny things.

## Here is Claude's attempt at one-shotting it:
# Jarvis Alarm — Setup Guide

A morning alarm that plays music, then narrates weather, your calendar, sports scores,
and news over the music (ducked in the background), in a JARVIS-style voice.

Built and smoke-tested piece by piece: weather/calendar/sports/news modules, the script
writer, TTS, and the audio ducking/mixing all run correctly (with graceful placeholder
fallbacks whenever a data source is unreachable or not yet configured).

## 1. Install (on your Debian laptop)

```bash
sudo apt update
sudo apt install -y ffmpeg espeak-ng python3-venv
cd jarvis-alarm
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## 2. Configure

```bash
cp config.example.json config.json
```

Edit `config.json`:

- `location.latitude` / `longitude` — for weather. Yours are pre-filled.
- `anthropic_api_key` — get one at console.anthropic.com if you want the LLM-written script
  (much more natural). Leave blank to use the built-in template writer instead — it works,
  just less fluid.
- `sports.favorite_teams` — must match ESPN's team display names, e.g. `"Seattle Seahawks"`.
- `news.categories` — map a label to any RSS feed URL. Swap in whatever sources you trust
  for "Christian News" etc. Any site with an RSS feed works.
- `tts.engine` — `"gtts"` (free, no key, decent quality) or `"elevenlabs"` (paid, best quality,
  needs `elevenlabs_api_key` and `elevenlabs_voice_id`).
- `audio.intro_music_file` — path to an mp3 you own. Drop a file into `music/` and point to it.

## 3. (Optional) Google Calendar setup

Only needed if you want real calendar events instead of placeholder ones.

1. Go to console.cloud.google.com, create a project.
2. Enable the "Google Calendar API".
3. Create OAuth credentials (Desktop app type), download as `credentials.json` into this folder.
4. In `config.json`, set `google_calendar.enabled` to `true`.
5. Install the extra packages: `pip install google-auth google-auth-oauthlib google-api-python-client`.
6. First run will open a browser for you to authorize — after that it's silent.

If you skip this, the calendar module returns your example schedule (Class 101, Class 102,
poster, RA duty) as placeholders so you can still test everything else.

## 4. Test it

```bash
python3 src/main.py --no-play          # build the file, print the script, don't play audio
python3 src/main.py --fallback-script  # skip the Claude API call, use the free template writer
python3 src/main.py                    # full run, plays the result out loud
```

Output audio lands at `output/morning_briefing.mp3` — listen to it directly if you don't
want it auto-played.

## 5. Schedule it to run automatically

**Simplest (recommended to start): leave the laptop on overnight, plugged in, sleep disabled.**

```bash
crontab -e
```

Add a line (adjust the path and time):

```
0 7 * * * cd /home/you/jarvis-alarm && venv/bin/python3 src/main.py >> logs/run.log 2>&1
```

This runs the script every day at 7:00 AM.

**More power-efficient later: suspend + `rtcwake`.**

Instead of leaving it on, you can suspend the laptop and have it wake itself:

```bash
# schedule a wake for 6:59 AM tomorrow, then suspend now
sudo rtcwake -m mem -t $(date -d 'tomorrow 06:59' +%s)
```

Pair this with a systemd timer (instead of cron) so the briefing script fires right after
`rtcwake` brings the machine back up, and a script that re-arms the next `rtcwake` call
each night. This is a bit more moving parts — get the cron version working first, then
graduate to this once you're happy with the pipeline.

## 6. Audio output

By default this plays through whatever `ffplay` treats as the system default output —
i.e. your laptop speakers. To send it to a Bluetooth speaker or your phone instead:

```bash
bluetoothctl
# pair / connect your device, then set it as the default audio sink in your Linux
# sound settings (pavucontrol is the easiest GUI for this: `sudo apt install pavucontrol`)
```

Once the Bluetooth device is the default sink, no code changes needed — `ffplay` just
uses whatever the system default is.

## Project structure

```
jarvis-alarm/
├── config.example.json      # copy to config.json and fill in
├── requirements.txt
├── music/                   # put your intro music mp3 here
├── output/                  # generated voice + final mixed briefing land here
└── src/
    ├── main.py               # orchestrator - this is what cron runs
    ├── script_writer.py       # turns raw data into the spoken script (Claude API or template)
    ├── tts.py                 # text -> speech (gTTS or ElevenLabs)
    ├── audio_mixer.py          # music + voice ducking/crossfade
    └── data_sources/
        ├── weather.py         # NWS API, no key needed
        ├── calendar.py        # Google Calendar, OAuth (optional)
        ├── sports.py          # ESPN public API, no key needed
        └── news.py            # RSS feeds, no key needed
```

## Extending it

- Add more sports leagues: `sports.get_recent_scores(teams, league="nba")`.
- Change the register/personality: edit `JARVIS_SYSTEM_PROMPT` in `script_writer.py`.
- Different voice: swap `elevenlabs_voice_id`, or change the `tld` in `tts.py`'s gTTS call
  for a different accent.
- Weekday vs weekend profiles: check `datetime.now().weekday()` in `main.py` and load a
  different config or skip the "class schedule" section on weekends.
  # 

{
  "user_name": "sir",
  "location": {
    "label": "Williamsville, NY",
    "latitude": 42.9628,
    "longitude": -78.7387
  },
  "alarm_time_24h": "06:00",

  "anthropic_api_key": "sk-ant-...",

  "google_calendar": {
    "enabled": false,
    "credentials_file": "credentials.json",
    "token_file": "token.json",
    "calendar_ids": ["primary"]
  },

  "sports": {
    "enabled": true,
    "favorite_teams": ["Seattle Seahawks"]
  },

  "news": {
    "enabled": true,
    "categories": {
      "US News": "https://feeds.npr.org/1003/rss.xml",
      "Tech News": "https://feeds.arstechnica.com/arstechnica/index",
      "Christian News": "https://www.christianitytoday.com/ct/rss.xml"
    },
    "max_headlines_per_category": 3
  },

  "tts": {
    "engine": "gtts",
    "elevenlabs_api_key": "",
    "elevenlabs_voice_id": ""
  },

  "audio": {
    "intro_music_file": "c:\Users\Zephrym\Music\MP3 Music 2-15-2026\Power Metal\Orden Ogan\In the Dawn of the AI.mp3",
    "intro_seconds_before_duck": 10,
    "duck_volume_db": -18,
    "fade_ms": 2500,
    "output_file": "output/morning_briefing.mp3"
  }
}
#### At this point in the project, I can't say that I fully understand how everything is supposed to fit together. This is a foray into app development that I've never done before, as my focus is networks and systems
