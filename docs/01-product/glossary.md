# Business Glossary

This document serves as the **Ubiquitous Language** (single source of truth) for all naming conventions used in the Code, Database, API, and UI.

## 1. Core Domain Entities
*Fundamental objects and data structures in the system.*

| Term | Definition |
| :--- | :--- |
| **User** | A person who uses the system, owns an account, and performs actions within the application. |
| **Profile** | The user's settings page containing personal data and security options (e.g., password change). |
| **Set** | A collection of flashcards created or copied by the user. Contains metadata (title, description, tags) and content. |
| **Flashcard** | A single learning unit with two sides (Front/Back). |
| **Front** | The obverse side of a flashcard containing the query (e.g., Question, Word). |
| **Back** | The reverse side of a flashcard containing the solution (e.g., Answer, Translation). |
| **Standard Set** | A type of set without language-specific automation. |
| **Language Set** | A type of set equipped with auto-translation features and example sentences. |
| **Public Set** | A publicly available set that any user can browse or copy to their private Space. |
| **Translation Hint** | An automatically generated translation suggestion for flashcards within a Language Set. |

## 2. Learning System (SRS)
*Terms related to the algorithm and study mechanics.*

| Term | Definition |
| :--- | :--- |
| **Session** | A study mode where the user reviews flashcards due for repetition according to the SRS algorithm. |
| **Level** | The SRS mastery stage of a flashcard (1–5). After Level 5, a card achieves 'Memorized' status. Determines the interval until the next Review. |
| **Memorized** | The highest status of a flashcard, indicating it has been fully learned (maintenance mode). |
| **Review** | A specific instance of repeating a flashcard that has become due based on its Level. |
| **Progress** | A percentage indicator (0-100%) showing mastery of a Set based on flashcard levels. |
| **Statistics** | Analytical data about a set: number of flashcards per level, study time, activity. |

## 3. Interface & Views (UI)
*Names of specific screens and areas in the application.*

| Term | Definition |
| :--- | :--- |
| **Space** | The user's main private area (landing page) containing the list of their Sets. |
| **Dashboard** | The detailed view of a single Set showing statistics and the "Start Session" button. |

## 4. Acronyms
| Acronym | Meaning |
| :--- | :--- |
| **API** | Application Programming Interface. |
| **SRS** | Spaced Repetition System. |