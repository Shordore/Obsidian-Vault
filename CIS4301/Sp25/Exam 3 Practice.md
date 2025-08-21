

HW5:

1.
{agent, traveler_ssn, trip_id}

2.
(a)




HW6:
CREATE TABLE Leg (Trip_id INT, startLocation VARCHAR(50), endLocation VARCHAR(50)< startDate DATE, endDate DATE PRIMARY KEY(trip_id startLocation EndLocation) CONSTRAINT s_e CHECK (endDate > startDate) FOREIGN KEY trip_id REFERENCES Trip(id));

CREATE TABLE Trip(id INT, start_location VARCAHR(50), end_location VARCHAR(50) < start_date Date, end_date Date PRIMARY KEY (id) CONSTRAINT s_e CHECK(endDate > startDate));


Triggers:
CREATE Trigger Trig1 BEFORE DELETE ON Traveler FOR EACH ROW INSERT INTO DeletedTravelerLog(ssn, name) Values(old.ssn, old.name);

CREATE TRIGGER Trig2 AFTER INSERT ON GoesOn FOR EACH ROW UPDATE SET = trip_count WHERE 


