![[software_testing_bootcamp.pdf]]
# How Software is Developed - Software Development Lifecycle Models

## Waterfall Model
The classic way of developing the software, which is the sequential development.

Sequential means that steps of the software development are done as a sequence of steps.

In sequential development, we have four main steps.

- Analysis. The business analyst analyzes the customer requirements. He writes down the documents like the SRS or the BRD.
- Design. We create wireframes, we create the UI design of the application.
- Implementation. We turn it into coding, whether it is front-end, back-end or mobile development.
- Testing

In sequential development we have two main lifecycles.

Steps that are included in the waterfall model:

- Requirements
- Design
- Development
- Testing
- Deployment
- Maintenance

## V-Model
The V model is also a sequential model.

| --- | ---- |
| --- | ---- |
| **Requirements**. The business requirements or the BRD cares about the client himself or the end customer. What will we deliver to him? | **Acceptance testing**. |
| **Specification**. The specifications or the SRS cares about the development team so it is delivered to the development team in order for them to know how will they deliver this functionality? | **System testing**
| **Architectural design** | **Integration testing** |
| **Detailed design** | **Unit testing** |

## Agile Software Development
In Agile in a general way we have 4 values and 12 principles.

The main idea behind Agile development is to deliver continuous feedback to the customer.

This is why some people call the Agile many waterfall(s) or many v-model because it is like the waterfall or the v-model, but within one week, two weeks, three weeks or at most one month.

Sometimes you see people referring to it as incremental or iterative development.

Agile is a philosophy or a way of thinking, and it can include more than one lifecycle.

Inside Agile we have Scrum, Kanban, spiral, XP and so on.

The most popular methodology in the Agile projects is called Scrum.

Scrums divides the projects into small iterations and we call them sprints, and each sprint is from one week to four weeks.

# Basic Concepts of Software Testing

## What is Software Testing?
Software testing can be dynamic testing or static testing.

Dynamic testing means that you execute the software.

In static testing we do not execute the software. We may review our code, search for maintainability issues in it, make sure that it follow the standards, review the requirements, review the design, review the user manuals, any type of review.

Software testing performs the two types: validation and verification.

Validation means that we build the right product. The product the user wants.

Verification means that we built that product right. So the architecture, the design, the performance, the security.

### Objectives of software testing

- Work-product evaluation
- Requirements fulfillment
- Building confidence
- Finding defects
- Preventing defects
- Providing information to stakeholders
- Reduce risk
- Compliance with laws

Objectives may vary

## Test Process
Any test process consists of three basic parts: planning, design and execution.

**Plan**
- Analysis
- Strategy
- Plan
- Tools

**Design**
- Test cases
- Scripts
- Scenarios
- Environment

**Execution**
- Test report
- Defect tracking
- Defect analysis
- Report

### ISTQB test process (2018)

- Test planning
- Test monitoring & control
- Test analysis
- Test design
- Test implementation
- Test execution
- Test completion

## Test Levels

- **Unit**. Focuses on components that are separately testable. Most of the time the person who is responsible for this level is the developer.
- **Integration**. Focuses on interactions between components or systems.
	- **Component integration**. Focuses on the integration between components. This level is also performed by the developer.
	- **System integration**. System testing is done by the tester.
- **System**. Tries to test the system as a whole. This is the most important test level for testers. We try to make the test environment correspond to the final target or production environment. We try to find as many defects as possible.
- **Acceptance**. Typically focuses on the behavior and capabilities of a whole system or product. Tries to make sure that the software performs correctly. Most of the time it is done by the users or the stakeholders. That's why we have a type of acceptance testing which is called alpha testing and beta testing.

## Testing Types

**Functional testing**
- Testing what the system does
- Usually answered with (Yes/No)

**Non-functional testing**
- Testing how the system performs
- Hard to answer with Yes/No
- Usually measured as a range

**Black-Box Testing**
- Testing without knowing the internal structure of the system.

**White-Box Testing**
- Testing while monitoring the internal structure of the system.

**Dynamic Testing**
- Testing that includes executing the software.

**Static Testing**
- Testing that doesn't include executing the software.

**Retesting (Confirmation testing)**
- Testing after debugging to ensure defects are fixed.

**Regression testing**
- Testing unchanged areas to ensure they are not affected by changes.

