# Music Store Inventory Database

### Designed by myself in conjunction with a few other classmates for a final project in a Systems Analysis class

## Section I - SQL Queries for Database Generation:

### Creating a table for product vendors (ex. Sweetwater, Western Sound LLC., etc.)
CREATE TABLE vendor
(
    VendorID CHAR(7) NOT NULL,
    VendorName CHAR(25) NOT NULL,
    PRIMARY KEY (VendorID)
);
### Creating a table for product brands (ex. Fender, Ibanez, Gibson, Marshall, etc.)
CREATE TABLE brand
(
    brandID CHAR(8) NOT NULL,
    brandName VARCHAR(25) NOT NULL,
    vendorid CHAR(7) NOT NULL,
    PRIMARY KEY (brandID),
    FOREIGN KEY (vendorid) REFERENCES vendor(VendorID)
);
### Creating a table for equipment (Every individual piece of equipment has a different ID number, allowing for expedited shipping and recieving procedures. Also includes equipment type (ex. Guitar, synthesizer, amp, microphone, etc.) for reference as well as a model name (ex. Fender Tone Master Pro) and the model weight (for shipping, loading, and lifting purposes)
CREATE TABLE equipment
(
    brandID CHAR(8) NOT NULL,
    equipmentID CHAR(8) NOT NULL,
    equipmentType CHAR(25),
    modelName VARCHAR(60) NOT NULL,
    modelWeight FLOAT,
    PRIMARY KEY (equipmentID),
    FOREIGN KEY (brandID) REFERENCES brand(brandID)
);
### Every customer has an ID that is used to keep track of their case as well as payment information and information about their specific case.
CREATE TABLE customer
(
    CustomerID CHAR(10) NOT NULL,
    CustomerName CHAR(25) NOT NULL,
    PRIMARY KEY (CustomerID)
);

CREATE TABLE CustomerCaseFile
(
    CustomerCaseID VARCHAR(16) NOT NULL,
    CustomerID CHAR(10) NOT NULL,
    PRIMARY KEY (CustomerCaseID),
    FOREIGN KEY (CustomerID) REFERENCES customer(CustomerID)
);

CREATE TABLE Reserved
(
    equipmentID CHAR(8) NOT NULL,
    ReservedStatus INT NOT NULL,
    ReservedStartDate DATE NOT NULL,
    ReservedEndDate DATE,
    CustomerID CHAR(10) NOT NULL,
    CustomerCaseID VARCHAR(16) NOT NULL,
    PRIMARY KEY (equipmentID, ReservedStartDate),
    FOREIGN KEY (CustomerID) REFERENCES Customer(CustomerID),
    FOREIGN KEY (CustomerCaseID) REFERENCES CustomerCaseFile(CustomerCaseID)
);

CREATE TABLE worker
(
    workerID INT NOT NULL,
    HireDate DATE NOT NULL,
    TerminationDate DATE NULL,
    WorkerName VARCHAR(255) NOT NULL,
    WorkerDateOfBirth DATE NOT NULL,
    WorkerSSN VARCHAR(11) NOT NULL,
    WorkerPhone VARCHAR(15) NOT NULL,
    Salary FLOAT NOT NULL,
    WorkerAddress VARCHAR(255) NOT NULL,
    PRIMARY KEY (WorkerID)
);

CREATE TABLE workerSchedule
(
    workerID INT NOT NULL,
    ScheduleDate DATE NOT NULL,
    ShiftStart TIME NOT NULL,
    ShiftEnd TIME NOT NULL,
    Hours DECIMAL(5,2) NOT NULL,
    PRIMARY KEY (workerID, ScheduleDate),
    FOREIGN KEY (workerID) REFERENCES worker(workerID)
);
### Future additions of this database could further integrate the worker information, allowing for scheduling to be done entirely through the SSL back-end of the website. Additionally, the POS system could be integrated with the online system.

