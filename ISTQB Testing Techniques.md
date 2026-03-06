The **International Software Testing Qualifications Board (ISTQB)** defines a set of **testing techniques** that help testers design effective test cases. These techniques are grouped into **three main categories**: **Black-Box Testing Techniques, White-Box Testing Techniques, and Experience-Based Testing Techniques**. Each group focuses on a different perspective of the system and helps testers improve defect detection.

---

# 1. Black-Box Testing Techniques

Black-box testing techniques focus on **testing the functionality of the system without knowledge of its internal code structure**. Testers design test cases based on **requirements, specifications, and expected behavior**. The system is treated like a “black box” where inputs are provided and outputs are observed.

### Key Characteristics

* No knowledge of source code is required.
* Tests are derived from **functional requirements and specifications**.
* Focuses on **what the system does**, not **how it does it**.
* Commonly used in **system testing and acceptance testing**.

### Common Black-Box Techniques

**1. Equivalence Partitioning**
This technique divides input data into **equivalence classes (partitions)** where the system is expected to behave similarly. Instead of testing every possible value, testers select one representative value from each partition.

Example:
If an input field accepts numbers from **1 to 100**, partitions could be:

* Valid: 1–100
* Invalid: <1
* Invalid: >100

Testing one value from each partition reduces the number of test cases while still providing good coverage.

**2. Boundary Value Analysis**
This technique focuses on **testing values at the boundaries of input ranges**, where defects commonly occur.

Example:
If a system accepts numbers **1–100**, boundary test cases would include:

* 0, 1, 2
* 99, 100, 101

These edge values often reveal errors like incorrect comparison operators or off-by-one mistakes.

**3. Decision Table Testing**
Decision tables are used when system behavior depends on **multiple conditions**. A table lists all combinations of conditions and the corresponding actions.

Example conditions:

* User logged in
* Valid payment method

Each combination produces a specific expected result. Decision tables ensure that all logical combinations are tested.

**4. State Transition Testing**
This technique is used when a system behaves differently depending on its **current state**.

Example states:

* Logged out
* Logged in
* Account locked

Testers verify correct transitions between states and check how the system behaves when invalid transitions occur.

**5. Use Case Testing**
Test cases are derived from **user scenarios or use cases** that describe how users interact with the system. This approach helps ensure that the system supports real-world workflows.

---

# 2. White-Box Testing Techniques

White-box testing techniques focus on **the internal structure of the software**, such as code logic, paths, and conditions. Test cases are derived from **knowledge of the program’s implementation**.

### Key Characteristics

* Requires understanding of **source code and system architecture**.
* Mostly performed by **developers or technical testers**.
* Ensures internal logic is properly tested.

### Common White-Box Techniques

**1. Statement Testing and Coverage**
This technique ensures that **every executable statement in the code is executed at least once** during testing.

Example:
If a function contains 10 statements, statement coverage ensures all 10 lines run during tests.

Coverage formula:

Statement Coverage =
(Executed Statements / Total Statements) × 100%

Higher coverage increases confidence that code logic has been exercised.

**2. Decision Testing and Coverage**
Decision testing checks that **all decision outcomes (true/false branches)** are executed.

Example:

```
if (age >= 18)
   allow access
else
   deny access
```

Tests must cover both:

* age ≥ 18
* age < 18

Decision coverage ensures all logical branches are tested.

**3. Condition Testing**
Condition testing verifies each **individual Boolean condition** inside decisions.

Example:

```
if (A && B)
```

Test cases must evaluate:

* A = true, B = true
* A = true, B = false
* A = false, B = true
* A = false, B = false

This ensures every logical condition behaves correctly.

---

# 3. Experience-Based Testing Techniques

Experience-based techniques rely on the **tester’s knowledge, intuition, and past experience** to design tests. Instead of strictly following specifications or code structure, testers use their understanding of common defect patterns.

### Key Characteristics

* Relies on tester expertise.
* Flexible and exploratory.
* Often used when documentation is incomplete.

### Common Experience-Based Techniques

**1. Error Guessing**
Testers predict potential defects based on their experience with similar systems.

Example guesses:

* Entering invalid data formats
* Submitting empty forms
* Uploading extremely large files

This technique often finds defects that structured methods might miss.

**2. Exploratory Testing**
Exploratory testing combines **test design, execution, and learning simultaneously**.

Instead of predefined test cases, testers explore the system dynamically while documenting findings. They continuously adapt their testing strategy based on observed behavior.

Benefits include:

* Discovering unexpected defects
* Improving understanding of the system
* Quickly identifying usability issues

**3. Checklist-Based Testing**
Testers use a **predefined checklist of common test scenarios** to guide testing.

Example checklist items:

* Validate input fields
* Test error messages
* Check UI responsiveness
* Verify security restrictions

This ensures consistent testing across projects.

---

# Summary of ISTQB Testing Techniques

| Category                 | Focus                   | Examples                                                                             |
| ------------------------ | ----------------------- | ------------------------------------------------------------------------------------ |
| Black-Box Testing        | System functionality    | Equivalence Partitioning, Boundary Value Analysis, Decision Tables, State Transition |
| White-Box Testing        | Internal code structure | Statement Coverage, Decision Coverage, Condition Testing                             |
| Experience-Based Testing | Tester knowledge        | Error Guessing, Exploratory Testing, Checklist Testing                               |

---

✅ **In simple terms:**

* **Black-Box** → Test based on requirements
* **White-Box** → Test based on code structure
* **Experience-Based** → Test based on tester expertise

Together, these techniques help testers design **efficient test cases, improve coverage, and detect defects more effectively**.

---
