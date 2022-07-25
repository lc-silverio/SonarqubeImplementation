# T11308: How to implement sonarqube in our workflow<!-- omit in toc --> 

## Purpose<!-- omit in toc --> 
- Document pending questions regarding how ``Sonarqube`` and ``Sentry`` should be integrated and how they will affect our workflow

---

## Table of Contents<!-- omit in toc --> 
  - [Integration into the workflow](#integration-into-the-workflow)
    - [Context](#context)
    - [During Development](#during-development)
    - [During Code Reviews](#during-code-reviews)
    - [During Testing / Quality review](#during-testing--quality-review)
    - [Support](#support)
    - [Older Projects](#older-projects)
    - [New Projects](#new-projects)
  - [External/Low/No code applications](#externallowno-code-applications)
  - [Other Companies](#other-companies)
  - [Resources](#resources)

---

## Integration into the workflow

### Context
- ``Sentry`` and ``Sonarqube`` will be integrated into our workflow as part of our development, review, support and quality control steps
- Both systems provide feedback on the general health of a given project and as such they can help our developers improve not only the applications we develop but also their coding skills and critical eye
- The main objective of these procedures and rules would not be to force developers to code in a given way, but to code in an homogeneous way that would:
  - Avoid errors
  - Enforce best practices
    - Rules to enforce best practices include conventions for comments and how to structure source files
  - Ensure consistency and maintainabilty
    - Rules to ensure consistency, include things like naming conventions, indent spacing and ordered import that althoug might not affect software functionality, should be consistent and clear throughout the engineering teams

### Before Development
- The acceptable grade must be defined at the start of the project and registered in the Impact assessment.

### During Development
- When developing new applications ``Sonarqube`` should be used as a support tool for the developer. 
- Using the feedback provided by the system (on each push/analysis) the developer must correct the code before sending it to review. This will help achieve better code as well as reduce the ammount of back and forth during code reviews
- Likewise ``Sentry`` should also be present as a monitoring tool with the objective of collecting data from errors that should be fixed before sending the code to merge
- With extensions, ``Sonarqube``'s capabilities can be further extended to improve the quality of the reports on the collected data
  - [SonarC#](https://www.sonarplugins.com/csharp) - Last Update 2020
- Tasks will be created to analyse the reports

### During Code Reviews
- Confirm that the continous is sending reports
- The senior developer will check the Sonarqube report grade. If the grade is under the minimal grade required the developer will be notified to do corrections to have a better grade.

### During Testing / Quality review
- During testing and quality review ``Sentry`` should be a part of the process.
- Here we validate that the application is logging events to ``Sentry`` and verify that the developer has solved previously logged issues and the code handles problems without crashing
- Also during this step the tester should review the report from ``Sonarqube`` to check that there were no major issues detected, especially ``Vulnerabilities``, if issues exist a task on open project must be created to solved them.

### Support
- While ``Sonarqube`` plays a greater role during development, during application support ``Sentry`` should recieve more focus
- A task will be added to the sprint (For any developer available). Events logged into ``Sentry`` should be analyzed during the sprint in order to contact the system responsible, they will decide the urgency and contact the system owner if a solution is required an HD will be created and follows the development process or a task will be added to backlog.

### Older Projects
- Validation from ``Sonarqube`` in older projects should be used applied in a case by case basis where company conventions should be employed first
- We can apply ``VB.Net Coding Style`` rules to our legacy and LTS projects, but ``Sonarqube`` will generate reports that would not be easy to handle.
- For these situations the proposition would be to only apply the ``C# Coding Style`` rules and keep evaluating `VB.Net` code during merge. 
- This way we can still work on improving new code following company convention for older applications

### New Projects
- For new/newer projects both ``Sentry`` and ``Sonarqube`` would be part of the foundation of our application, providing feedback to our code as it grows.
- For new projects it would be advisable that the rigorousness of ``Sonarqube`` would be bigger in order to avoid producing sub-par code right from the start 
- It should be defined a rule level where we can keep a balanced between creativity and conventions/maintainability
- Exceptions to the rule can still be applied but these should be **exceptions** and not bad habits.

### Dealing with Quality Gates
- When a new system is created/analysed in Sonar the Senior responsible must define the correct Quality Gate for the system. 
- When dealing with legacy projects we should start with a less regid set of rules and progressfuly set to the normal set of rules that are complient to the quality norms (ISO 5055:2021).
- System must keep above C grade.
- New rules can be sugested on the Developers Montly meeting.

# External/Low/No code applications
- Does not support
- Alternative: [Microsoft Powerapps code review tool](https://powerapps.microsoft.com/en-us/blog/power-apps-code-review-tool/)

# Other Companies
- Some use applications like [Sonarqube](https://marketplace.atlassian.com/apps/1212735/sonar-for-bitbucket?hosting=datacenter&tab=overview&utm_source=blog&utm_medium=unpaid-social&utm_campaign=P%3Amarketplace*O%3Aecosystem*H%3Afy22q2*I%3Acode-quality-blog*), Stylecop or Resharper
- Other apply conventions like PEP8(PY) or [ISO 5055:2021](https://www.it-cisq.org/standards/code-quality-standards/)
- Others publish guides ([Google](https://github.com/google/styleguide), [Nasa](https://ntrs.nasa.gov/citations/20080039927), [LinkedIn](https://github.com/linkedin/swift-style-guide), [Alibaba](https://alibaba.github.io/Alibaba-Java-Coding-Guidelines/), [AirBnB](https://github.com/airbnb/javascript), [Oracle](https://www.oracle.com/java/technologies/javase/codeconventions-introduction.html#16712))

# Resources
- [Software Engineering at Google by Tom Manshreck and Hyrum Wright](https://res.infoq.com/articles/software-engineering-google/en/resources/software_engineering_at_google_extract-1622201647282.pdf)
- [Coding Standards and Conventions in Software Development Team by Prince Sengayire](https://medium.com/@psengayire/the-importance-of-coding-standards-and-conventions-in-the-software-development-team-how-they-can-5d252556a05)
- [Code quality: a concern for businesses, bottom lines, and empathetic programmers by Isaac Lyman](https://stackoverflow.blog/2021/10/18/code-quality-a-concern-for-businesses-bottom-lines-and-empathetic-programmers/)
- [Code Complete  by Steve McConnell](http://aroma.vn/web/wp-content/uploads/2016/11/code-complete-2nd-edition-v413hav.pdf)
- [13 Good Coding Practices: What to Know in 2022 by Qulix Systems](https://www.qulix.com/about/blog/good-coding-practices/)
- [4 tips to improve code quality by Atlassian](https://www.atlassian.com/blog/add-ons/4-tips-to-improve-code-quality)
