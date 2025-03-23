
Table commands:

CREATE TABLE GoesOn(
ssn INT,
id INT,
PRIMARY KEY (ssn, id),
FOREIGN KEY (ssn) REFERENCES Traveler(ssn) ON DELETE CASCADE,
FOREIGN KEY (id) REFERENCES Trip(id) ON DELETE CASCADE
);

CREATE TABLE Leg(
trip_id INT,
startLocation VARCHAR(50),
endLocation VARCHAR(50),
startDate DATE,
endDate DATE,
PRIMARY KEY(trip_id, startLocation, endLocation, startDate),
FOREIGN KEY (trip_id) REFERENCES Trip(id) ON DELETE CASCADE
);

CREATE TABLE Owns(
ssn INT,
passportNum INT,
country VARCHAR(50),
PRIMARY KEY(ssn, passportNum),
FOREIGN KEY(ssn) REFERENCES Traveler(ssn) ON DELETE CASCADE,
FOREIGN KEY (passportNum) REFERENCES Passport(passportNum) ON DELETE CASCADE
);

CREATE TABLE Passport(
passportNum INT PRIMARY KEY,
country VARCHAR(50),
expDate DATE,
holderName VARCHAR(50)
);

Insert Commands:

INSERT INTO GoesOn (ssn, id) VALUES
(101, 201),
(101, 208),
(102, 202),
(102, 205),
(103, 203),
(103, 206),
(106, 206),
(106, 201),
(107, 207),
(108, 208);

INSERT INTO Leg (trip_id, startLocation, endLocation, startDate, endDate) VALUES
(201, ’New York’, ’London’, ’2025-07-10’, ’2025-07-12’),
(201, ’London’, ’Paris’, ’2025-07-13’, ’2025-07-20’),
(202, ’Tokyo’, ’Seoul’, ’2025-08-01’, ’2025-08-05’),
(202, ’Seoul’, ’Sydney’, ’2025-08-06’, ’2025-08-15’),
(203, ’London’, ’Berlin’, ’2025-09-05’, ’2025-09-08’),
(203, ’Berlin’, ’Rome’, ’2025-09-09’, ’2025-09-15’),
(204, ’Miami’, ’Atlanta’, ’2025-06-15’, ’2025-06-17’),
(204, ’Atlanta’, ’New York’, ’2025-06-18’, ’2025-06-20’),
(205, ’San Francisco’, ’Frankfurt’, ’2025-10-01’, ’2025-10-06’),
(205, ’Frankfurt’, ’Berlin’, ’2025-10-07’, ’2025-10-10’),
(206, ’Chicago’, ’Denver’, ’2025-09-10’, ’2025-09-11’),
(206, ’Denver’, ’Los Angeles’, ’2025-09-12’, ’2025-09-12’),
(207, ’Boston’, ’Dubai’, ’2025-07-05’, ’2025-07-10’),
(207, ’Dubai’, ’Singapore’, ’2025-07-11’, ’2025-07-18’),
(208, ’New York’, ’Istanbul’, ’2025-09-10’, ’2025-09-12’),
(208, ’Istanbul’, ’Dubai’, ’2025-09-13’, ’2025-09-15’);

INSERT INTO Owns (ssn, passportNum, country) VALUES
(101, 5001, ’USA’),
(102, 5002, ’Canada’),
(103, 5003, ’UK’),
(104, 5004, ’Germany’),
(105, 5005, ’France’),
(106, 5006, ’Australia’),
(107, 5007, ’Japan’),
(108, 5008, ’India’);

INSERT INTO Passport (passportNum, country, expDate, holderName) VALUES
(5001, ’USA’, ’2030-01-01’, ’David Harris’),
(5002, ’Canada’, ’2027-06-15’, ’Sarah Connor’),
(5003, ’UK’, ’2026-12-30’, ’Mike Johnson’),
(5004, ’Germany’, ’2028-05-10’, ’Laura White’),
(5005, ’France’, ’2029-11-20’, ’James Miller’),
(5006, ’Australia’, ’2027-03-25’, ’Emma Watson’),
(5007, ’Japan’, ’2031-09-10’, ’Chris Evans’),
(5008, ’India’, ’2025-07-05’, ’Sophia Brown’);


SQL Queries:

1. `SELECT DISTINCT TravelAgent.name FROM Traveler JOIN Booking on Traveler.ssn = Booking.traveler_ssn JOIN TravelAgent ON Booking.agent = TravelAgent.name WHERE Traveler.dob = '1985-06-12';`

2. `SELECT Traveler.dob FROM Traveler WHERE Traveler.ssn IN (SELECT Owns.ssn FROM Owns JOIN Passport ON Owns.passportNum = Passport.passportNum WHERE Passport.expDate < '2027-01-01');`

3. `SELECT TravelAgent.name FROM TravelAgent WHERE years_experience > (SELECT years_experience FROM TravelAgent WHERE name LIKE 'John%');`

4. `SELECT ssn FROM Owns INTERSECT SELECT ssn FROM GoesOn GROUP BY ssn HAVING count(id) > 1;`

5. `SELECT Booking.agent, Trip.start_location, Trip.end_location FROM Booking NATURAL JOIN Trip;`

6. `SELECT TravelAgent.name FROM TravelAgent WHERE years_experience < ALL (SELECT years_experience FROM TravelAgent WHERE years_experience > 10);`

7. `SELECT Trip.* FROM Trip JOIN GoesOn ON Trip.trip_id = GoesOn.id JOIN Owns ON GoesOn.ssn = Owns.ssn JOIN Passport ON Owns.passportNum = Passport.passportNum WHERE Trip.end_date > Passport.expDate;`

8. `SELECT TravelAgent.name, COUNT(Booking.trip_id) FROM TravelAgent JOIN Booking ON TravelAgent.name = Booking.agent GROUP BY TravelAgent.name HAVING COUNT(Booking.trip_id) > 1;`

9. `SELECT name, Traveler.ssn, dob FROM Traveler LEFT JOIN GoesOn ON Traveler.ssn = GoesOn.ssn WHERE GoesOn.ssn IS NULL;`

10. `SELECT Trip.* FROM Trip JOIN Booking ON Trip.trip_id = Booking.trip_id JOIN TravelAgent ON Booking.agent = TravelAgent.name WHERE TravelAgent.years_experience < 5;`