

HW5:

1.
{agent, traveler_ssn, trip_id}

2.
(a)
agent -> years_experience
{agent}+ = {agent, years_experience}

Decompose:
R1 = {<u>agent</u>, years_experience}
R2 = {agent, traveler_ssn, trip_id, start_location, end_location, passport_number, expiration_date}

(b)
R1 = {<u>traveler_ssn</u>, passport_number, expiration_date}
R2 = {traveler_ssn, agent, start_location, end_location, trip_id }

(c)
passport_number -> expiration_date
{passport_number}+ = {passport_number, expiration_date}

Decompose:
R1 = {<u>passport_number</u>, expiration_date}
R2 = {passport_number, traveler_ssn}



HW6:
CREATE TABLE Booking(agent varchar(50), traveler_ssn INT, trip_id INT)


CREATE TABLE Traveler(name VARCHAR(50) NOT NULL, ssn INT PRIMARY KEY, dob DATE)

CREATE TABLE TravelAgent(name VARCHAR(50) PRIMARY KEY, years_experience INT, phone VARCHAR(50), CONSTRAINT YE_Check CHECK (years_experience >= 1));

CREATE TABLE Passport(passport_number INT PRIMARY KEY, country VARCHAR(50), expirationDate DATE, holderName, VARCHAR(50) CONSTRAINT exp_date CHECK (expirationDate > '2020-01-01'));

CREATE TABLE Owns (ssn INT PRIMARY KEY, passport_number INT, country VARCHAR(50) FOREIGN KEY (ssn) REFERENCES Traveler(ssn) ON UPDATE CASCADE ON DELETE CASCADE);



