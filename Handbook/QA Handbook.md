# Quality Assurance Handbook

## Introduction

## Task Estimation in Scrum

## Code Reviews

## Continuous Integration & Deployment

### Introduction
- CI/Cd is a DevOps practice which stands for Continuous Integration and Deployment. 

- **Continuous Integration** is the practice of committing code to a repository very frequently, these repositories have automated workflows to build and test the committed code. If either process fails, the team is informed, and merging is stalled until the issue has been resolved. This practice identifies issues in the code early, therefore reducing code incompatibility and merge conflicts.

- **Continuous Deployment** is the practice of frequently deploying code to production through automated pipelines. There are many deployment strategies, such as blue/green, canary, shadow, etc. We recommend Canary, as outlined, and justified [below.](#canary-strategy)


### Continuous Integration Workflow
<img src="/Image_Folder/continuous-integration-workflow-diagram.png" height="500">

#### Gitflow compliance
-	All developers must follow our company Gitflow branching strategy outlined in the diagram below and the following [link](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow).
<img src="/Image_Folder/git-flow-diagram.png" height="500">

#### Committing practices
-	Developers are encouraged to commit changes to their branches often (commit once one logical unit of work is completed)
#### CI platform integration
-	These commits should trigger an automated build and test process utilising a CI platform like Jenkins, Travis CI or GitHub actions.
#### Containerization Strategy
-	Automation should utilise containerisation solutions like docker to ensure a uniform build and testing environment that replicates the production environment. This avoids the famous “it works on my machine” issue.
#### Automated Testing Guidelines
-	Guidelines for creating these automated tests are in the section [below](#automated-testing)
#### Failure Response Protocol
-	If a build or test fails, the team should be notified so that the issue can be addressed immediately, no new code should be added until the issue is resolved.
#### Local and Manual Testing
-	Developers should not neglect testing locally, as over-reliance on automated testing may slow down our pipeline.
-	Developers should also not neglect manual testing; it is still important to perform Exploratory tests, User experience tests, etc, to test unique scenarios automation may not cover. 


### Automated Testing 

#### Test Pyramid strategy 

- The process where quick and simple tests are run first, followed by more complex tests that take longer to run. 
- We would first run unit tests, which are lightweight and ensure code work by addressing the smallest possible unit of behaviour. 
- Next Integration tests are used to test that different pieces of software interact with each other as expected.
- Next End to end test, which runs through the entire system are run. It is recommended to limit the number of these as they can take a long time and be flaky.
- Finally, performance testing is used to assess how a system will perform in a production-like environment using Load and Stress tests.
<img src="/Image_Folder/test-pyramid-strategy-diagram.png" height="500">

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
<img src="/Image_Folder/parallel-test-execution-diagram.png" height="500">

### Deployment Process 

#### Canary Strategy
- Developers should follow a Canary Deployment Strategy to ensure fast deployment and feedback while minimizing the risk of defects affecting users. This is ideal for our fast-moving team, to ensure we are developing quickly while also reducing the current issue of high defects making it to production.
	- A new version of the application should be rolled out to a select group of users 
	- Data and feedback are gathered from the users and is incorporated into the new version before deploying to the entire user base
	- If an issue is identified we can roll back the application to the previous state and address the issues, which will only affect the canary users
	- We incrementally roll out the update to more users until all users are on the updated version, continuing to incorporate feedback and monitor the application 
    <img src="/Image_Folder/canary-strategy-diagram.png" height="500">

#### Automatic Deployment Process
- Deployment similar to integration should be automated using CI/CD tools like Jenkins 
- Infrastructure as code should be used to ensure a consistent environment, tools like Terraform and Ansible should be utilised 
<img src="/Image_Folder/automatic-deployment-diagram.png" height="500">

#### Feature Toggle
- Developers should implement feature toggle (or flags) to enable the toggling on and off of features without the need to redeploy code
- This is useful with canary as it allows us to make dynamic changes to our application without downtime.

<img src="/Image_Folder/feature-toggle-diagram.png" height="400">

#### Roll back Strategy
- The rollback strategy should be automatically triggered if the deployment fails, there is a significant increase in error rates, security vulnerabilities are detected or if user feedback is negative. 
- If the issue is feature-specific, we can toggle the feature off and either remove it or improve based on feedback. If the issue is more widespread we roll back to previous stable version. 

### Monitoring and feedback loops
<img src="/Image_Folder/Monitoring_Feeback_Diagram.png" height="500">

* View: During the project building process, keep update and send feedback to different parts is important. 
* Adjustment: Feedback received by different departments to make changes. 
* Improvement: Under the agile monitoring and feedback system, fast feedback, fast verification, and fast delivery are inevitable
	- Good reviews and feedback are important to help steer the developer in the right direction.

### Security Practices 
- Software must ensure that its content, resource management, and its own characteristics, including its operating environment and connections between users, are hidden from unauthorized entities.
- Software and the resources managed by it must be resistant to active attacks, protected from modification and destruction by unauthorized users, and able to recover from damaged states.
- The software can be accessed by authorized users and used according to demand, that is, the use of the system and resources by legitimate users will not be unreasonably denied.



