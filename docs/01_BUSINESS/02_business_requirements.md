# Business Requirements
Requirements define **what the system must do** and specify the features, capabilities, and constraints of the system to meet business needs.

## Functional Requirements (BR-F)

### Account Management (A)
- **A001** – User creates an account.
- **A002** – User logs in to the account.
- **A003** – User logs out of the account.
- **A004** – User resets the password.
- **A005** – User views their profile.
- **A006** – User changes the password in their profile.

### Dashboard (D)
- **D001** – User views the dashboard after logging in.
- **D002** – The system displays a list of the user's own sets on the dashboard, including copied public sets, which are treated as fully independent copies.
- **D003** – The list of sets shows only: title, description, tags, number of flashcards, whether the set is public, and the percentage Progress. Detailed statistics of the set (number of flashcards at levels 1–5 and memorized, time spent studying in the last week) and the option to start a test session are displayed when clicking on a specific set.
- **D004** – The system allows filtering and sorting sets, e.g., by Progress or flashcards that need to be reviewed now.

### Collections / Sets (C)
- **C001** – User creates a set, providing a required title, optionally a description and tags, and chooses the type: standard or language.
- **C002** – User edits a set (title, description, tags).
- **C003** – User deletes a set completely.
- **C004** – User copies a public set to their space; the copy becomes a fully independent set owned by the user.
- **C005** – The system limits the number of flashcards in a set to a maximum of 200.

### Flashcards (F)
- **F001** – User adds flashcards to a set.
- **F002** – User deletes flashcards from a set.
- **F003** – The system generates translation hints and example sentences for language flashcards.

### Public Sets (P)
- **P001** – User browses public sets.
- **P002** – User filters and sorts public sets (e.g., by tags, popularity).
- **P003** – User previews the content of a public set.
- **P004** – User copies a public set to their space as a fully independent set.

### Study / SRS (S)
- **S001** – User starts a session for a set.
- **S002** – All flashcards in the set start at level 1.
- **S003** – Flashcards advance by 1 level for a correct answer or drop to level 1 for an incorrect answer.
- **S004** – Review intervals by level:
  - Level 1 – repeated continuously,
  - Level 2 – 1 day,
  - Level 3 – 3 days,
  - Level 4 – 10 days,
  - Level 5 – 30 days,
  - Memorized – every 30 days.
- **S005** – If there are no level 1 flashcards in the set, the system displays the elapsed time until the next review; during this period, reviews are not possible.
- **S006** – The system notifies the user when flashcards need to be reviewed (in-app notification + email).
- **S007** – The set's percentage Progress is calculated as: 0% = all flashcards at level 1, 100% = all flashcards memorized.

## Non-Functional Requirements (BR-NF)

- **001** – All user passwords must be stored securely using hashing.
- **002** – The system must log errors to allow for rapid diagnosis and debugging.
- **003** – The user interface must be intuitive and responsive on both desktop and mobile devices.
- **004** – The system and API must respond in under 1 second for all user interactions and views.

