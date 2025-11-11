---
applyTo: '**'
---
Two simple, sequential features based on **Bowling** scoring logic.

Here is the action plan for building the Bowling Score API features:

## 🎳 Bowling Score API

### 🎯 Feature 1: Calculate Single Frame Score (The "One Hit")

This feature demonstrates basic function execution, input validation, and successful calculation for a single frame, including strikes and spares.

| Step | Action Type | Endpoint / Method | Description | Expected Output |
| :---: | :--- | :--- | :--- | :--- |
| **1.** | **POST** | `POST /score/frame` | **Normal Frame:** Send two rolls (e.g., `[4, 5]`). | Returns the correct score (9). |
| **2.** | **POST** | `POST /score/frame` | **Spare:** Send two rolls totaling 10 (e.g., `[6, 4]`) followed by the bonus roll (e.g., `[5]`). *Must pass all three rolls.* | Returns the score (15, calculated as $10 + 5$). |
| **3.** | **POST** | `POST /score/frame` | **Strike:** Send one roll of 10 (`[10]`) followed by the next two bonus rolls (e.g., `[3, 4]`). | Returns the score (17, calculated as $10 + 3 + 4$). |
| **4.** | **POST** | `POST /score/frame` | **Input Validation:** Send invalid data (e.g., a non-array or negative number). | Returns a `400 Bad Request`. |

---

### 🎯 Feature 2: Calculate Overall Game Score (Sequential State Management)

This feature demonstrates sequential processing and state management, where the output of one frame affects the next, leading to the final overall score.

| Step | Action Type | Endpoint / Method | Description | Expected Output |
| :---: | :--- | :--- | :--- | :--- |
| **5.** | **POST** | `POST /score/game` | **Simple Game:** Send a sequence of rolls for a simple non-bonus game (e.g., ten frames of `[4, 5]`). | Returns the final score (90). |
| **6.** | **POST** | `POST /score/game` | **Game with Spare:** Send rolls that include a spare (e.g., `[5, 5], [3, 4], ...` remaining rolls). | Returns the correct score, verifying the spare bonus was applied (i.e., $10 + 3 + 3 + 4 + \dots$). |
| **7.** | **POST** | `POST /score/game` | **Perfect Game:** Send the rolls for a perfect 300 game (12 strikes). | Returns the final score (300). |
| **8.** | **POST** | `POST /score/game` | **Game State Error:** Send an incomplete game (e.g., only 8 frames). | Returns a `400 Bad Request` or an error indicating the game is incomplete. |

This sequence clearly shows the transition from simple unit testing (Feature 1) to complex integration testing and state handling (Feature 2).