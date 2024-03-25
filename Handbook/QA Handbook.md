# Quality Assurance Handbook

## Introduction

## Task Estimation in Scrum

## Code Reviews

### What Are Code Reviews?
 
 - A code review is the process of getting feedback and approval from other developers on submitted code before it is merged into the main codebase. 
 - A code review is an essential practice for ensuring that the code meets predetermined standards, is of high quality, and is free from bugs.
 - Many companies practice different processes of how to carry out code reviews. Different processes depend on a number of factors such as, the level of experience of developers, specific project or regulatory requirements,and the complexity and lifecycle stage of the project, etc. Below are some different approaches:
    - Checklist-Based Reviews - where reviewers follow a predetermined list of checks to follow while reviewing code.
    - Pair Programming - involves two developers, where a developer codes and gets real-time feedback off another developer (code review) on their code.
    - Pre-Commit Reviews - This is where code is reviewed before it is merged into the main branch.
- Google mandates code reviews and follows the Pre-commit review. Below is a diagram of their Code Review Flow.

<img src="../Image_Folder/GoogleCRFlow.png" height="500" width="500"> 

### Best Practices for Conducting Effective Code Reviews

- This section highlights key practices for both reviewers and reviewees that we believe are beneficial in fostering a positive and productive feedback environment.

- For Reviewers
    - The reviewer should possess enough experience to effectively identify key aspects such as design, logic, and bugs.
    - Adhere to a predefined checklist that define the goals and standards of the review process.
    - Code reviews should not be rushed to avoid code smells entering the main codebase. Limiting code review sessions or setting a maximum line of code (LOC) per hour can ensure that the reviewer does not lose focus.
    - Feedback should be constructive. Providing constructive feedback helps to enhance understanding and learning rather then incite competition or conflict.
- For Reviewees
    - Reviewee must be receptive to feedback. They must have a willingness to learn and understand criticism is not personal.
    - Code must be reviewed and tested by the reviewee before requesting a code review.This saves the reviewers from having to respond to miscellaneous errors such as spelling mistakes.
    - Seek and give clarity when needed. Be prepared to offer clarity on code you have produced and seek clarity when feedback is unclear.
    - Small, incremental code changes should be the aim as code with many lines is more strenuous to review. 

<img src="../Image_Folder/@iamdeveloper_tweet.png">


### The Psychological Aspects of Code Reviews

- Understanding the psychological aspects of code reviews are vital to ensure effective code reviews because they impact team collaboration dynamics and team members personal growth. Code review procedures can be improved and made more productive by comprehending and taking care of these factors. 

- Ownership: The 'endowment effect' shows that people value their work more highly simply because it's theirs, making objective self-review and acceptance of criticism challenging.
- Worthwhileness vs Conflict Potential: When conducting a code review, certain review comments will carry more risk of potential conflict and may not be worthwhile commenting while some comments are certainly worthwhile. To explain, below is a grid that places certain comments along two axes: worthwhileness and conflict potential. 

<img src="../Image_Folder/WorthVSConflict.png" height="500">

- Below are approaches both reviewers and reviewees can take to avoid conflict and encourage collaboration.
    - Reviewers
        - Use collaborative language and avoid using the word "You". For example, a better way of saying "Your code is inefficient" would be "How could we optimize this for better performance".
        - Avoid leaving many comments where possible as this can demotivate the reviewer, instead prioritise essential comments, which brings the code up to a level of acceptance.
        - As well as leaving constructive feedback, always attempt to leave a positive comment on something you felt was done well. This can boost the confidence of the reviewee.
    - Reviewee
        - Ensure you reply to comments left by a reviewer as well as thanking them for taking the time to review your code.
        - Ensure to annotate your pull request to give context to your changes to the reviewer.

### Advantages and Disadvantages of Code Reviews

- **Advantages of code reviews**
    - **Enhanced code quality:** Independent reviewers can identify spelling mistakes, formatting issues, potential bugs, errors in logic, or security vulnerabilities that automated testing may miss, therefore enhancing the code quality and reducing the risk of bugs.
    - **Mentorship:** Code reviews allow developers to gain insights into their own code from feedback from developers with varying experiences, allowing the developer to improve their coding ability.
    - **Knowledge Sharing:** Reviewers can also learn best practices from reviewing other developers' code while also gaining a better knowledge of the code base as they may be asked to review a section of code they have never looked at before.

- **Disadvantages of code reviews**
    - **Time-consuming:** Code reviews can be time-consuming, taking time away from developing features, which can delay releases, especially in teams with limited developer capacity.
        - Mitigation: Ensure the team spreads the work of code reviews, avoiding over-reliance on certain developers.
    - **Conflict potential:** The potential for conflict to arise among developers if opinions differ and communication is not polite/collaborative.
        - Mitigation: Ensure all team members communicate in a collaborative and professional manner.
    - **Demoralizing:** Similarly, if feedback is not presented in a rude or non-constructive manner, the developer may feel demoralized and unmotivated.
        - Mitigation: Ensure feedback is given in a constructive and respective manner. 
    - **Oversights:** There is always a risk that some bugs, bad practices, etc, may be overlooked by reviewers, especially if a review is long, and fatigue may play a factor.
        - Mitigation: Encourage smaller incremental changes to reduce the size of code reviews, set a time limit for looking at a code review in one sitting and introduce automation tools to identify issues early and reduce the number in reviews.

### Code reviews in CI/CD
- Code reviews play an important role in the continuous integration and deployment process which is outlined [below](#continuous-integration--deployment).
- Code reviews occur when a pull request is created to merge a branch into the develop branch after passing the automated tests.
- Code reviews can also be automated using static analysis tools, linters, and automated security vulnerability scanners. These tools can automatically flag potential issues before a human reviewer looks at the code.


## Continuous Integration & Deployment

