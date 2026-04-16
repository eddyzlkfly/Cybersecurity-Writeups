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

From the result, we learn that a body was discovered at **Coral Bay Marina** on the specified date. More importantly, the description mentions that there were **two people** nearby, including one who lives around **"300ish Ocean Drive"**.

## 2) Identify suspects based on address and name pattern

From the previous step, we found that one of the individuals lives around **"300ish Ocean Drive"**.  
So, we query the `person` table to find anyone living on **Ocean Drive**.  

At the same time, we also try filtering based on a possible name pattern ending with **"ul"** and **"ez"** to narrow down suspects further.

```sql
SELECT * FROM person WHERE address LIKE "%Ocean Drive%" OR name LIKE "%ul %ez";
```
| id  | name            | alias       | occupation      | address         |
| --- | --------------- | ----------- | --------------- | --------------- |
| 1   | Marco Romano    | The Shadow  | Fisherman       | 22 Ocean Drive  |
| 5   | Michael Santos  | Silent Mike | Bartender       | 33 Ocean Drive  |
| 62  | Jesse Brooks    | The Judge   | Court Clerk     | 234 Ocean Drive |
| 101 | Carlos Mendez   | Los Ojos    | Fisherman       | 369 Ocean Drive |
| 102 | Raul Gutierrez  | The Cobra   | Nightclub Owner | 45 Sunset Ave   |
| 105 | Victor Martinez | Slick Vic   | Bartender       | 33 Ocean Drive  |

From the results, we get multiple individuals living on Ocean Drive.

However, based on the clue mentioning **"300ish Ocean Drive"**, we can narrow it down to addresses that are closer to that range:

- **234 Ocean Drive**
- **369 Ocean Drive**

This significantly reduces our suspect list and gives us a smaller group to investigate further in the next step.

## 3) Verify suspects using interview transcripts

From the previous step, we narrowed down our suspects to those living around **300ish Ocean Drive**, specifically:

- **Carlos Mendez (ID: 101)**
- **Raul Gutierrez (ID: 102)**

To gather more information, we check their interview transcripts to see if there are any useful clues.

```sql
SELECT * FROM interviews WHERE person_id IN (101, 102);
```
| id  | person_id | transcript                                                             |
| --- | --------- | ---------------------------------------------------------------------- |
| 101 | 101       | I saw someone check into a hotel on August 13. The guy looked nervous. |
| 103 | 102       | I heard someone checked into a hotel with "Sunset" in the name.        |

From the results, we get two important clues:

One suspect mentioned someone checking into a hotel on August 13
Another mentioned a hotel with "Sunset" in its name

This suggests that the suspect may have stayed at a hotel before or after the incident.
These clues will help us identify the exact location and narrow down the suspect further in the next step.

