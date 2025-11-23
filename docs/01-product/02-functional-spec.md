# 2. Functional Specification

## Module 1: Identity & Account Management
*Handles user access and security.*

### Feature 1.1: User Registration
* **Process:** User enters email/password -> System validates -> Registration confirmed -> Account created -> Redirect to Space.
* **Business Rules:**
    * **BR-1101:** Passwords must be hashed securely.
    * **BR-1102:** Successful registration automatically logs the user in.
    * **BR-1103:** User must confirm registration via email link within 24h.
* **Visual Logic Reference:** 
    * **Process Diagram (BPMN):** [User Registration](../assets/bpmn/bpmn-user-registration.png)

### Feature 1.2: Authentication (Login/Logout)
* **Process:** User logs in via Email/Password OR "Continue with Google".
* **Business Rules:**
    * **BR-1201:** Session persists until explicit logout.
    * **BR-1202:** User can request a password reset via email link.
* **Visual Logic Reference:** 
    * **Process Diagram (BPMN):** [User Login](../assets/bpmn/bpmn-user-login.png)

---

## Module 2: Workspace & Study Set Management
*The core CRUD operations for content creators.*

### Feature 2.1: User Space
* **Description:** The main view after login, displaying all owned Study Sets.
* **Business Rules:**
    * **BR-2101:** Displays own Study Sets AND copied public sets (treated as independent instances).
    * **BR-2102:** List item shows: Title, Description, Tags, Card Count, Progress %.
    * **BR-2103:** Allows filtering/sorting by Progress or "Review Needed" status.

### Feature 2.2: Set Dashboard (Detailed View)
* **Description:** The specific hub for a single Study Set, accessed by clicking an item in the User Space.
* **Business Rules:**
    * **BR-2201:** Displays count of cards per Level (1–5, Memorized) and recent study time.
    * **BR-2202:** Must include "Start Session" (DASH-01) and options to manage content/metadata.

### Feature 2.3: Study Set Management
* **Process:** User creates/edits a set -> Defines metadata -> Adds Flashcards.
* **Business Rules:**
    * **BR-2301:** User creates a unified Study Set.
    * **BR-2302:** User has the option to enable Language Automation for the set, requiring selection of the Source Language and Target Language.
    * **BR-2303:** **Limit:** Maximum 200 Flashcards per set.
    * **BR-2304:** User can delete a set permanently.

### Feature 2.4: Flashcard Operations
* **Business Rules:**
    * **BR-2401:** If Language Automation is enabled for the Study Set (as configured in BR-2302), the system automatically generates Translation Hints & Examples for every new flashcard.
    * **BR-2402:** All new flashcards initialize at **Level 1**.

---

## Module 3: Smart Learn System
*The "Brain" of the application. Controls study logic.*

### Feature 3.1: Study Session Logic
* **Process:** User clicks "Start Session" -> System serves due cards -> User answers -> System updates Level.
* **Business Rules:**
    * **BR-3101 (Availability):** Session can only start if there are cards at Level 1 OR cards due for review. If not, show timer.
    * **BR-3102 (Progress):** 0% = All cards Level 1; 100% = All cards Memorized.
    * **BR-3103 (Notifications):** System sends email/push when reviews are due.

### Feature 3.2: The Smart Learn Algorithm
* **Process:** System evaluates the user's answer rating -> Updates Flashcard Level -> Smart Learn calculates the exact date to remind the user based on the interval table.
* **Business Rules:**
    * **BR-3201 (Level Progression):**
        * **Correct Answer:** Flashcard level increases by +1.
        * **Incorrect Answer:** Flashcard level resets to **Level 1**.
    * **BR-3202 (Review Intervals):** The system must enforce the following wait times between reviews based on the card's new level:
        | Current Level | Interval (Time until next review) |
        | :--- | :--- |
        | **Level 1** | Continuous (Immediate) |
        | **Level 2** | 1 Day |
        | **Level 3** | 3 Days |
        | **Level 4** | 10 Days |
        | **Level 5** | 30 Days |
        | **Memorized** | 30 Days (Maintenance) |

### Visual Logic Reference (Complete Module Flow)
* **Process Diagram (BPMN):** [Smart Learn](../assets/bpmn/bpmn-smart-learn.png)
* *Note: This diagram visualizes the user flow from Feature 3.1 combined with the logic from Feature 3.2.*

## Module 4: Public Library
*Discovery and sharing features.*

### Feature 4.1: Browsing & Discovery
* **Process:** User navigates to Public tab -> Filters list -> Previews Study Set.
* **Business Rules:**
    * **BR-4101:** User can preview content without owning the Study Set.
    * **BR-4102:** Filtering available by Tags and Popularity.

### Feature 4.2: Cloning Content
* **Process:** User clicks "Copy to my Space".
* **Business Rules:**
    * **BR-4201:** The copied set becomes a **fully independent clone**. Changes to the original do NOT affect the copy, and vice versa.