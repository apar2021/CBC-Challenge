# Task 1 - Find the Unknown Object 

The US Coast Guard (USCG) recorded an unregistered signal over 30 nautical miles away from the continental US (OCONUS). NSA is contacted to see if we have a record of a similar signal in our databases. 
The Coast guard provides a copy of the signal data. Your job is to provide the USCG any colluding records from NSA databases that could hint at the object’s location.
Per instructions from the USCG, to raise the likelihood of discovering the source of the signal, they need multiple corresponding entries from the NSA database whose geographic coordinates are within 1/100th of a degree. 
Additionally, record timestamps should be no greater than 10 minutes apart.
Downloads:

file provided by the USCG that contains metadata about the unknown signal (USCG.log)
NSA database of signals (database.db)

Prompt:
Provide database record IDs, one per line, that fit within the parameters specified above.

Approach to Solving: 
Given the task information, we have to find the records of a signal that is over 30 nautical miles from the Oconus. While looking through the database, we can find database records that are in the given distance from the Oconus. I was able to access the database using the SQLite application. In the database, we can find five tables: audio_object,event,location,and sqlite_sequence,and timestamp. 
After simulatenously parsing through the five tables, we can find all the records that coincide with the given criteria of the Task. There should be less than 10 records while submitting your answer. 
