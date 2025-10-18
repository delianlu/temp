Version 2 - 13/10/2025 - Updated technologies (JUnit + Robolectric + AndroidX Instrumentation) and marked implemented tests as Pass.
# Test Plan

**Author**: Team017

## 1 Testing Strategy

### 1.1 Overall strategy

As part of the software verification process, the team will focus on the following aspects of verification for the Job Offer Comparison App.
* Perform dynamic verification through testing - The team plans to allocate most of its testing effort to dynamic verification by leveraging testing at different granularity levels.
    * Unit Testing - To test each function/method in isolation, the team will utilize unit testing (e.g., given the input salary, the getAdjustedSalary() method returns the correct value for adjusted salary). The goal is to identify failures and faults of the implementation at the early stages of development. Each team member will be responsible for writing a comprehensive unit test suite for the features they implement.
    * Integration Testing - To ensure the correct interaction between components during the execution of flows (e.g., the flow of the user comparing two jobs and viewing the comparison result), the team plans to implement an integration test suite. Once the complete system is formed by integrating individual efforts, one team member will be assigned to write an integration test suite to verify the correct behaviour of different flows as per the requirements.
    * System Testing - Once the system is fully integrated, the team plans to test the system end-to-end, covering all the flows manually. By utilizing various design artifacts (e.g., requirement specifications, use case documents), the team intends to validate the correct and uninterrupted system behavior. Furthermore, several non-functional aspects are also expected to be measured, including the system's performance. The team plans to assign one team member to perform the system testing.
    * Regression Testing - The team does not currently plan to perform regression testing.
* Perform static verification through inspection and formal proof of correctness. The objective is to ensure a correct and complete implementation with minimal defects and bugs. The team plans to utilize various design artifacts (e.g., requirement specifications, use case documents) to verify that the implementation adheres to these artifacts. To achieve this, the team plans to conduct code reviews, and each team member is responsible for reviewing and providing feedback on code developed by other team members as part of this static review process.


### 1.2 Test Selection

The team intends to utilize both black-box and white-box testing techniques during the testing phase. Since black-box testing does not require a complete system implementation to design the test suite, the team plans to employ black-box testing strategies to define the test suite in parallel to the system implementation. In this way, the team will have a ready-to-use test suite to start testing as soon as the system implementation is complete. Following the systematic functional-testing approach, the team will first list the testable features based on various design artifacts (e.g., requirement specifications, use case documents). Then, using domain knowledge, the team will identify input categories from which inputs for test cases should be drawn. Then the inputs for functions will be selected, covering interesting, edge, and corner cases. The team will also focus on maintaining an optimum number of test cases without overdoing it (e.g., writing several test cases for the validateWeight(int) method by providing inputs from the range 1 to 9). The black box testing approach is expected to be utilized at all granularity levels, which are unit, integration, and system.


Additionally, the team will employ the white-box testing strategy once the application implementation is completed. In this way, the team expects to cover code behaviors that are not captured through black-box testing and verify that the execution of logic is correct by defining a test suite with adequate statement, branch, and condition coverage. The white-box strategy will be utilized in unit and integration testing.


### 1.3 Adequacy Criterion

The team will measure the quality of test cases in the following aspects.

* Functional Coverage: To ensure the expected behavior of all system functionalities, the team will first define a complete list of functionalities to be tested by utilizing the requirement specification and the use case document. The functional coverage is then measured for a given test level as follows.
>Functional Coverage = $\frac{\text{Number of functions tested by test suite}}{\text{Total number of functions}}$
* Structural Coverage: The team will assess the structural coverage in following aspects.
  * Statement Coverage
    * Requirement:  More than 90% coverage. 
    > Coverage Measure: $\frac{\text{Number of statements executed by the test suite}}{\text{Total number of statements}}$

  * Branch Coverage
    * Requirement:  100% coverage. 
    > Coverage Measure: $\frac{\text{Number of branches executed by the test suite}}{\text{Total number of branches}}$

  * Condition Coverage
    * Requirement:  100% coverage. 
    >Coverage Measure: $\frac{\text{Number of conditions executed by the test suite}}{\text{Total number of conditions}}$

Since branch and condition coverage together subsume statement coverage, the team will focus on achieving 100% branch and condition coverage, which in turn results in 100% statement coverage. 

The team will measure unit testing adequacy based solely on structural coverage and integration test adequacy based on functional coverage. Since integration testing through functional coverage ensures correct interaction between components, the team decides not to re-measure the integration testing quality with structural coverage. The team will measure the quality of system testing based on the functional coverage. 

### 1.4 Bug Tracking

The team will utilize GitHub’s "Issues" feature to track bugs and enhancement requests. Once a Bug or a possible enhancement is found, the individual should create an issue with the following details.
* Title
* Type (bug or feature enhancement)
* A conscious summary of the bug/feature enhancement
* Steps to recreate (if bug)
* Relevant screenshots
* The expected behaviour and actual behaviour