**Smoke testing**
- Testing main functionalities to ensure that the build is stable enough to continue testing.

## Test Scenario Writing

### What is a test scenario?
A test scenario is defined as any functionality that can be tested. It is also called *test condition* or *test possibility*. 

## Test Case Writing

### Test Case Writing

**Test case**
A set of preconditions, inputs, actions (where applicable), expected results and postconditions, developed based on test conditions.

1. **Test case title**. Verify login with a valid username and password.
2. **Precondition**. User is already registered using valid credentials.
3. **Test steps**. 
	1. Enter a valid username
	2. Enter a valid password
	3. Click on sign in
4. **Expected result**. User is logged in successfully and redirected to (XYZ) page.
5. **Test scenario (test suite)**. Login.
6. **Test environment**. Hardware, software and network. Windows 10 - Chrome - WiFi
7. **Actual result**. Never fill the actual result field until you execute the test case.
8. **Status**. 
	- **New (ready to test)**. The test case is not executed.
	- **Pass**. The test case is executed and the actual result is the same as the expected result.
	- **Fail**. The test case is executed and the actual result is different from the expected result. 
	- **Blocked/Skipped**. The test case can't be executed.

 
# Test Execution and Bug Reporting

## How to Write a Bug Report

**What is a defect?**
An imperfection or deficiency in a work product where it does not meet its requirements or specifications (synonyms: bug, fault).

1. **Bug report title**. Section -> Description. Register -> No error message appears when user leaves password field empty.
2. **Steps to reproduce**. 
3. **Expected result**. The same expected result like in the test case.
4. **Actual result**.
5. **Test environment**.
6. **Screenshot or video**.
7. **Bug priority**.
	- Critical
	- High
	- Medium
	- Low

## Types of Defects

1. **Functional**
2. **Visual (UI)**
3. **Content**
4. **Performance**
5. **Suggestion**
 
# Testing Reports: Test Progress & Test Summary Report

## What are testing reports and why do we need them?

**Test progress report**
A type of test report produced at regular intervals about the progress of test activities against a baseline, risks and alternatives requiring a decision. Synonyms: test status report.

**Test summary report**
A type of test report produced at completion milestones that provides an evaluation of the corresponding test items against exit criteria.

# Manual Software Testing Interview Questions

## What is the difference between SDLC & STLC?

**Software Development Life Cycle (SDLC)** is a process used by the software industry to design, develop and test high quality software. The SDLC aims to produce a high quality software that meets or exceeds customer expectations, reaches completion within time and cost estimates.

**Software Testing Life Cycle (STLC)** is a sequence of different activities performed by the testing team to ensure the quality of the software or the product. STLC is an integral part of SDLC, but STLC deals only with the testing phase.

## What are the different levels of software testing?

**Unit testing** aims to verify each part of the software by isolating it and then perform tests to demonstrate that each individual component is correct in terms of fulfilling requirements and the desired functionality (done by developers).

**Integration testing** aims to test different parts of the system in combination in order to asses if they work correctly together. By testing the units in groups, any faults in the way they interact together can be identified (done by developers).

**System testing**. All the components of the software are tested as a whole in order to ensure that the overall product meets the requirements specified (done by testers).

**Acceptance testing** is the level in the software testing process where a product is given the green light or not. The aim of this type of testing is to evaluate whether the system complies with the end-user requirements and if it is ready for deployment (done by users).

## What is the difference between a test case and a test scenario?

**Test scenario** is defined as any functionality that can be tested. It is also called test condition or test possibility. Example: test the login functionality.

**Test case** is a set of actions executed to verify a particular feature or functionality of your software application. A test case contains test steps, test data, precondition, postcondition. Developed for specific test scenario to verify any requirement. Example: test login with a valid username and a valid password.

The test scenario can be tested with more than one test case.

## What is the difference between functional and non-functional testing?

**Functional testing** is a type of testing which verifies that each function of the software application operates in conformance with the requirement specification. It tests what the system does.

**Non-functional testing** is a type of testing to check non-functional aspects (performance, usability, reliability, etc.) of a software application. It tests how well the system performs.

## What is the difference between validation and verification?

**Verification**
Are we building the product right?

