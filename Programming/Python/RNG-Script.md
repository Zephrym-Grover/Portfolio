# Random Number Generator Scripts

### Not entirely sure when these will be useful, but I'm making these for myself anyway just to have in case I need them, as I see a variety of uses for them


# Dice Generators (for roleplaying games, all should be set to allow for the rolling of multiple dice of that type simultaneously

## Coin flip
import random
ResultsArray = []
NumberOfTimes = int(input("How many coins are you flipping"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,2)
    if x == 1:
        ResultsArray.append("Heads")
    else:
        ResultsArray.append("Tails")
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D4
import random
ResultsArray = []
NumberOfTimes = int(input("How many 4 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,4)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D6
import random
ResultsArray = []
NumberOfTimes = int(input("How many 6 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,6)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D8
import random
ResultsArray = []
NumberOfTimes = int(input("How many 8 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,8)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D10
import random
ResultsArray = []
NumberOfTimes = int(input("How many 10 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(0,9)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)

## D% (Designed to work how a classic set of D% dice work, wheras the D100 works on just generating out of 100)
import random
ResultsArray = []
NumberOfTimes = int(input("How many D% sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(0,9)
    y = random.randint(0,9)
    ResultsArray.append(y+x*10)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D12
import random
ResultsArray = []
NumberOfTimes = int(input("How many 12 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,12)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D20
import random
ResultsArray = []
NumberOfTimes = int(input("How many 20 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,20)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)

## D24
import random
ResultsArray = []
NumberOfTimes = int(input("How many 24 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,24)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D32
import random
ResultsArray = []
NumberOfTimes = int(input("How many 32 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,32)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D60
import random
ResultsArray = []
NumberOfTimes = int(input("How many 60 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,60)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D64
import random
ResultsArray = []
NumberOfTimes = int(input("How many 64 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,64)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
## D100
import random
ResultsArray = []
NumberOfTimes = int(input("How many 100 sided dice are you rolling?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,100)
    ResultsArray.append(x)
    count = count + 1

print("Your Result(s):")
print(ResultsArray)
# Time generator scripts

## Minute-of-the-hour generator
import random
ResultsArray = []
NumberOfTimes = int(input("How many minutes are you generating?"))
count = 0
while count < NumberOfTimes:
    x = random.randint(1,60)
    ResultsArray.append(x)
    count = count + 1
for i in range(len(ResultsArray)):
    ResultsArray[i] = f":{ResultsArray[i]}"

print("Your minutes:")
print(ResultsArray)
## Hour of the day generator
import random
ResultsArray = []
numberOfTimes = int(input("How many hours would you like to generate?"))
count = 0
while count < numberOfTimes:
    x = random.randint(1,24)
    if x > 12:
        x = f"{x - 12}PM"
    else:
       x = f"{x}AM" 
    ResultsArray.append(x)
    count = count + 1
print("your minutes")
print(ResultsArray)
## Minute of the day generator

## Day of the week generator

## Day of the month generator

## Month of the year generator

## Day of the year generator

# R.A. Stuff

## R.A. Round Time Generator (Weekdays)

## R.A. Round Time Generator (Weekends)

## Month of the semester

# Example Generators

## Name generator (Male)

## Name generator (Female)

## E-Mail Generator

## Phone Number Generator (U.S.)






