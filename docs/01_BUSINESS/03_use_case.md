# Use Case Model
Use Cases describe **how users interact with the system** to achieve specific goals, illustrating practical scenarios of system usage from the user's perspective.

## Actors
- **Creator** – User creating their own sets and flashcards.
- **Learner** – User learning and reviewing their flashcards.
- **Public Explorer** – User browsing public sets and copying them.
- **Account Mgr** – User managing their account and profile.
- **System** – Automated system actions.

## Use Cases
| ID   | Name | Actor | Description |
|------|------|--------|-------------|
| **UC1** | Register Account | Account Mgr | User creates a new account. |
| **UC2** | Log In | Account Mgr | User logs into the system. |
| **UC3** | Log Out | Account Mgr | User logs out from the system. |
| **UC4** | Reset Password | Account Mgr | User initiates password reset. |
| **UC5** | View Profile | Account Mgr | User views their profile information. |
| **UC6** | Change Password | Account Mgr | User updates their password in the profile settings. |
| **UC7** | View Dashboard | Creator / Learner | User views their dashboard with all owned sets (including copied public sets). |
| **UC8** | Filter & Sort Sets | Creator / Learner | User filters or sorts sets by progress, review status, or other criteria. |
| **UC9** | Create Set | Creator | User creates a new set by providing a title and optional details. |
| **UC10** | Edit Set | Creator | User modifies the metadata of an owned set (title, description, tags). |
| **UC11** | Delete Set | Creator | User deletes one of their sets permanently. |
| **UC12** | Add Flashcards | Creator | User adds new flashcards to a set they own. |
| **UC13** | Delete Flashcards | Creator | User removes specific flashcards from their own set. |
| **UC14** | Generate Language Hints | System | The system generates translation suggestions and example sentences for language-type flashcards. |
| **UC15** | Browse Public Sets | Public Explorer | User browses public sets available in the system. |
| **UC16** | Filter & Sort Public Sets | Public Explorer | User filters/sorts public sets by tags, popularity, etc. |
| **UC17** | Preview Public Set | Public Explorer | User views details and flashcards of a public set without owning it. |
| **UC18** | Copy Public Set | Public Explorer | User copies a public set to their own collection as a fully independent clone. |
| **UC19** | Start Session | Learner | User starts a test session for any set they own. |
| **UC20** | Answer Flashcards | Learner | User answers flashcards during a session; system updates SRS levels automatically. |
| **UC21** | View Set Statistics | Learner | User views detailed analytics: flashcards per level, time spent, weekly learning chart. |
| **UC22** | Check Time Until Next Review | Learner | User sees countdown until the next allowed SRS session if no level-1 flashcards are available. |
| **UC23** | Send Review Notifications | System | The system sends notifications and emails reminding the user to review due flashcards. |

## Diagram
![Use Case Diagram](../img/use-case-model.svg)