- Verify the intermediary products like requirement documents, design documents, ER diagrams, test plan and traceability matrix
- Developer point of view
- Verified without executing the software code
- Techniques used: informal review, inspection, walkthrough, technical and peer review

**Validation**
Are we building the right product?

- Validate the final end product like developed software or service or system
- Customer point of view
- Validated by executing the software code
- Techniques used: functional testing, system testing, smoke testing, regression testing and many more

## When should we start testing in our project?
Software testing should start early in the Software Development Life Cycle. This helps to capture and eliminate defects in the early stages of SDLC i.e. requirement gathering and design phases. An early start to testing helps to reduce the number of defects and ultimately the rework cost in the end.

One of the seven principles of software testing is "Early testing saves time and money".

## What is exploratory testing, why do we use it?
Exploratory testing is an approach to software testing that is concisely described as simultaneous learning, test design and test execution.

In exploratory testing, test cases are not created in advance, but testers check system on the fly.

Exploratory testing is used for two reasons:

- When we don't have time to design test cases
- When there are poor or no requirements

## What is change-related testing? What is the difference between confirmation testing and regression testing?

**Confirmation testing or re-testing**
When a test fails because of the defect, then that defect is reported and a new version of the software is expected that has had the defect fixed. In this case we need to execute the test again to confirm whether the defect got actually fixed or not.

**Regression testing** is defined as a type of software testing to confirm that a recent program or code change has not adversely affected existing features.

Impact analysis is used to know how much regression testing will be required.

## What is the difference between black-box, white-box and grey-box testing?

**Black-box testing** is a software testing method in which the internal structure/design implementation of the item being tested is not known to the tester.

**White-box testing** is a software testing method in which the internal structure/design implementation of the item being tested is known to the tester.

**Grey-box testing** is a software testing technique to test a software product or application with partial knowledge of internal structure of the application. The purpose of grey-box testing is to search and identify the defects due to improper code structure or improper use of applications.

## Which test cases are written first, black-box or white box?
Black-box test cases are written first because their test basis are the user requirements and the SRS, while the test basis for white-box test cases are detailed design and component specification.

## What is use-case testing?
A use case is a description of a particular use of the system by an actor (a user of the system).

Each case describes the interactions the actor has with the system in order to achieve a specific task (or at least produce something of value to the user).

Actors are generally people but they may also be other systems.

Use case testing is a technique that helps us identify test cases that exercise the whole system on a transaction by transaction basis from start to finish.

## What is the difference between equivalence partitioning & boundary-value analysis?

**Equivalence partitioning** divides data into partitions (also known as equivalence classes) in such a way that all the members of a given partition are expected to be processed in the same way.

**Boundary value analysis (BVA)** is an extension of equivalence partitioning, but can only be used when the partition is ordered, consisting of numeric or sequential data. The minimum and maximum values (or first and last values) of a partition are its boundary values.

Behavior at the boundaries of equivalence partitions is more likely to be incorrect than behavior within the partitions.

## What is requirements traceability matrix?

**Requirements traceability** is the ability to connect requirements to other artifacts - such as different types of software tests or bugs. It's used to track requirements - and prove that requirements have been fulfilled.

**Bidirectional traceability** is the ability to trace forward (e.g. from requirement to test case) and backward (e.g. from test case to requirement).

**Requirement Traceability Matrix (RTM)** is a document that maps and traces user requirement with test cases. It captures all requirements proposed by the client and requirement traceability in a single document. The main purpose of the Requirement Traceability Matrix is to validate that all requirements are checked via test cases such that no functionality is unchecked during software testing.

## What is the difference between static & dynamic testing?

**Dynamic testing** involves the execution of the component or system being tested.

**Static testing** does not involve the execution of the component or system being tested. It relies on the manual examination of work products (i.e. reviews) or tool-driven evaluation of the code or other work products (i.e. static analysis).

## What is the test plan?

**Test plan**
A document describing the scope, approach, resources and schedule of intended test activities. It identifies amongst others test items, the features to be tested, the testing tasks, who will do each task, degree of tester independence, the test environment, the test design techniques and entry and exit criteria to be used, and the rationale for their choice, and any risks requiring contingency planning. It is a record of the test planning process.

As the project and test planning progress, more information becomes available and more detail can be included in the test plan. Test planning is a continuous activity and is performed throughout the product's lifecycle.