In this way, the team plans to prioritize issues and resolve them throughout the development process. 


### 1.5 Technology

| Testing Type          | Technology |
|-----------------------|------------|
| Unit Testing          | JUnit, Robolectric |
| Integration Testing   | AndroidX Instrumentation (JUnit4) |
| System Testing        | Manual     |
| Performance Testing   | TBD        |


## 2 Test Cases

### Unit Tests

The unit test suite consists of the following test cases. These test cases were defined using the requirement document and the use case document of the system. All unit tests have been implemented and executed successfully, achieving 100% pass rate across 63 test methods.



| Test Case              | Purpose                                                          | Necessary Steps                                                  | Expected Result                                                                                    | Actual Result                                         | Pass/Fail |
|------------------------|------------------------------------------------------------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|-------------------------------------------------------|-----------|
| testEditCurrentJob     | Test the edit current job logic                                  | Execute the testEditCurrentJob test case in the unit test suite  | The current job details should be updated                                                          | Implemented (AddEditCurrentJobTest)                   | Pass      |
| testAddCurrentJob      | Test the add current job logic                                   | Execute the testAddCurrentJob test case in the unit test suite   | The given job should be set as the current job                                                     | Implemented (AddEditCurrentJobTest)                   | Pass      |
| testClearCurrentJob    | Test the remove current job logic                                | Execute the testClearCurrentJob test case in the unit test suite | The current job should be deleted                                                                  | Implemented (AddEditCurrentJobTest)                   | Pass      |
| testAddJobOffer        | Test the add job offer logic                                     | Execute the testAddJobOffer test case in the unit test suite     | The given job offer should be added to the list of job offers                                      | Implemented                                           | Pass      |
| testEditJobOffer       | Test the edit job offer logic                                    | Execute the testEditJobOffer test case in the unit test suite    | The given job offer details should be set for the selected job offer                               | Implemented                                           | Pass      |
| testRemoveJobOffer     | Test the remove job offer logic                                  | Execute the testRemoveJobOffer test case in the unit test suite  | The given job offer should be removed from the list of job offers                                  | Implemented                                           | Pass      |
| testShowJobRanked      | Test the logic of creating the list of ranked jobs               | Execute the testShowJobRanked test case in the unit test suite   | The correctly ranked list of jobs should be returned                                               | Implemented (5 tests in JobServiceRankingTest)        | Pass      |
| testCompareJobs        | Test the logic of comparing two given jobs                       | Execute the testCompareJobs in the unit test suite               | The correct job comparison result should be returned                                               | Implemented                                           | Pass      |
| TestEditPreference     | Test the logic of editing the user preference                    | Execute the testEditPreference in the unit test suite            | The user preference details should be updated                                                      | Implemented (15 tests in UserPreferenceTest)          | Pass      |
| testComputeScore       | Test the logic of computing a score for a given job              | Execute the testComputeScore in the unit test suite              | The correct job score should be calculated and returned                                            | Implemented (15 tests in JobServiceComputeScoreTest)  | Pass      |
| testValidatePreference | Test the logic of validating the UserPreference attribute values | Execute the testValidatePreference in the unit test suite        | For a given UserPreference, if all attribute values are valid, return true; return false otherwise | Implemented                                           | Pass      |
| testValidateJob        | Test the logic of validating Job attribute values                | Execute the testValidateJob in the unit test suite               | For a given Job, if all attribute values are valid, return true; return false otherwise            | No separate validateJob() method exists. Input validation is performed at UI layer in Activities. Covered by integration and system tests | N/A       |
| testEnsureComparable   | Test the logic of validating the comparability of two jobs       | Execute the testEnsureComparable in the unit test suite          | For given two jobs, if the two jobs are comparable, return true; return false otherwise            | Private method. Tested through <br/>testCompareJobs() | Pass      |
| testGetAdjustedSalary  | Test the logic for calculating the adjusted salary               | Execute the testGetAdjustedSalary in the unit test suite         | Return the calculated adjusted salary                                                              | Implemented                                           | Pass      |
| testGetAdjustedBonus   | Test the logic for calculating the adjusted bonus                | Execute the testGetAdjustedBonus in the unit test suite          | Return the calculated adjusted bonus                                                               | Implemented                                           | Pass      |

### Integration Tests

The integration test suite consists of the following test cases designed to verify the correct interaction between components during the execution of complete user flows. All integration tests have been implemented and executed successfully, achieving 100% pass rate across 17 test methods.


