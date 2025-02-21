
<b>SQL Tables commands:</b>

CREATE TABLE TravelAgent(
    name varchar(50) PRIMARY KEY, years_experience INT NOT NULL, phone VARCHAR(50) NOT NULL
);

CREATE TABLE Traveler(
    name VARCHAR(50) NOT NULL, ssn INT PRIMARY KEY, dob DATE NOT NULL
);


CREATE TABLE Trip(
    id INT PRIMARY KEY, start_location VARCHAR(50) NOT NULL, end_location VARCHAR(50) NOT NULL, start_date DATE NOT NULL, end_date DATE NOT NULL);


CREATE TABLE Booking(
    agent VARCHAR(50) NOT NULL, traveler_ssn INT NOT NULL, trip_id INT NOT NULL, FOREIGN KEY (agent) REFERENCES TravelAgent(name), FOREIGN KEY (traveler_ssn) REFERENCES Traveler(ssn), FOREIGN KEY (trip_id) REFERENCES Trip(id));


<b>SQL Insert Commands:</b>

INSERT INTO TravelAgent( name, years_experience, phone) VALUES
('Alice Brown', 12, '123-456-7890'),
('John Smith', 8, '234-567-8901'),
('Michael Johnson', 5, '345-678-9012'),
('Sarah Williams', 15, '456-789-0123'),
('Daniel Lee', 20, '567-890-1234'),
('Rachel Green', 3, '678-901-2345');


INSERT INTO Traveler(name, ssn, dob) VALUES
('David Harris', 101,'1985-06-12'),
('Sarah Connor', 102,'1992-03-05'),
('Mike Johnson', 103,'1998-09-17'),
('Laura White', 104,'1995-04-23'),
('James Miller', 105,'2000-08-14'),
('Emma Watson', 106,'1997-11-30'),
('Chris Evans', 107,'1993-06-21'),
('Sophia Brown', 108,'1999-02-25');

INSERT INTO Trip(id, start_location, end_location, start_date, end_date) VALUES
(201, 'New York', 'Paris', '2025-07-10', '2025-07-20'),
(202, 'Tokyo', 'Sydney', '2025-08-01', '2025-08-15'),
(203, 'London', 'Rome', '2025-09-05', '2025-09-15'),
(204, 'Miami', 'New York', '2025-06-15', '2025-06-20'),
(205, 'San Francisco', 'Berlin', '2025-10-01', '2025-10-10'),
(206, 'Chicago', 'Los Angeles', '2025-09-10', '2025-09-12'),
(207, 'Boston', 'Dubai', '2025-07-05', '2025-07-18'),
(208, 'New York', 'Dubai', '2025-09-10', '2025-09-15');


INSERT INTO Booking(agent, traveler_ssn, trip_id) VALUES
('Alice Brown', 101, 201),
('John Smith', 102, 202),
('Michael Johnson', 103, 203),
('Sarah Williams', 104, 204),
('Daniel Lee', 105, 205),
('Alice Brown', 106, 206),
('Rachel Green', 107, 207),
('John Smith', 108, 201),
('Alice Brown', 101, 208);


<b>Screenshots for step 2:</b>

Screenshot of inserting the tables and the resulting output success.
![[Tables&Success.png]]


Screenshot of inputting dummy data and the output success.
![[Insert&Success.png]]


<b>Queries:</b>
1.
SELECT name, phone, 'Experienced Agent' AS Experience FROM TravelAgent WHERE years_experience > 10;

2.
SELECT start_date, end_date FROM Trip WHERE start_location = 'New York';

3.
SELECT * FROM Trip WHERE start_location = 'New York' AND end_location = 'Paris';

4.
SELECT * FROM Trip WHERE start_location = 'New York' OR start_location = 'Miami';

5.
SELECT * FROM Trip WHERE start_date > '2025-08-01';

6.
SELECT traveler_ssn, trip_id FROM Booking WHERE agent = 'Alice Brown';

7.
SELECT * FROM Traveler WHERE name LIKE '_a%';

8.
SELECT * FROM Traveler WHERE name NOT LIKE 'David Harris';

9.
SELECT * FROM TravelAgent WHERE phone LIKE '456%';

10.
SELECT * FROM Trip WHERE start_date BETWEEN '2025-07-01' AND '2025-09-30';


<b>Query Screenshots:</b>

1.
![[Pasted image 20250218150325.png]]

2.
![[Pasted image 20250218150357.png]]

3.
![[Pasted image 20250218150714.png]]

4.
![[Pasted image 20250218150802.png]]

5.
![[Pasted image 20250218150903.png]]

6.
![[Pasted image 20250218151220.png]]

7.
![[Pasted image 20250218151238.png]]

8.
![[Pasted image 20250218151355.png]]

9.
![[Pasted image 20250218151440.png]]

10.
![[Pasted image 20250218151520.png]]