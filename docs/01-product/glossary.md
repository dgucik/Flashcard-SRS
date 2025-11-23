# Business Glossary

This document serves as the **Ubiquitous Language** (single source of truth) for all naming conventions used in the Code, Database, API, and UI.

## 1. Core Domain Entities
*Fundamental objects and data structures in the system.*

| Term | Definition |
| :--- | :--- |
| **User** | A person who uses the system, owns an account, and performs actions within the application. |
| **Profile** | The user's settings page containing personal data and security options (e.g., password change). |
| **Study Set** | A collection of flashcards created or copied by the user. Contains metadata (title, description, tags) and content. |
| **Flashcard** | A single learning unit with two sides (Front/Back). |
| **Front** | The obverse side of a flashcard containing the query (e.g., Question, Word). |
| **Back** | The reverse side of a flashcard containing the solution (e.g., Answer, Translation). |
| **Public Set** | A publicly available Study Set that any user can browse or copy to their private Space. |
| **Translation Hint** | An automatically generated translation suggestion for flashcards when the user opts for Language Hints. |

## 2. Smart Learn System
*Terms related to the algorithm and study mechanics.*

| Term | Definition |
| :--- | :--- |
| **Smart Learn** | The proprietary study system based on the SRS algorithm. It automatically calculates the exact time to remind the user about a flashcard. |
| **Session** | A study mode where the user reviews flashcards due for repetition according to the Smart Learn algorithm. |
| **Level** | The mastery stage of a flashcard (1–5). After Level 5, a card achieves 'Memorized' status. Determines the interval until the next Review. |
| **Memorized** | The highest status of a flashcard, indicating it has been fully learned (maintenance mode). |
| **Review** | A specific instance of repeating a flashcard that has become due based on its Level. |
| **Progress** | A percentage indicator (0-100%) showing mastery of a Study Set based on flashcard levels. |
| **Statistics** | Analytical data about a Study Set: number of flashcards per level, study time, activity. |

## 3. Interface & Views (UI)
*Names of specific screens and areas in the application.*

| Term | Definition |
| :--- | :--- |
| **Space** | The user's main private area (landing page) containing the list of their Study Sets. |
| **Dashboard** | The detailed view of a single Study Set showing statistics and the "Start Session" button. |

## 4. Acronyms
| Acronym | Meaning |
| :--- | :--- |
| **API** | Application Programming Interface. |
| **SRS** | Spaced Repetition System (The mathematical basis for Smart Learn). |