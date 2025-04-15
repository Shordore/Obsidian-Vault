
CREATE TABLE Traveler (name VARCHAR(50) NOT NULL, ssn INT PRIMARY KEY, dob DATE);

CREATE TABLE Trip (id INT PRIMARY KEY, start_location VARCHAR(50), end_location VARCHAR(50), start_date DATE, end_date DATE, CHECK (end_date >= start_date));

CREATE TABLE TravelAgent ( name VARCHAR(50) PRIMARY KEY, years_experience INT CHECK (years_experience >= 1), phone VARCHAR(50));


CREATE TABLE Passport (passport_number INT, country VARCHAR(50), expirationDate DATE, holderName VARCHAR(50), PRIMARY KEY (passport_number, country), CHECK (expirationDate > '2020-01-01'));


CREATE TABLE Owns (ssn INT, passport_number INT, country VARCHAR(50), PRIMARY KEY (ssn, passport_number, country), FOREIGN KEY (ssn) REFERENCES Traveler(ssn) ON UPDATE CASCADE ON DELETE CASCADE);


CREATE TABLE Booking (traveler_ssn INT, trip_id INT, agent VARCHAR(50), PRIMARY KEY (traveler_ssn, trip_id), FOREIGN KEY (traveler_ssn) REFERENCES Traveler(ssn) ON UPDATE CASCADE ON DELETE CASCADE, FOREIGN KEY (trip_id) REFERENCES Trip(id), FOREIGN KEY (agent) REFERENCES TravelAgent(name) ON DELETE SET NULL);


CREATE TABLE GoesOn ( ssn INT, id INT, PRIMARY KEY (ssn, id), FOREIGN KEY (ssn) REFERENCES Traveler(ssn)  ON UPDATE CASCADE  ON DELETE CASCADE, FOREIGN KEY (id) REFERENCES Trip(id));


CREATE TABLE Leg (trip_id INT, startLocation VARCHAR(50), endLocation VARCHAR(50), startDate DATE, endDate DATE, PRIMARY KEY (trip_id, startLocation, endLocation), FOREIGN KEY (trip_id) REFERENCES Trip(id), CHECK (endDate >= startDate));


Insert Statements:
-- Traveler
INSERT INTO Traveler (name, ssn, dob) VALUES
('John Doe', 101, '1985-06-12'),
('Alice Brown', 102, '1992-03-05'),
('Mike Johnson', 103, '1998-09-17'),
('Lisa Turner', 104, '2000-12-22'),
('Sarah Connor', 105, '2003-11-01');

-- TravelAgent
INSERT INTO TravelAgent (name, years_experience, phone) VALUES
('Emily Clark', 12, '123-456-7890'),
('Robert Smith', 8, '234-567-8901'),
('Anna Wilson', 15, '345-678-9012'),
('Michael Davis', 10, '456-789-0123'),
('Mary Johnson', 3, '567-890-1234');

-- Trip
INSERT INTO Trip (id, start_location, end_location, start_date, end_date) VALUES
(201, 'New York', 'Paris', '2023-07-10', '2023-07-20'),
(202, 'Tokyo', 'Sydney', '2023-08-01', '2023-08-15'),
(203, 'London', 'Rome', '2023-09-05', '2023-09-15'),
(204, 'Berlin', 'Tokyo', '2023-10-02', '2023-10-12'),
(205, 'Miami', 'New York', '2023-10-22', '2023-10-29');

-- Passport
INSERT INTO Passport (passport_number, country, expirationDate, holderName) VALUES
(3001, 'USA', '2025-11-30', 'John Doe'),
(3002, 'Canada', '2026-08-20', 'Alice Brown'),
(3003, 'UK', '2024-09-15', 'Mike Johnson'),
(3004, 'Australia', '2027-02-10', 'Lisa Turner'),
(3005, 'France', '2023-12-05', 'Sarah Connor');

-- Insert into Owns
INSERT INTO Owns (ssn, passport_number, country) VALUES
(101, 3001, 'USA'),
(102, 3002, 'Canada'),
(103, 3003, 'UK'),
(104, 3004, 'Australia'),
(105, 3005, 'France');

