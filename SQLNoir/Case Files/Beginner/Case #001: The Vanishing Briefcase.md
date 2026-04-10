# Case #001: The Vanishing Briefcase

Set in the gritty 1980s, a valuable briefcase has disappeared from the Blue Note Lounge. A witness reported that a man in a trench coat was seen fleeing the scene. Investigate the crime scene, review the list of suspects, and examine interview transcripts to reveal the culprit.

# Objectives

1. Retrieve the correct crime scene details to gather the key clue.
2. Identify the suspect whose profile matches the witness description.
3. Verify the suspect using their interview transcript.

# Investigation Steps
## 1 - Identify suspects matching the witness description

Since the witness mentioned seeing a man wearing a trench coat, the first thing to do is filter the suspects based on their attire.

To do this, we run the following SQL query to retrieve suspects who were wearing a trench coat.
```sql
SELECT * FROM suspects WHERE attire = "trench coat"
```
The query returns three suspects who match the description. These are the individuals who were wearing a trench coat, so they become our primary suspects for now.

| id | name | attire | scar |
|----------|----------|----------|----------|
| 3   | Frankie Lombardi   | trench coat   | left cheek   |
| 183   | Vincent Malone   | trench coat   | left cheek   |
| 237   | Christopher Black   | trench coat   | right cheek   |

From the results, the suspects are:

- Frankie Lombardi
- Vincent Malone
- Christopher Black

## 2 - Retrieve crime scene details

SELECT * FROM crime_scene WHERE location = "Blue Note Lounge"

| id | date | type | location | description |
|----------|----------|----------|----------|----------|
| 76   | 19851120   | theft   | Blue Note Lounge   | A briefcase containing sensitive documents vanished. A witness reported a man in a trench coat with a scar on his left cheek fleeing the scene.
   
## 3

SELECT * FROM interviews WHERE suspect_id IN (3, 183)

| suspect_id | transcript |
|----------|----------|
| 3   | NULL   |
| 183   | I wasn’t going to steal it, but I did.   |


