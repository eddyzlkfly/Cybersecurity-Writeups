# Case #003: The Miami Marina Murder

A body was found floating near the docks of Coral Bay Marina in the early hours of August 14, 1986. Your job, detective, is to find the murderer and bring them to justice. This case might require the use of JOINs, wildcard searches, and logical deduction. Get to work, detective.

# Objectives

1. Find the murderer.

# Investigation Steps
## 1) Retrieve crime scene details

Since the case description already provides us with the **date** and **location**, we can use this information to query the `crime_scene` table and retrieve details about the incident.

```sql
SELECT * FROM crime_scene WHERE date = "19860814" AND location = "Coral Bay Marina";
```
| id | date     | location         | description                                                                                                                                          |
| -- | -------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 43 | 19860814 | Coral Bay Marina | The body of an unidentified man was found near the docks. Two people were seen nearby: one who lives on 300ish "Ocean Drive" and another whose first name ends with "ul" and his last name ends with "ez".
