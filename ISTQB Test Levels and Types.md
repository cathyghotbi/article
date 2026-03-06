Below is a clear explanation of **ISTQB Test Levels** and **ISTQB Test Types** as defined by the **International Software Testing Qualifications Board (ISTQB)**. These concepts explain **when testing is performed** (levels) and **what aspects of the system are tested** (types).

---

# 1. ISTQB Test Levels

Test levels represent **different stages in the software development lifecycle where testing activities occur**. Each level focuses on different parts of the system and has different objectives. The four main levels are **Unit Testing, Integration Testing, System Testing, and Acceptance Testing**.

---

## 1. Unit Testing

Unit testing is the **lowest level of testing** and focuses on verifying the smallest components of software, usually individual **functions, classes, or modules**. This testing ensures that each unit of code performs its intended function correctly.

Unit testing is typically performed by **developers** during the coding phase. The purpose is to identify defects in the code early before the components are integrated into larger parts of the system. Developers use frameworks and tools to automate these tests and run them frequently during development.

In unit testing, the internal structure of the code is known, which means it often uses **white-box testing techniques** such as statement coverage and decision coverage. For example, a developer might test a function that calculates a discount to ensure that it works correctly for different inputs and edge cases.

The main benefits of unit testing include early defect detection, easier debugging, and improved code quality. When a unit test fails, developers can quickly locate the issue because the test targets a small piece of code.

Overall, unit testing forms the **foundation of software quality** because errors are detected and fixed before they propagate into larger components of the system.

---

## 2. Integration Testing

Integration testing focuses on **verifying the interactions between different modules or components** of a system. Even if individual units work correctly, defects may appear when components communicate with each other.

This level of testing checks things like:

* Data flow between modules
* Interface compatibility
* Communication between services
* API interactions

Integration testing can be performed in several approaches, such as **top-down, bottom-up, big-bang, or incremental integration**. For example, if an e-commerce system includes modules for user accounts, payment processing, and order management, integration testing ensures that these modules work together correctly.

During this stage, testers may use **stubs and drivers** to simulate components that are not yet developed. For example, a stub may imitate the behavior of a payment gateway while testing the checkout module.

Integration testing helps detect issues such as incorrect data formats, broken API connections, or miscommunication between system components. By verifying interactions early, it reduces the risk of major system failures later in development.

---

## 3. System Testing

System testing evaluates the **complete and integrated software system** to verify that it meets the specified requirements. At this level, the entire application is tested as a whole rather than focusing on individual modules.

System testing is typically performed by **independent testing teams** rather than developers. It usually occurs after integration testing is completed and before the product is delivered to users.

This level focuses on verifying both **functional and non-functional requirements**, including:

* System behavior
* Performance
* Security
* Reliability
* Usability

Testers simulate real-world scenarios to ensure the software behaves correctly in its intended environment. For example, they may test how an online platform handles multiple users logging in simultaneously or how it processes large volumes of transactions.

System testing often uses **black-box testing techniques**, since testers focus on inputs and outputs rather than internal code structure.

The goal of system testing is to confirm that the entire system works according to the business requirements and is ready for acceptance testing.

---

## 4. Acceptance Testing

Acceptance testing is the **final level of testing** before software is released to users. Its purpose is to determine whether the system meets **business needs and user expectations**.

This type of testing is usually performed by **end users, customers, or business stakeholders** rather than developers or technical testers. The focus is on verifying that the system supports real-world workflows and delivers the expected value.

Common forms of acceptance testing include:

* **User Acceptance Testing (UAT)**
* **Operational Acceptance Testing (OAT)**
* **Contract Acceptance Testing**
* **Regulatory Acceptance Testing**

For example, during UAT, business users might test an accounting system by performing real tasks such as creating invoices, generating reports, and processing payments.

If the system passes acceptance testing, stakeholders approve it for deployment. If major issues are found, the system is returned to development for fixes.

Acceptance testing ensures that the software is **not only technically correct but also useful and aligned with business goals**.

---

# 2. ISTQB Test Types

While **test levels describe when testing occurs**, **test types describe what aspects of the system are tested**. Test types can be applied at multiple levels depending on the project needs.

---

## 1. Functional Testing

Functional testing verifies that the software performs the functions specified in the requirements. It focuses on **what the system should do** rather than how it is implemented.

Testers validate features such as:

* User login
* Data processing
* Form submissions
* Business rules

Functional tests typically use **black-box techniques**, where testers provide inputs and verify outputs. For example, a tester might verify that entering correct login credentials allows access while incorrect credentials produce an error message.

The objective is to ensure that every system feature works correctly and produces expected results. Functional testing is critical because it validates the **core functionality that users rely on**.

---

## 2. Non-Functional Testing

Non-functional testing evaluates **system characteristics rather than specific functions**. These tests assess qualities such as performance, reliability, and usability.

Common non-functional test types include:

* Performance testing
* Security testing
* Usability testing
* Compatibility testing
* Reliability testing

For example, a performance test might measure how many users a system can support simultaneously before response time degrades. Non-functional testing ensures that the system meets **quality attributes and operational requirements**.

---

## 3. Structural Testing

Structural testing focuses on the **internal structure and implementation of the system**. It ensures that code logic and internal paths are properly tested.

This type of testing often uses **white-box techniques**, such as:

* Statement coverage
* Branch coverage
* Path coverage

For example, testers verify that every decision point in the code has been executed during testing. Structural testing improves code quality by identifying hidden logic errors and untested paths.

---

## 4. Change-Related Testing

Change-related testing verifies that **software modifications do not introduce new defects** and that existing functionality continues to work correctly.

There are two main forms:

**Re-testing (Confirmation Testing)**
This verifies that a previously identified defect has been successfully fixed.

**Regression Testing**
This ensures that changes to the code have not negatively affected other parts of the system.

Regression testing is often automated and run frequently during development to maintain system stability.

---

# Summary

### Test Levels (When Testing Happens)

| Level               | Focus                          |
| ------------------- | ------------------------------ |
| Unit Testing        | Individual components          |
| Integration Testing | Interaction between modules    |
| System Testing      | Entire system behavior         |
| Acceptance Testing  | Business and user requirements |

### Test Types (What Is Tested)

| Test Type              | Focus                                                 |
| ---------------------- | ----------------------------------------------------- |
| Functional Testing     | System features                                       |
| Non-Functional Testing | Quality attributes (performance, security, usability) |
| Structural Testing     | Internal code structure                               |
| Change-Related Testing | Validating fixes and preventing regressions           |

---

✅ **Simple way to remember:**

* **Test Levels → stages of testing**
* **Test Types → aspects of software quality**

---

