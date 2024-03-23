# Quality Assurance Handbook

## Introduction

## Task Estimation in Scrum

## Code Reviews

## Continuous Integration & Deployment

### Continuous Integration Workflow
![continuous-integration-workflow-diagram](/Image_Folder/continuous-integration-workflow-diagram.png)
#### Gitflow compliance
-	All developers must follow our company Gitflow branching strategy outlined in the diagram below and the following [link](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow).
![gitflow-diagram](/Image_Folder/git-flow-diagram.png)
#### Commiting practices
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
![test-pyramid-strategy-diagram](/Image_Folder/test-pyramid-strategy-diagram.png)

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
![parallel-test-execution-diagram](/Image_Folder/parallel-test-execution-diagram.png)

### Deployment Process 

#### Canary Strategy
- Developers should follow a Canary Deployment Strategy to ensure fast deployment and feedback while minimizing the risk of defects affecting users.
	- A new version of the application should be rolled out to a select group of users 
	- Data and feedback are gathered from the users and is incorporated into the new version before deploying to the entire user base
	- If an issue is identified we can roll back the application to the previous state and address the issues, which will only affect the canary users
	- We incrementally roll out the update to more users until all users are on the updated version, continuing to incorporate feedback and monitor the application 
    ![canary-strategy-diagram](/Image_Folder/canary-strategy-diagram.png)

#### Automatic Deployment Process
- Deployment similar to integration should be automated using CI/CD tools like Jenkins 
- Infrastructure as code should be used to ensure a consistent environment, tools like terraform and ansible should be utilised 
![automatic-deployment-diagram](/Image_Folder/automatic-deployment-diagram.png)

#### Feature Toggle
- Developers should implement feature toggle (or flags) to enable the toggling on and off of features without the need to redeploy code
- This is useful with canary as it allows us to make dynamic changes to our application without downtime.
![feature-toggle-diagram](/Image_Folder/feature-toggle-diagram.png)
#### Roll back Strategy
- The rollback strategy should be automatically triggered if the deployment fails, there is a significant increase in error rates, security vulnerabilities are detected or if user feedback is negative. 
- If the issue is feature-specific, we can toggle the feature off and either remove it or improve based on feedback. If the issue is more widespread we roll back to previous stable version. 

### Monitoring and feedback loops
![Monitoring_Feedback_Diagram](/Image_Folder/Monitoring_Feeback_Diagram.png)
* View: During the project building process, keep update and send feedback to different parts is important. 
* Adjustment: Feedback received by different departments to make changes. Improvement: Under the agile monitoring and feedback system, fast feedback, fast verification, and fast delivery are inevitable

### Security Practices 
- Establish inspection department: 
- Conduct safety awareness training：Software development teams must understand all the security challenges they may face during the development process. It would be helpful for them to learn about common security attacks related to software development, especially those related to their own enterprise domain. When developers know how cybercriminals and hackers work, they can avoid coding practices that can be exploited. Frequent meetings can be organized where team members can interact with each other and discuss secure development techniques. These sessions will help them understand how to write code that can withstand cyber-attacks.
- Security access authority: Databases are one of the most valuable and critical parts of any software system and therefore need to be properly configured and secured. A team needs to ensure that data does not result in leaks or unauthorized access due to overlooked vulnerabilities in the system. Implementing a digital user identity will allow security teams to restrict access to different users/developers so that they can only access what is needed for their work in a particular practice.


