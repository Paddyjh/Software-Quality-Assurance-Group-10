# Quality Assurance Handbook

## Introduction

## Task Estimation in Scrum

## Code Reviews

## Continuous Integration & Deployment

### Continuous Integration Workflow

### Automated Testing 

#### Test Pyramid strategy 

- The process where quick and simple tests are run first, followed by more complex tests that take longer to run. 
- We would first run unit tests, which are lightweight and ensure code work by addressing the smallest possible unit of behaviour. 
- Next Integration tests are used to test that different pieces of software interact with each other as expected.
- Next End to end test, which runs through the entire system are run. It is recommended to limit the number of these as they can take a long time and be flaky.
- Finally, performance testing is used to assess how a system will perform in a production-like environment using Load and Stress tests.

#### Test Coverage
- Although not an exact science a minimum of 80% coverage is recommended.
- It is crucial to develop quality tests as line coverage does not translate to quality tests.
	
#### Regular Test updates
- Tests should be regularly reviewed to ensure that they are of high quality and cover new features as they are added.

#### Flaky Test Management
- These are tests that both pass and fail without changes to the test or code, which slows down the CI/CD pipeline.
- Addressing the issue: Label as flaky so these tests run separately until fixed, identify poor data management, and check test environment management.
- Avoid using delays or sleep methods.

#### Parallel Test Execution 
- The test suite should be segmented and run in parallel. 
- This facilitates quicker feedback, better usage of our resources, and increased test coverage as we can now run more tests.


### Deployment Strategies 

### Monitoring and feedback loops

### Security Practices 
