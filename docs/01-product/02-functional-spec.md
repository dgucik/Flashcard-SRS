# 2. Functional Specification

## Module 1: Identity & Account Management
*Handles user access and security.*

### Feature 1.1: User Registration
* **Process:** User enters email/password -> System validates -> Registration confirmed -> Account created -> Redirect to Space.
* **Business Rules:**
    * **AUTH-01:** Passwords must be hashed securely.
    * **AUTH-02:** Successful registration automatically logs the user in.
    * **AUTH-03:** User must confirm registration via email link within 24h.
* **Visual Logic Reference:** 
    * **Process Diagram (BPMN):** [User Registration](../assets/bpmn/bpmn-user-registration.png)

### Feature 1.2: Authentication (Login/Logout)
* **Process:** User logs in via Email/Password OR "Continue with Google".
* **Business Rules:**
    * **AUTH-04:** Session persists until explicit logout.
    * **AUTH-05:** User can request a password reset via email link.
* **Visual Logic Reference:** 
    * **Process Diagram (BPMN):** [User Login](../assets/bpmn/bpmn-user-login.png)

---

## Module 2: Workspace & Set Management
*The core CRUD operations for content creators.*

### Feature 2.1: User Space
* **Description:** The main view after login, displaying all owned sets.
* **Business Rules:**
    * **SP-01:** Displays own sets AND copied public sets (treated as independent instances).
    * **SP-02:** List item shows: Title, Description, Tags, Card Count, Progress %.
    * **SP-03:** Allows filtering/sorting by Progress or "Review Needed" status.

### Feature 2.2: Set Dashboard (Detailed View)
* **Description:** The specific hub for a single set, accessed by clicking an item in the User Space.
* **Business Rules:**
    * **DV-01:** Displays count of cards per Level (1–5, Memorized) and recent study time.
    * **DV-02:** Must include "Start Session" (DASH-01) and options to manage content/metadata.

### Feature 2.3: Set Management
* **Process:** User creates/edits a set -> Defines metadata -> Adds Flashcards.
* **Business Rules:**
    * **SET-01:** User must choose type: `Standard` or `Language`.
    * **SET-02:** **Limit:** Maximum 200 Flashcards per set.
    * **SET-03:** User can delete a set permanently.

### Feature 2.4: Flashcard Operations
* **Business Rules:**
    * **CARD-01:** If Set Type is `Language`, system automatically generates Translation Hints & Examples.
    * **CARD-02:** All new flashcards initialize at **Level 1**.

---

## Module 3: Learning System (SRS)
*The "Brain" of the application. Controls study logic.*

### Feature 3.1: Study Session Logic
* **Process:** User clicks "Start Session" -> System serves due cards -> User answers -> System updates Level.
* **Business Rules:**
    * **SRS-01 (Availability):** Session can only start if there are cards at Level 1 OR cards due for review. If not, show timer.
    * **SRS-02 (Progress):** 0% = All cards Level 1; 100% = All cards Memorized.
    * **SRS-03 (Notifications):** System sends email/push when reviews are due.

### Feature 3.2: The Algorithm (Spaced Repetition)
* **Process:** System evaluates the user's answer rating -> Updates Flashcard Level -> Calculates next Review Date based on the interval table.
* **Business Rules:**
    * **SRS-04 (Level Progression):**
        * **Correct Answer:** Flashcard level increases by +1 (S003).
        * **Incorrect Answer:** Flashcard level resets to **Level 1** (S003).
    * **SRS-05 (Review Intervals):** The system must enforce the following wait times between reviews based on the card's new level (S004):
        | Current Level | Interval (Time until next review) |
        | :--- | :--- |
        | **Level 1** | Continuous (Immediate) |
        | **Level 2** | 1 Day |
        | **Level 3** | 3 Days |
        | **Level 4** | 10 Days |
        | **Level 5** | 30 Days |
        | **Memorized** | 30 Days (Maintenance) |

### Visual Logic Reference (Complete Module Flow)
* **Process Diagram (BPMN):** [Study Session & Algorithm](../assets/bpmn/bpmn-study-session-n-algorithm.png)
* *Note: This diagram visualizes the user flow from Feature 3.1 combined with the logic from Feature 3.2.*

## Module 4: Public Library
*Discovery and sharing features.*

### Feature 4.1: Browsing & Discovery
* **Process:** User navigates to Public tab -> Filters list -> Previews Set.
* **Business Rules:**
    * **PUB-01:** User can preview content without owning the set.
    * **PUB-02:** Filtering available by Tags and Popularity.

### Feature 4.2: Cloning Content
* **Process:** User clicks "Copy to my Space".
* **Business Rules:**
    * **PUB-03:** The copied set becomes a **fully independent clone**. Changes to the original do NOT affect the copy, and vice versa.