**Master test plan**
A test plan that typically addresses multiple test levels.

**Phase test plan**
A test plant that typically addresses one test phase.
 
## What is the difference between a mistake, defect, and failure?
A person can make an error (mistake), which can lead to the introduction of a defect (fault or bug) in the software code or in some other related work product.

An error that leads to the introduction of a defect in one work product can trigger an error that leads to the introduction of a defect in a related work product. 

If a defect in the code is executed, this may cause a failure, but not necessarily in all circumstances.

## What are the most important components of a defect report?

1. Title
2. Steps to reproduce
3. Expected result
4. Actual result
5. Priority
6. Screenshot or video

## What is risk based testing?

**Risk based testing (RBT)** is a software testing type which is based on the probability of risk. It involves assessing the risk based on software complexity, criticality of business, frequency of use, possible areas with defect, etc.

Risk based testing prioritizes testing of features and functions of the software application which are more impactful and likely to have defects.

Risk based testing steps:

1. Identify the risks
2. Analyze the risks
3. Prioritize the risks
4. Mitigate the risks

## What is the difference between alpha testing & beta testing?

**Alpha and beta testing** are typically used by developers of commercial off-the-shelf (COTS) software who want to get feedback from potential or existing users, customers, and/or operators before a software product is put on the market.

**Alpha testing** is performed at the developing organization's site, not by the development team, but by potential or existing customers, and/or operators or an independent test team.

**Beta testing** is performed by potential or existing customers, and/or operators at their own locations. Beta testing may come after alpha testing, or may occur without any preceding alpha testing having occurred.

## What is decision table testing?
Decision table testing is used for testing systems for which the specification takes the form of rules or cause-effect combinations. In a decision table, the inputs are listed in a column, with the outputs in the same column but below the inputs. The remainder of the table explores combinations of inputs to define the outputs produced.

## What is the waterfall model?
The waterfall model is the earliest SDLC approach that was used for software development.

The waterfall model illustrates the software development process in a linear sequential flow. This means that any phase in the development process begins only if the previous phase is complete. In this waterfall model, the phases do not overlap.

Requirements -> Design -> Development -> Testing -> Deployment -> Maintenance

## What is the V-model?
The V-model is an SDLC model where execution of processes happens in a sequential manner in a V-shape. It is also known as Verification and Validation model.

The V-model is an extension of the waterfall model and is based on the association of a testing phase for each corresponding development stage. This is a highly disciplined model and the next phase starts only after completion of the previous phase.

Requirement analysis - Acceptance testing
System design - System testing
Architecture design - Integration testing
Module design - Unit testing
Coding

# Basics of Agile & Agile Testing

## Agile 4 Values

**Individuals & Interactions over Processes and Tools**

**Working Software over Comprehensive Documentation**

**Customer Collaboration over Contract Negotiation**

**Responding to Change over Following a Plan**

## Agile 12 principles

1. Our highest priority is to satisfy the customer through early and continuous delivery of valuable software.
2. Deliver working software frequently, at intervals of between a few weeks to a few months, with a preference to the shorter timescale.
3. Working software is the primary measure of progress.
4. Welcome changing requirements, even late in development. Agile processes harness change for the customer's competitive advantage.
5. Continuous attention to technical excellence and good design enhances agility.
6. Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
7. Simplicity - the art of maximizing the amount of work not done - is essential.
8. Build projects around motivated individuals. Give them the environment and support they need, and trust them to get the job done.
9. The best architectures, requirements, and designs emerge from self-organizing teams.
10. Business people and developers must work together daily throughout the project.
11. The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.
12. At regular intervals, the team reflects on how to become more effective, then tunes and adjusts it behavior accordingly.

## User Story Definition
User stories are written to capture requirements from the perspectives of developers, testers, and business representatives. The user stories must address both functional and non-functional characteristics.

## Decomposing requirements

**Themes**
A scrum theme is the highest level of the story hierarchy. It describes a view of a tangible product or an abstract goal (such as performance tuning). A product owner further breaks down a theme into one or more epics. You may group features into themes in your product road map.

**Features**
A feature is a new capability provided to customers. Features are part of products at a very high level.

**Epic User Stories**
Medium-sized requirements that are decomposed from a feature.

**User Stories**
Requirement that contains a single action.

