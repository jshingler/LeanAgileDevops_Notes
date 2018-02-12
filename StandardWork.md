# Standard Work, a devOps Point of View

For the information below, ... It would be easy to get into a discussion is a given point, or technique a Lean, Agile, or DevOps thing.
There is overlap in Lean, Agile, and DevOps and this type of discussion is a waste of time.  Given that, we will not make a distinction.

Intents:
- Tracability
  All Changes to a solution must be tracable to the reason for the change.  In the case of code, or configuration, all changes must have
  a corresponding Story Card that explains the intent of the change and the acceptance criteria.  The Card Identifier, must be part of the
  commit message to source control.
  
  All changes to code and configuration must be source controlled.  "Source Control All Things"
  
  Misc:
  - Story cards should be small enough to complete in 3 days or less
  
## Application Architecture
- Establish Deployment Startegy (IaaS, CaaS, PaaS, OnPrem) 
- Establish System Context and Dependencies (Other Systems)
  - C4 Models - https://c4model.com/  
  NOTE: This should be a living document and maintained as Product Documentation
- Establsih High Level Architecture and Structure
- Establish Protocols and Styles (HTTPS, REST, Messaging, ...)
- Establish AuthN / AuthZ Style
- Establish Security Levels and Strategy
- Establish Performance Test Strategy / Plan
  
## Iteration 0
- Establish Story / Issue Management System access (Jira)
- Establish Source Code Repository access (Git)
  - Configure hook to validate commit message contains Story / Issue Mgmt Identifier
  - Configure hook to trigger Continuous Integration
- Define Source Control Strategy (Master or Branch, Gitflow, ... )
- Establish Binary Repository access (Nexus)
- Establish Static Analysis Capabilities (SonarQube, +Plugins)
- Establish Security Analysis Capabilities (SonaTypeIQ, ...)
- Determine Unit Testing and Component Testing Frameworks (Junit, Jasmine, ...)
- Code simplest possible "Hello World" Application, Service, Component
- Write Build Process Build, Unit Test, Component Test, Static Analysis Tasks (Gradle, Maven, NMake, ...)
  - Stub and Mock as appropriate
- Create Basic Continuous Integration Pipeline  (Concourse, Jenkins Pipeline)
  - Get Source Code (Prefer Webhook, Polling for change acceptable)
  - Compile
  - Unit Test
  - Component Test
  - Static Analysis
  - Security Analysis
  - Pipeline Must be Source Controlled too
  - Publish to Binary Repository
- Establish plan for managing sensitive data like passwords (Vault, CredHub, ...)
- Create Basic Continuous Delivery / Deployment Pipeline (Concourse, Jenkins Pipeline)  
If the team likes, Dev can be pushed automatically.  In order to not interrupt work anyone has in process,
QA and above should be pull based from the Binary Repository
  - Pre Deployment Validation of Component Dependencies before Deploying a component  
  (Database, other components, ...)
  - Post Deployment Validation - Smoke Test  
  Depending upon Component Dependencies, ... require standing up Mock and Stubbedd dependencies (MonteBank)
- Establish Monitoring and Alerting Process and Tooling  
  Monitoring and Alerting should be start in development, don't wait for Stage or Production.  Should be considered as 3 Amigos.
- Establish Performance Testing Process and Tooling  
  Criteria / Performance allocations should be establish for each layer of the solution and component / service (API)
- Establish Business Metrics expectations

## Daily

- Pull a Story Card
  - 3 Amigo to make sure Story and Acceptance Criteria are understood.
  - Assign Card to you
- Create a Source Control Branch
  - May be for a group of related cards
  - 3 Days or less of work
- Use Test Driven Development (TDD) Process during implementation.
- Unit Test and Component Test Coverage >= 70%  
  The Intent of Unit Tests and Component Tests are for the benefit of the engineer during the development process.
  - Stub and Mock as appropriate (Consider tools like http://www.mbtest.org/
- Automate Acceptance Criteria (ATDD)  
  NOTE: This is not the same as unit tests.
  ATDD is to prove that the Story Card Criteria have been met.
  - Stub and Mock as appropriate (Consider tools like http://www.mbtest.org/
- API Testing (if appropriate)
  - https://docs.pact.io/
  
  
## Iteration
- Implement and Execute Performance Tests
- Implement and Execute Security Tests

## Release
- Pre-Release Dependency Validation
  Is the proper version of the depend components deployed
- Release Validation (Smoke Tests)

## Run / Operations
- Monitoring and Alerting  
Production is #1, Consider Implications to team velocity, allocating points per iteration to production support.
- Analyze Business Metrics (Product Owner)  
Feeds into Prioritization and Backlog
- Log Aggregations (Splunk / Elk)



## 3 Amigo Considerations
- What are the security requirements (AuthZ)
- What are the Performance requirements (is 30 Second response oaky?)
- Are there Monitoring and Alerting considerations 
- Are there Business Metrics that should be captured
- Assume Nothing

  
  
  
  
 
