# Case #001: The Vanishing Briefcase

Set in the gritty 1980s, a valuable briefcase has disappeared from the Blue Note Lounge. A witness reported that a man in a trench coat was seen fleeing the scene. Investigate the crime scene, review the list of suspects, and examine interview transcripts to reveal the culprit.

# Objectives

1. Retrieve the correct crime scene details to gather the key clue.
2. Identify the suspect whose profile matches the witness description.
3. Verify the suspect using their interview transcript.

# Investigation Steps
## 1

SELECT * FROM suspects WHERE attire = "trench coat"

| id | name | attire | scar |
|----------|----------|----------|----------|
| 3   | Frankie Lombardi   | trench coat   | left cheek   |
| 183   | Vincent Malone   | trench coat   | left cheek   |
| 237   | Christopher Black   | trench coat   | right cheek   |

## 2

SELECT * FROM crime_scene WHERE location = "Blue Note Lounge"

| id | date | type | location | description |
|----------|----------|----------|----------|----------|
| 76   | 19851120   | theft   | Blue Note Lounge   | A briefcase containing sensitive documents vanished. A witness reported a man in a trench coat with a scar on his left cheek fleeing the scene.
   