**User Tasks**
Actions required to develop a requirement of a user story.

## INVEST technique

- **Independent**. This means the requirement can exist outside of other user stories and still be meaningful. This allows for requirements and their user stories to be freely rearranged if necessary.
- **Negotiable**. User stories should also be general enough for the development team and client to work around their implementation. They should not focus on specific technical details. Instead, focus should be on the most important aspects of requirements, while remembering that these could change.
- **Valuable**. User stories should bring value to the client.
- **Estimatable**. It should be possible to estimate how much time it would take to design and implement the requirement in the user story.
- **Simple or Small**. A user story should be small because it is meant to be developed in a short time period. If the time to design and implement a requirement is uncertain, the user story is likely too big, so it should be broken down into smaller, manageable ones.
- **Testable**. User stories should be verifiable against a set of criteria in order to determine if it is "done", meaning that the user story has accomplished what it set out to do, and does not need further work. This is usually accomplished with acceptance tests.

## What is Scrum?

Scrum roles:

1. **Product Owner** is accountable for maximizing the value of the product resulting from the work of the Scrum team. The product owner is also accountable for effective product backlog management, which includes:
	- Developing and explicitly communicating the product goal
	- Creating and clearly communicating product backlog items
	- Ordering product backlog items
	- Ensuring that the product backlog is transparent, visible and understood
2. **Scrum Master** is accountable for establishing Scrum as defined in the scrum guide. They do this by helping everyone understand Scrum theory and practice, both within the Scrum team and the organization. The Scrum master is accountable for the Scrum team's effectiveness. They do this by enabling the Scrum team to improve its practices, within the Scrum framework. Scrum masters are true leaders who serve the Scrum team and the larger organization.
3. **Development Team**

## Scrum Practices

**Sprint**
Scrum divides a project into iterations (called sprints) of fixed length (usually two to four weeks).

**Product Increment**
Each sprint results in a potentially releasable/shippable product (called an increment).

**Product Backlog**
The product owner manages a prioritized list of planned product items. The product backlog evolves from sprint to sprint (backlog refinement).

**Sprint Backlog**
At the start of each sprint, the Scrum team selects a set of highest priority items from the product backlog. Since the Scrum team, not the product owner, selects the items to be realized within the sprint, the selection is referred to as being on the pull principle rather than the push principle.

**Definition of Done**
To make sure that there is a potentially releasable product at each sprint's end, the Scrum team discusses and defines appropriate criteria for sprint completion. The discussion deepens the team's understanding of the backlog items and the product requirements.

**Timeboxing**
Only those tasks that the team expects to finish within the sprint are part of the sprint backlog. If the development team cannot finish a task, it is moved back into the product backlog.

**Transparency**
The development team reports and updates sprint status on a daily basis at a meeting called the daily scrum. This makes the progress of the current sprint visible to everyone.

## Retrospective Meeting
Retrospective is a meeting held at the end of each iteration to discuss what was successful, what could be improved, and how to incorporate the improvements in future iterations.

## Kanban
Kanban is a management approach that is sometimes used in Agile projects. The general objective is to visualize and optimize the flow of work within a value-added chain.
 

# Mobile Testing Basics

## Types of Mobile Applications

**Native**
- Good performance
- High cost
- Installed physically on the device
- Examples: Google Maps, Facebook, LinkedIn

**Browser-based**
- Accessed through a mobile browser
- Low cost
- Easy to develop
- Browser compatibility testing is required

**Hybrid**
- A combination of native app and web app
- A website inside an app
- Easy to develop
- Can work offline

# API Testing

## HTTP Basics
Hypertext Transfer Protocol.

It consists of 4 parts:
- Startline (mandatory)
- Headers
- Blank line
- Body

**Start Line**
Request:
- Version (1.1 or 2)
- Method (Get-Post-Put-Delete)
- Folder & Parameters (/search?q=mohamedsalah)

Response:
- Version (1.1 or 2)
- Status code
	- 2xx (Good)
	- 4xx (Problem with the source)
	- 5xx (Problem with the API at the destination)

**Headers**
Request:
- Host (www.google.com)
- Token (used in security)

Response:
- Cookies
- HTML

**Blank Line**
It's a blank line to separate the header from the body.

**Body**
Request:
- Get (nothing in the body)
- Post (the data you provide, xml or json)

