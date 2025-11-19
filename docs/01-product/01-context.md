# 1. Product Definition & Context

## 1.1. Purpose
To provide a web-based flashcard platform that leverages the **Spaced Repetition System (SRS)** algorithm to maximize learning efficiency and retention for users.

## 1.2. Business Goals
* **Core Learning:** Enable users to memorize content efficiently via automated intervals.
* **Content Management:** Empower users to create, manage, and customize personal flashcard sets.
* **Community:** Facilitate knowledge sharing by allowing users to browse and copy public sets.
* **Language Support:** Reduce friction in language learning by auto-generating translation hints.

## 1.3. Scope
### In Scope
* **Account System:** Registration, login, and profile management.
* **Set Management:** CRUD operations for sets and flashcards; cloning public sets.
* **Study System:** SRS logic execution, progress tracking, and study sessions.
* **Discovery:** Browsing, filtering, and previewing public content.

### Out of Scope
* Offline functionality (requires active internet connection).
* Real-time collaborative editing of sets.
* Native mobile applications (scope limited to responsive web interface).

## 1.4. Stakeholders
* **End User**: The primary actor who creates sets, studies flashcards, and tracks progress.

## 1.5. Glossary
For detailed definitions of terms like **Set**, **Space**, and **SRS**, please refer to the global [Business Glossary](./glossary.md).