- [Introduction](#Introduction)
- [Recent Accomplishments](#Recent-Accomplishments)
- [Project Showcases](#Project-Showcases)
- [Tech Profile - skills, languages, platforms, etc.](#Tech-Profile)

# Introduction
- Technology Executive
- Cloud Architect
- Operational Team Lead with deep hands on experience
- AI-assisted development and tooling to 10X developer productivity based on software craftsmanship and design patterns
- Ability to navigate complex situations with minimum information to provide clarity, direction and an actionable path forward

I enjoy helping companies and teams build software through improving team processes, delivering business value utilizing my 20 year experience in software design principles.

# Recent Accomplishments

- Application Modernization project for a northeast Ohio locally owned and operated discount closeout and grocery store, with 61 stores throughout the region, completed and launched in 12 month engagement resulting in improved speed and accuracy in warehouse orders, improved User Experience, and clearing the blocker for infrastructure upgrades
- Avon Lake High School - C# and API Development, held session with Avon Lake High School AP Computer Science students (grades 10, 11, and 12). We covered API development with Blazor and C#, talked about careers in the field and topics such as client/server, http verbs, status codes, and data modeling. While we didn't get a chance to finish our homework forecaster based on the NOAA weather API, it was good to be back in the classroom after my days at Microsoft's TEALS.
- Team Leadership and Cloud migration: Instituted software development best practices, cloud migration and future architecture for a 200M corporation; leading to faster delivery of new features and higher code quality.
- Recent project launch for large distributed application, being the driving force behind: API architecture, container orchestration, data structures, framework and platform evaluations, customer identity and access management, Agile methodologies, CI/CD processes, and client-side frameworks React/NextJS to support the rapid growth and expansion of the 200M corporation.
- Modernization of a cloud-native, line-of-business application for a Fortune 500 electric utility company, utilizing Azure Cloud Infrastructure, Microsoft Entra B2B and B2C, Angular, including custom JWT/OAuth2 implementation, and .NET following Domain Driven Design. Successfully completed within the target budget of 1M, achieved through effective prioritization, constant client communication and scope management.
- Experience in React Native for web and mobile development of SaaS company.
- Speaker THAT Conference - Azure DevOps for Agencies
- Defining and driving company goals and exemplifying company values through example, 1 on 1s, and creating a safe, healthy, and desirable place of employment for all employees.
- Mentorship of junior developers in coding best practices, design patterns, and setting proper example of how to be a professional developer.

# Project Showcases

## Inventory Management and Intranet Application Modernization - Northeast Ohio Grocery Store Chain
### Background
The client is a northeast Ohio locally owned and operated discount closeout and grocery store, with 61 stores throughout the region. Their inventory represents name brand merchandise in the groceries, health and beauty, and general merchandise categories.
Store daily inventory ordering, pharmacy data, employee training core business functions were handled through a bespoke Intranet application written in the late 90's and early 2000's. Inventory ordering functionality is critical to keeping stock and items available through numerous internal and external warehouses. The legacy technology stack utilized was Microsoft ASP (Active Server Pages), Visual Basic 6.0 ActiveX/COM objects, and a on-premise Microsoft SQL server with SSIS/DTSX Integration Services.

### Challenges / Pain Points
The user experience was extremely cumbersome. Performing daily tasks of ordering inventory were clunky, unintuitive and prone to errors.
Validation was initially handled through client-side Visual Basic and some Javascript presenting huge problems in modern browsers, blocking the release of latest versions.
The heavy use of COM objects and ActiveX were blocking server operating systems upgrades.
Overall security grade of the application was extremely low due to age and numerous advances in technology over the last nearly 30 years.
Internal business processes for handling application changes were not documented, stored in source control, and without control systems.

### Goals
The number one priority was to remove the ActiveX/COM objects. Second was to rewrite the Inventory Ordering critical business function improving UI/UX, validation and streamlining external warehouse integrations. Due to budget constraints the entire application could not be rewritten, however, the goal of eliminating Active Server Pages when appropriate was a close third.
Solution and Approach

There were several constraints when preparing the application modernization strategy for the new system:

* On-premise hosting of the application and database
* Limit changes to the database structure and scheme due to other systems integrations and maintain the existing SQL stored procedures
* Limit the external dependencies on Microsoft Azure infrastructure

The approach is to use Domain Driven Design under a modular monolith. The audience of the application was small; less than 100 store managers who interacted with it daily. Additionally, I had only be concerned with private/internal access to the application for authentication and authorization.

Technology Stack: .NET 9.0 / Razor pages, Entity Framework, EF PowerTools to aid in stored procedure input/output scaffolding.

A new template was developed using Bootstrap and the Material Design Framework MudBlazor.
Azure DevOps for source control, work items, and CI/CD pipelines was utilized.
### Key Takeaways / Lessons Learned
Using an agile approach to the project went very well. This kept the client informed of the progress, gave them opportunities to review progress made and discuss any questions. With a smaller team, we met weekly and after a few couple of reviews, meeting time was typically about 15-20 minutes making everyone happy.
Having the SQL schema remain unchanged (or adjusted in a non-breaking fashion) proved to be challenging. Additionally, where appropriate, the business logic was migrated to the domain carefully.

#### Skills
Blazor · Microsoft AzureDevOps CI/CD Pipelines · Technology Leadership · Agile Methodologies · C# · .NET · MS SQL · Entity Framework · Application Modernization · Strangler Fig · Domain Driven Design

## Strategic Technology Direction, Roadmap, Application Modernization - Perfect Game

Perfect Game USA is an organization dedicated to the development and promotion of youth baseball.
They host travel team tournaments and individual showcases, to promote and provide valuable
exposure for young athletes and to gain exposure to college coaches and MLB scouts.

Prior to Bennett Adelson’s involvement, Perfect Game lacked effective internal software development,
delivery, poor code quality, little to no QA and no Agile processes or ceremonies. The team often faced
urgent issues without the necessary system processes or guidance.

To address these concerns the engagement was divided into three phases:

- Phase I: Migration from Rackspace to Azure for all business-critical applications and databases
- Phase II: Software Development Practices and Procedures, Agile transformation, and Continuous
  Integration and Continuous Deployment
- Phase III: Defining the Future State, Software Architecture

### Phase I - Azure App Services and Azure SQL Managed Instance

The infrastructure footprint at Rackspace was comprised of several large dedicated virtual machines that
were expensive to maintain, were running outdated operating systems and applications, and were not
configured for reliability and scalability. As such, business applications were migrated to Azure app
services and core database services were migrated to Azure SQL Managed Instance.

### Phase II - Leadership, Agile Ceremonies, and Azure DevOps Pipelines and git

Workflows

Software development processes for the entire 10-person development team had numerous bad
practices. For example, the team was deploying code to production directly from their workstations.
Code was not routinely merged into a main branch for other developers.

### Phase III Defining the Future State and Software Architecture

Perfect Game USA over the years has put an enormous effort into the software that runs their business without a long-term vision. Bennett Adelson worked with Perfect Game to define the future tech stack and direction.

#### Skills

Technology Roadmapping · Microsoft Azure · Technology Leadership · Agile Methodologies · C# · .NET Core · Application Modernization · Application Programming Interfaces (API) · NextJS · Strangler Fig · Domain Driven Design

## Application Modernization – FirstEnergy, Pennsylvania Customer Assistance Program - PCAP

FirstEnergy is a Fortune 500 utility company operating in the Northeast region of the United States. The Pennsylvania Customer Assistance Program (PCAP) is designed to help income qualified residential customers maintain electric service and eliminate their past due balance. The legacy application was written in the late 90s and due to its age was only used internally by FirstEnergy employees. The public facing online enrollment was handled and managed by an external third-party Dollar Energy Fund. FirstEnergy was looking to bring the application in-house to provide updated application security, increased systems integrations with backend systems, and greater visibility into customer issues and eliminate duplicated processes and data entry.

Since the legacy application was written approximately two decades ago, and since the system workflow, data processing and customer service were largely handled by an external third party uncovering or discovering the core business logic was extremely difficult. An extended period was dedicated to requirements with activities such as Event Storming and in-depth team interviews were conducted, striking a balance between agile and waterfall for discovery.

Once the system boundaries were understood, the team adopted Domain-Driven Design as a software paradigm. Team members consisted of both Bennett Adelson members, a senior developer, UI/UX designer, and cloud architect as well as members of FirstEnergy developer staff and a project manager. The application had a very complex, time sensitive workflow process and data management requirements.

Following this principle, this allowed the team to move in a very agile fashion with a
focus on just-in-time requirement gathering. Additionally, the budget and scope allowed for frequent refactoring. Having the latitude to rework core sections as the team learned more about the system and how it should behave was crucial for the success of the project.

#### Skills

Cross-functional Team Leadership · SAP Integration · Angular · C# · Domain-Driven Design (DDD) · Cloud Computing · Application Modernization · .NET Core · Application Programming Interfaces (API)

# Tech Profile

A listing of recent technologies and other items to help give additional context. Hardly an exhaustive list.

### AI
- Anthropic Claude
- Github Copilot
- ChatGBT
- Agenic workflows
- MCP servers

### Languages

- .NET (Core)
- Typescript
- Angular
- React Native
- NextJS

### Application Modernization
- Reverse Proxy YARP
- Strangler Fig
- .NET Framework -> .NET
- Current State vs Future State
- Roadmapping
- Dependency mapping
- Monolith, Modular Monolith, Microservices
- Migration and modernization tools, Azure Migrate

### Paradigms

- Azure Enterprize Architecture / Azure Landing Zones
- Domain Driven Design
- Minimum Apis
- GraphQL
- CI/CD pipelines (DevSecOps)
- API / Microservces
- Events/Messaging
- Mobile development
- Docker
- Azure Aspire
- git, branching strategies
- Event Storming
- CQRS
- Mediator

### Security
- OAuth
- OpenID Connect - OICD
- EntraAD, MSAL
- RBAC
- OSWAP
- General best practices as applied to Software Engineering

### Test
- XUnit, NUnit
- Grafana k6 (load test)
- Playwright

### Cloud

- Azure Certified [verify](https://learn.microsoft.com/en-us/users/keithalanrowe/credentials/a314102f78ba1346?ref=https%3A%2F%2Fwww.linkedin.com%2F)
- Containers
- Storage
- Compute
- Security
- Cost Analysis
- Governance
- Compliance
- PaaS, Serverless
- Kubernetes
- Azure Container Apps
- Function Apps, Logic Apps
- Observability, Application Insights, Log Application Workspaces, OpenTelemetry
- Resiliency

### Data
- Familiar with ETL, Snowflake, Azure Data Factory (ADF), Databricks
- Python (non-professional)

### Database - Relational, Document

- Microsoft SQL Server
- Datawarehouse, Data Lake
- PostgreSQL
- Mongo/Cosmos
- Oracle / API integrations
- TSQL, stored procedures, indexes, maintenance tasks
- Performance tuning

### Scripting

- Powershell
- Bash / zSh
- winget / Chocolatey

### Mobile 
- Ionic / Capacitor 
- React Native
- Expo 

### Platforms

- Azure DevOps
- Github
- Supabase
- Atlassian - Jira, Confluence
- Azure Communication Services, Twillo / Sendgrid
- Figma
- SMTP, Sendgrid, Twillo, Azure Communication Services

### Payment Gateways - API

- Authorize.Net
- Stripe
- PayPal

### Content Management Systems / Integrations

- Shopify
- BigCommerce
- nopCommerce
- Wordpress
- Drupal
- Static file

### Pipelines

- Azure DevOps - yaml, classic
- ARM/Bicep
- azd
- Terraform (experimental only)
- Github Actions
- Jenkins
- DevSecOps, GitHub Advanced Security, Coverity Black Duck

### Infrastructure
- Firewalls
- Azure FrontDoor, WAF
- Networking, subnets, vnets
- VPN
- DNS
- Virtual machines, setup, configure
- Routing

### Public Hosting
- Domain name registration
- Nameserver configuration

### Business Operating Systems

- EOS Entrepreneurial Operating System


<!---
keitharowe/keitharowe is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
