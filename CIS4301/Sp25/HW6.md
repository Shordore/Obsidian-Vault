<b>Part 2 Tables:</b>

<b>Traveler:</b>
`CREATE TABLE Traveler (name VARCHAR(50) NOT NULL, ssn INT PRIMARY KEY, dob DATE);`

<b>Trip:</b>
`CREATE TABLE Trip (id INT PRIMARY KEY, start_location VARCHAR(50), end_location VARCHAR(50), start_date DATE, end_date DATE, CHECK (end_date >= start_date));`

<b>TravelAgent:</b>
`CREATE TABLE TravelAgent ( name VARCHAR(50) PRIMARY KEY, years_experience INT CHECK (years_experience >= 1), phone VARCHAR(50));`

<b>Passport:</b>
`CREATE TABLE Passport (passport_number INT, country VARCHAR(50), expirationDate DATE, holderName VARCHAR(50), PRIMARY KEY (passport_number, country), CHECK (expirationDate > '2020-01-01'));`

<b>Owns:</b>
`CREATE TABLE Owns (ssn INT, passport_number INT, country VARCHAR(50), PRIMARY KEY (ssn, passport_number, country), FOREIGN KEY (ssn) REFERENCES Traveler(ssn) ON UPDATE CASCADE ON DELETE CASCADE);`


<b>Booking:</b>
`CREATE TABLE Booking (traveler_ssn INT, trip_id INT, agent VARCHAR(50), PRIMARY KEY (traveler_ssn, trip_id), FOREIGN KEY (traveler_ssn) REFERENCES Traveler(ssn) ON UPDATE CASCADE ON DELETE CASCADE, FOREIGN KEY (trip_id) REFERENCES Trip(id), FOREIGN KEY (agent) REFERENCES TravelAgent(name) ON DELETE SET NULL);`


<b>GoesOn:</b>
`CREATE TABLE GoesOn ( ssn INT, id INT, PRIMARY KEY (ssn, id), FOREIGN KEY (ssn) REFERENCES Traveler(ssn)  ON UPDATE CASCADE  ON DELETE CASCADE, FOREIGN KEY (id) REFERENCES Trip(id));`


<b>Leg:</b>
`CREATE TABLE Leg (trip_id INT, startLocation VARCHAR(50), endLocation VARCHAR(50), startDate DATE, endDate DATE, PRIMARY KEY (trip_id, startLocation, endLocation), FOREIGN KEY (trip_id) REFERENCES Trip(id), CHECK (endDate >= startDate));`



<b>Part 4 Triggers:</b>


Trigger 1:
`CREATE TABLE DeletedTravelerLog (ssn INT, name VARCHAR(50));`


```
DELIMITER //

CREATE TRIGGER Trig1
BEFORE DELETE  ON Traveler
FOR EACH ROW
BEGIN
INSERT INTO DeletedTravelerLog(ssn, name) VALUES (OLD.ssn, OLD.name);
END;

// DELIMITER;
```

Trigger 2:
`CREATE TABLE TravelerStats (ssn INT PRIMARY KEY, trip_count INT DEFAULT 0);`

```
DELIMITER //

CREATE TRIGGER Trig2
AFTER INSERT ON GoesOn
FOR EACH ROW
BEGIN
INSERT INTO TravelerStats (ssn, trip_count) VALUES (NEW.ssn, 1) ON DUPLICATE KEY UPDATE trip_count = trip_count + 1;
END;
// DELIMITER;
```

<b>Part 5 Constraint Scenarios:</b>

1.`DELETE FROM Trip WHERE id = 201;`
![[Pasted image 20250415144402.png]]
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