The **International Software Testing Qualifications Board (ISTQB)** defines a **structured Test Process** that describes the activities performed during software testing. This process ensures testing is organized, traceable, and aligned with project goals. It typically consists of **six main phases**: **Test Planning, Test Monitoring & Control, Test Analysis, Test Design, Test Implementation, Test Execution, and Test Completion (Closure)**.

---

# 1. Test Planning

Test planning is the **first phase of the testing process**, where the overall testing strategy and objectives are defined. The main goal is to determine **how testing will be performed during the project**.

During this phase, the test manager or test lead prepares a **test plan** that outlines the scope, resources, schedule, and approach for testing. Important decisions are made regarding which features will be tested, the types of testing that will be performed, and the tools that will be used.

Key activities include:

* Defining **test objectives and scope**
* Identifying **test levels and test types**
* Estimating testing effort and resources
* Assigning roles and responsibilities
* Selecting **test tools and environments**
* Identifying **risks and mitigation strategies**

For example, in a banking application project, the test plan may define that system testing will include functional testing, security testing, and performance testing. It may also specify deadlines and responsible team members.

Test planning ensures that testing activities are **well-organized, realistic, and aligned with project constraints** such as time, cost, and risk.

---

# 2. Test Monitoring and Control

Test monitoring and control occurs **throughout the entire testing lifecycle**. Its purpose is to track testing progress and ensure that activities stay aligned with the test plan.

**Test monitoring** involves collecting information about testing progress, such as:

* Number of executed test cases
* Number of passed or failed tests
* Defects discovered
* Test coverage

**Test control** involves taking corrective actions if the testing process deviates from the plan. For example, if testing falls behind schedule, the team may add more testers, adjust priorities, or focus on high-risk areas.

Typical monitoring tools include **test dashboards, defect tracking systems, and progress reports**.

For instance, if a large number of critical defects are found during system testing, the team may temporarily pause further testing until the development team fixes the issues.

This phase helps ensure that testing remains **effective, transparent, and aligned with project goals**.

---

# 3. Test Analysis

Test analysis focuses on **identifying what needs to be tested**. Testers analyze requirements, user stories, specifications, and system documentation to determine the testing conditions.

A **test condition** is an item or feature that should be verified by testing. For example:

* Valid login functionality
* Correct calculation of taxes
* Secure password handling

During this phase, testers also prioritize test conditions based on **risk and business importance**. High-risk areas of the system are given more attention during testing.

Testers often collaborate with developers, analysts, and stakeholders to clarify requirements and identify potential ambiguities or missing information.

For example, if a requirement states that “the system must process payments quickly,” testers may ask for clarification on acceptable response time.

Test analysis ensures that testing is based on **clear, well-understood requirements** and that critical features receive adequate coverage.

---

# 4. Test Design

Test design involves **creating detailed test cases and test scenarios** based on the test conditions identified during test analysis.

During this phase, testers determine:

* Test inputs
* Expected results
* Required test data
* Test procedures

Testers also choose appropriate **testing techniques**, such as equivalence partitioning, boundary value analysis, or decision tables.

For example, if a login feature is being tested, test cases may include:

* Valid username and password
* Invalid password
* Empty input fields
* Locked account scenario

Test design also ensures **traceability** between test cases and requirements. This is often documented using a **requirements traceability matrix (RTM)**.

The goal of this phase is to ensure that test cases are **systematic, comprehensive, and aligned with project requirements**.

---

# 5. Test Implementation

Test implementation prepares everything needed to **execute the designed tests**.

Key activities include:

* Creating and organizing **test cases into test suites**
* Preparing **test data**
* Setting up the **test environment**
* Writing **automated test scripts** if automation is used
* Verifying that all necessary tools and systems are available

For example, testers may configure a testing environment that simulates production conditions, including databases, servers, and external services.

Testers may also prepare **test execution schedules** and ensure that dependencies between tests are understood.

The objective of this phase is to ensure that testing can proceed **smoothly and efficiently** without delays caused by missing resources or configurations.

---

# 6. Test Execution

Test execution is the phase where **test cases are actually run** against the software system.

During execution, testers perform the following activities:

* Run test cases manually or automatically
* Compare **actual results with expected results**
* Record the outcomes of tests
* Report any defects discovered

If a test case fails, a **defect report** is created and sent to the development team. The defect report typically includes information such as:

* Steps to reproduce the issue
* Expected result
* Actual result
* Screenshots or logs

Once developers fix the defect, testers perform **re-testing** to confirm the fix and **regression testing** to ensure other functionality is unaffected.

Test execution is often the most visible part of testing because it directly reveals system defects.

---

# 7. Test Completion (Closure)

Test completion occurs **after all planned testing activities are finished**. The purpose is to finalize testing, document results, and evaluate the testing process.

Key activities include:

* Verifying that all planned tests have been executed
* Ensuring all critical defects are resolved
* Creating **test summary reports**
* Documenting lessons learned
* Archiving test artifacts for future reference

A **test summary report** usually includes:

* Total number of tests executed
* Number of passed and failed tests
* Defects found and fixed
* Overall assessment of product quality

The team may also conduct a **retrospective meeting** to identify improvements for future projects.

Test completion ensures that testing results are clearly documented and that the organization gains knowledge to improve future testing efforts.

---

# Summary of the ISTQB Test Process

| Phase                     | Purpose                               |
| ------------------------- | ------------------------------------- |
| Test Planning             | Define strategy, scope, and resources |
| Test Monitoring & Control | Track progress and adjust testing     |
| Test Analysis             | Identify what needs to be tested      |
| Test Design               | Create test cases and scenarios       |
| Test Implementation       | Prepare test environment and data     |
| Test Execution            | Run tests and report defects          |
| Test Completion           | Finalize testing and document results |

---

✅ **Simple way to remember the ISTQB Test Process:**

**Plan → Monitor → Analyze → Design → Implement → Execute → Close**

---