Response:
- What you requested
- HTML webpage

## XML Basics
- eXtensible Markup Language
- A format we use to send the APIs
- Created by W3C (the same organization created HTML)
- In XML, the terms in the tags don't mean anything
- In HTML, the terms mean something
- HTML is not extensible (you can't extend it to mean something else)
- Browsers can understand XML

HTTP header line: Content-Type: application/xml
HTTP body: XML

## JSON Basics
- JavaScript Object Notation
- It's the part of JavaScript that holds data
- JSON code is smaller than xml

HTTP header line: Content-Type: application/json
HTTP body: json

## SOAP & REST APIs

**SOAP**
- Simple Object Access Protocol
- It uses WSDL (web service description language)
- Start Line POST WSDL HTTP Version
- Header Line Content-Type: text/xml
- Blank Line
- Body XML Envelope formed using WSDL

**REST**
- Representational State Transfer
- Rest is representational, the actual record is not sent, a representation of the record is sent.
- Rest is stateless
- In SOAP, if the program stops (at the server), it breaks down then we have a major issue. REST waits until it works (stateless)
- REST uses JSON

# API Testing with Postman

## What is Postman?
- Postman is a tool that you can use to test your own REST APIs or external APIs.
- Postman is a browser.

## API Security: Authorization & Authentication

**Authorization in APIs**
Authorization is how we determine what things a given user is allowed to do.

**Authentication in APIs**
You need to test that different types of users only have access to the things that they should.

**Basic Auth**
Used for APIs that require you to specify a username and password in order to use the API.

# Performance Testing

## What is Performance Testing

**Time Behavior**
The most common performance testing objective. It examines the ability of the system to responde to user inputs within a specified time and under specified conditions.

**Resource Utilization**
If the availability of system resources is identified as a risk, the utilization of those resources (e.g. the allocation of limited RAM) may be investigated by conducting specific performance tests.

**Capacity**
If issues of system behavior at the required capacity limits of the system (e. g. numbers of users or volumes of data) is identified as a risk, performance tests may be conducted to evaluate the suitability of the system architecture.

**Performance Testing**
Performance testing is an umbrella term including any kind of testing focused on performance (responsiveness) of the system or component under different volumes of load.

**Load Testing**
Load testing focuses on the ability of a system to handle increasing levels of anticipated realistic loads resulting from transaction requests generated by controlled numbers of concurrent users or processes.

**Stress Testing**
Stress testing focuses on the ability of a system or component to handle peak loads that are at or beyond the limits of its anticipated or specified workloads.

**Scalability Testing**
Scalability testing focuses on the ability of a system to meet future efficiency requirements which may be beyond those currently required.

**Spike Testing**
Spike testing focuses on the ability of a system to respond correctly to sudden bursts of peak loads and return afterwards to a steady state.

**Endurance Testing**
Endurance testing focuses on the stability of the system over a time frame specific to the system's operational context.

**Concurrency Testing**
Concurrency testing focuses on the impact of situations where specific actions occur simultaneously (e.g. when large numbers of users log in at the same time)

**Capacity Testing**
Capacity testing determines how many users and/or transactions a given system will support and still meet the stated performance objectives.

## Concept of Load Generation

**User Interface**
May be an adequate approach if only a small number of users are to be represented.

**Crowds**
Depends on the availability of a large number of testers who will represent real users.

**APIs**
This approach is less sensitive to changes in the UI.

**Communication protocols**
This tool-based approach simulates very large numbers of users in a repeatable and reliable manner.

## Creating Load Profiles

A load profile specifies the activity which a component or system being tested may experience in production. It consists of a designated number of instances that will perform the actions of predefined operational profiles over a specified time period.

**Ramp-ups**: Steadily increasing load (e.g. add one virtual user per minute)
**Ramp-downs**: Steadily decreasing load
**Steps**: Instantaneous changes in load (e.g. add 100 virtual users every five minutes)
**Predefined distributions**: (e.g. volume mimics daily or seasonal business cycles)

# Codeless Test Automation using Selenium

## Introduction to Codeless Test Automation

Codeless automated testing, or codeless automation is the process of creating automated tests without writing a single line of code. Codeless automation lets teams automate the process of writing test scripts regardless of skill level.