| Test Case               | Purpose                                           | Necessary Steps                                                             | Expected Result                                                                                            | Actual Result                                 | Pass/Fail |
|-------------------------|---------------------------------------------------|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|-----------------------------------------------|-----------|
| testEditCurrentJobFlow  | Test the flow of editing the current job          | Execute the testEditCurrentJobFlow test case in the integration test suite  | Current job details should be updated to the attribute values provided by the user                         | Implemented (CurrentJobIntegrationTest)       | Pass      |
| testAddCurrentJobFlow   | Test the flow of adding the current job           | Execute the testAddCurrentJobFlow test case in the integration test suite   | Current job details should be set to the attribute values provided by the user                             | Implemented (CurrentJobIntegrationTest)       | Pass      |
| testClearCurrentJobFlow | Test the flow of clearing the current job         | Execute the testClearCurrentJobFlow test case in the integration test suite | Current job should be cleared (set to null)                                                                | Implemented (CurrentJobIntegrationTest)       | Pass      |
| testAddJobOfferFlow     | Test the flow of adding a job offer               | Execute the testAddJobOfferFlow test case in the integration test suite     | A new job offer with the provided attribute values by the user should be added to the job offers list      | Implemented                                   | Pass      |
| testEditJobOfferFlow    | Test the flow of editing a job offer              | Execute the testEditJobOfferFlow test case in the integration test suite    | The selected job offer should be updated with the attribute values provided by the user                    | Implemented                                   | Pass      |
| testRemoveJobOfferFlow  | Test the flow of removing a job offer             | Execute the testRemoveJobOfferFlow test case in the integration test suite  | The selected job offer should be removed from the job offers list                                          | Implemented                                   | Pass      |
| testShowJobRankedFlow   | Test the flow of creating the list of ranked jobs | Execute  testShowJobRankedFlow test case in the integration  test suite     | A correctly ranked list of jobs should be returned                                                         | Implemented (JobServiceRankingTest)           | Pass      |
| testCompareJobsFlow     | Test the flow of comparing two given jobs         | Execute the testCompareJobsFlow in the integration test suite               | A list of JobComparisonData objects with the correct results should be returned for the two selected jobs. | Implemented                                   | Pass      |
| tesSetPreferenceFlow    | Test the flow of setting/editing user preferences | Execute the testEditPreferenceFlow in the integration test suite            | User preferences weights should be set to the values provided by the user                                  | Implemented (PreferenceIntegrationTest)       | Pass      |


### System Tests

The following flows, which are derived based on the requirement document and use case document, were tested manually during system testing. All system tests have been completed successfully, validating end-to-end functionality and user workflows.

| Test Case                | Purpose                                                  | Necessary Steps                                                                                                                                                                                | Expected Result                                                                                             | Actual Result | Pass/Fail |
|--------------------------|----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|---------------|-----------|
| Edit current job         | Test the end-to-end flow of editing the current job.     | 1. Go to the **Main Menu** <br>2. Select **Enter/Edit Current Job** <br> 3. Edit job details <br>4. Hit **Save** <br>5. Go back to the **Main Menu** and select **Enter/Edit Current Job**     | The current job attribute values should match the values provided by the user at the edit current job step. | Tested        | Pass      |
| Add current job          | Test the end-to-end flow of adding the current job.      | 1. Go to the **Main Menu**<br> 2. Select **Enter/Edit Current Job** <br> 3. Insert job details <br> 4. Hit **Save** <br> 5. Go back to the **Main Menu** and select **Enter/Edit Current Job** | The current job attribute values should match the values provided by the user at the add current job step.  | Tested        | Pass      |
| Add job offer            | Test the end-to-end flow of adding a job offer.          | 1. Go to the **Main Menu**<br> 2. Select **Enter Job Offer**<br> 3. Insert job offer details <br> 4. Hit **Save**                                                                              | A new job offer with the provided attribute values by the user should be added to the job offers list.      | Tested        | Pass      |
| Edit job offer           | Test the end-to-end flow of editing a job offer.         | 1. Go to **Main Menu** <br> 2. Select **Manage Job Offers** <br> 3. Tap **Edit** on an offer <br> 4. Change fields <br> 5. Hit **Save**                                                        | The selected job offer reflects the updated attribute values.                                               | Tested        | Pass      |
| Delete job offer         | Test the end-to-end flow of deleting a job offer.        | 1. Go to **Main Menu** <br> 2. Select **Manage Job Offers** <br> 3. Tap **Delete** on an offer <br> 4. Confirm deletion                                                                         | The selected job offer is removed from the list.                                                            | Tested        | Pass      |
| Compare two jobs         | Test the end-to-end flow of comparing two jobs.          | 1. Go to the **Main Menu** <br> 2. Select **Compare Job Offers**<br> 3. Select two jobs <br> 4. Hit **Compare**                                                                                | A comparison table for the selected two jobs should appear with the highest job score highlighted.               | Tested        | Pass      |
| Edit comparison settings | Test the end-to-end flow of editing comparison settings. | 1. Go to the **Main Menu** <br> 2. Select **Adjust Comparison Settings**<br> 3. Edit weights <br> 4. Hit **Save** <br> 5. Go back to the **Main Menu** and select **Adjust Comparison Settings** | The weights should match the values provided by the user at the edit comparison settings step.              | Tested        | Pass      |
