
<b>Part 1:</b>

1.`CREATE VIEW TopAgents AS SELECT name, years_experience FROM TravelAgent WHERE years_experience >10;`
![[Pasted image 20250417215059.png]]

2.`CREATE VIEW ActiveTrips AS SELECT id, start_location, end_location, end_date FROM Trip WHERE end_date > CURRENT_DATE();`
![[Pasted image 20250417215117.png]]


3.`CREATE VIEW PassportHoldersByCountry AS SELECT country, count(*) AS passport_count FROM Passport GROUP BY country;`
![[Pasted image 20250417215133.png]]


4.`CREATE VIEW AgentBookings AS SELECT agent, count(*) AS trip_count FROM Booking GROUP BY agent;`
![[Pasted image 20250417215149.png]]


5.`CREATE VIEW UpcomingTripsByTraveler AS SELECT traveler.name AS nameOfTraveler, trip.id, trip.start_date, trip.end_date FROM Traveler JOIN GoesOn ON traveler.ssn = GoesOn.ssn JOIN Trip ON GoesOn.id = Trip.id WHERE trip.start_date > CURRENT_DATE();`
![[Pasted image 20250417215207.png]]



<b>Part 2:</b>
1.`SELECT DISTINCT Booking.agent FROM Booking JOIN ActiveTrips ON Booking.trip_id = ActiveTrips.id;`
![[Pasted image 20250423162821.png]]

2.`SELECT country FROM PassportHoldersByCountry ORDER BY passport_count DESC LIMIT 1;`
![[Pasted image 20250417215556.png]]


3.`WITH trip_count AS (SELECT nameOfTraveler, count(*) AS count_trip FROM UpcomingTripsByTraveler GROUP BY nameOfTraveler), count_max AS (SELECT MAX(count_trip) AS max_count FROM trip_count) SELECT nameOfTraveler FROM trip_count where count_trip = (SELECT max_count from count_max);`
![[Pasted image 20250417215615.png]]

4.`SELECT ActiveTrips.id, ActiveTrips.start_location, ActiveTrips.end_location, Booking.agent FROM ActiveTrips JOIN Booking ON ActiveTrips.id = Booking.trip_id;`
![[Pasted image 20250417215637.png]]