-- Insert into Booking
INSERT INTO Booking (agent, traveler_ssn, trip_id) VALUES
('Emily Clark', 101, 201),
('Robert Smith', 102, 202),
('Anna Wilson', 103, 203),
('Michael Davis', 104, 204),
('Emily Clark', 105, 205);

-- Insert into GoesOn
INSERT INTO GoesOn (ssn, id) VALUES
(101, 201),
(102, 202),
(103, 203),
(104, 204),
(105, 205);

-- Insert into Leg
INSERT INTO Leg (trip_id, startLocation, endLocation, startDate, endDate) VALUES
(201, 'New York', 'Paris', '2023-07-10', '2023-07-20'),
(202, 'Tokyo', 'Sydney', '2023-08-01', '2023-08-15'),
(203, 'London', 'Rome', '2023-09-05', '2023-09-15'),
(204, 'Berlin', 'Tokyo', '2023-10-02', '2023-10-12'),
(205, 'Miami', 'New York', '2023-10-22', '2023-10-29');

Part 4 Triggers:


Trigger 1:
CREATE TABLE DeletedTravelerLog (ssn INT, name VARCHAR(50));


DELIMITER //

CREATE TRIGGER Trig1
BEFORE DELETE  ON Traveler
FOR EACH ROW
BEGIN
INSERT INTO DeletedTravelerLog(ssn, name) VALUES (OLD.ssn, OLD.name);
END;

// DELIMITER;

Trigger 2:
CREATE TABLE TravelerStats (ssn INT PRIMARY KEY, trip_count INT DEFAULT 0);

DELIMITER //

CREATE TRIGGER Trig2
AFTER INSERT ON GoesOn
FOR EACH ROW
BEGIN
INSERT INTO TravelerStats (ssn, trip_count) VALUES (NEW.ssn, 1) ON DUPLICATE KEY UPDATE trip_count = trip_count + 1;
END;
// DELIMITER;

Part 5 Constraint Scenarios:

1.`DELETE FROM Trip WHERE id = 201
![[Pasted image 20250415144402.png
This fails because the trip id is still being referenced by the booking table constraint. Since it is still being used it is protected from deletion.

2.`UPDATE Owns SET ssn = 999 WHERE ssn = 101;`
![[Pasted image 20250415144507.png]]
Since there is no ssn in Traveler with 999 it fails to be updated in Owns.

3.`INSERT INTO TravelAgent VALUES ("Jake Taylor", 0, "678-901-2345");`
![[Pasted image 20250415145238.png]]
The check constraint on TravelAgent requires years_experience to be at least 1, to which this is 0.

4.`UPDATE Passport SET expirationDate = "2018-12-01" WHERE passport_number = 3001;`
![[Pasted image 20250415145304.png]]
This happened because the expiration date was less than the constraint.

5.`INSERT INTO Trip VALUES (206,"Paris", "Berlin", "2023-12-10", "2023-12-01");`
![[Pasted image 20250415145409.png]]
The constraint in Trip requires that the end date is after the start date which this violates.

6.`UPDATE Traveler SET ssn = 106 WHERE ssn = 102;`
![[Pasted image 20250415145614.png]]
Due to the update cascade rule the related info in Bookings, Owns, and GoesOn get updated when an ssn changes.

7.`DELETE FROM TravelAgent WHERE name LIKE "Emily Clark";`
![[Pasted image 20250415145813.png]]
Due to ON DELETE SET NULL when an agent is deleted all bookings they have made get their name set to null in Bookings.

8.`INSERT INTO Traveler VALUES (NULL, 107, "2001-05-10");`
![[Pasted image 20250415145928.png]]
Traveler name column is explicitly not null, so attempting to input a null value leads to the error.

9.`DELETE FROM Traveler WHERE ssn = 103;`
![[Pasted image 20250415150208.png]]
![[Pasted image 20250415150218.png]]
Due to the trigger when a traveler is deleted their information get automatically relayed to the DeletedTravelerLog before the deletion is made.


10.`INSERT INTO GoesOn VALUES (104, 205);`
![[Pasted image 20250415150251.png]]
Due to the trigger after inserting into GoesOn, an update is made to the TravelerStats table which lists the ssn of the Traveler, and updates the trip counter to add one.