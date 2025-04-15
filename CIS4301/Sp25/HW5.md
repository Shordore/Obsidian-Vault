 <b>1.Compute the Primary Key:</b>
 Primary Key:
	{agent, traveler_ssn, trip_id}


<b>2.Decompose into BCNF:</b>
Agent -> years_experience
	1.  (agent, years_experience)
	2. (agent, traveler_ssn, trip_id, passport_number, expiration_date, start_location, end_location)


passport_number -> expiration_date
	1.(passport_number, expiration_date)


traveler_ssn -> passport_number
	1. (traveler_ssn, passport_number)
	2. (agent, trip_id, start_location, end_location, traveler_ssn, expiration_date)


trip_id -> start_location, end_location
	1. (trip_id, start_location, end_location)
	2. (agent, trip_id, traveler_ssn)


<b>3.List the Final Relations:</b>
	1. (<u>agent</u>, years_experience)
	2. (<u>passport_number</u>, expiration_date)
	3. (<u>traveler_ssn</u>, passport_number)
	4. (<u>trip_id</u>, start_location, end_location)


<b>4.Justify Each Decomposition Step:</b>
	1. agent is not a superkey so it had to be split
	2. passport_number was not the key on its own so it needed to be put in another table where it can be the primary key.
	3. traveler_ssn is not a superkey so it got put in another table
	4. trip_id was not the full key in this relation so it got put into a separate relation