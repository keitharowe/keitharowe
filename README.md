- [Introduction](#Introduction)
- [Recent Accomplishments](#Recent-Accomplishments)
- [Project Showcases](#Project-Showcases)
- [Tech Profile - skills, languages, platforms, etc.](#Tech-Profile)

# Introduction
- Technology Executive
- Cloud Architect
- Operational Team Lead with deep hands on experience
- AI-assisted development and tooling to amplify developer productivity based on software craftsmanship and design patterns
- Ability to navigate complex situations with minimum information to provide clarity, direction and an actionable path forward

I enjoy helping companies and teams build software through improving team processes, delivering business value utilizing my 20 year experience in software design principles.

# Recent Accomplishments

- Led an enterprise data platform modernization for a national staffing firm. Migrated integration and orchestration off a seat-licensed third-party platform onto Azure Data Factory, designed and built a governed Snowflake enterprise data warehouse using a medallion architecture with streams, tasks, and slowly changing dimension history, and automated the employee identity lifecycle so onboarding, role changes, and offboarding stay consistent across the corporate directory, HR, and commissions systems.
- Developed and delivered a security remediation program for the same platform, closing findings that ranged from secrets committed to source and unauthenticated access to employee data, to public internet exposure of on-prem APIs. Re-architected on-prem data access behind a Self-Hosted Integration Runtime and private endpoints so internal systems are no longer reachable from the public internet.
- Established the supporting engineering platform: trunk-based CI/CD with automatic development deploys and approval-gated production, Azure Monitor and Log Analytics observability with alerting into Microsoft Teams, a private developer portal that publishes API specifications from the build, and a branded email domain on Azure Communication Services.
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

## Enterprise Data Platform Modernization and Cloud Migration for a National Staffing Firm

### Background
The client is a national staffing and workforce solutions company that places thousands of temporary, contract, and direct hire employees across the United States. Their employee data moves through a chain of systems: an on-prem AS/400, several internal HR and metadata applications, Active Directory, a Snowflake data warehouse, and downstream systems for sales commissions and payroll. Historically these systems were stitched together by a third-party integration platform (iPaaS) and a collection of scripts that had grown difficult to reason about and expensive to license. Bennett Adelson was engaged to define the target architecture, move orchestration onto Azure, close a backlog of security findings, and build a governed enterprise data warehouse the business could trust for reporting and commissions.

### Challenges / Pain Points
Integration ran on a seat-licensed third-party platform with limited visibility into what ran, what failed, and why. Several on-prem APIs were reachable from the public internet and protected only by a static API key, and some secrets and keys had been committed to source control. Read access to employee data was not consistently authenticated. The warehouse had grown without clear governance, so transformations were ad hoc, data ownership was unclear, and quality problems could fail silently. One such failure, an oversized value quietly breaking a nightly load, went unnoticed for roughly seven weeks. Employee onboarding and offboarding leaned on manual steps, the nightly directory sync required a person to review and release it every day, and returning employees were sometimes confused with their old terminated records. There was no standard for CI/CD, environments, or observability.

### Goals
- Make Azure Data Factory the single orchestration standard, replacing the third-party iPaaS and the loose scripts around it.
- Design and build a governed Snowflake enterprise data warehouse that reporting and commissions could depend on.
- Remove public exposure of on-prem systems and adopt security by default: managed identities, Key Vault, and private networking.
- Automate the employee identity lifecycle so onboarding, changes, and offboarding stay consistent across systems without daily manual work.
- Stand up trunk-based CI/CD, monitoring, and alerting so problems surface loudly instead of silently.

### Solution and Approach

**Data and Integration Architecture.** We designed the data flow as a single directional loop rather than a web of point to point connections. Source systems land data in Snowflake, Azure Data Factory compares and orchestrates, custom .NET APIs carry out the writes back to operational systems such as Active Directory, and the results are captured back in Snowflake. A Self-Hosted Integration Runtime became the standard way to reach on-prem systems, which let us retire the public API exposure instead of guarding it. Moving orchestration onto Azure Data Factory also changed the cost model from paid seats to per-run execution and gave us built-in run history and monitoring the previous platform lacked.

**Enterprise Data Warehouse (Snowflake).** This was the center of the engagement. We organized the warehouse into a medallion architecture, a layered model that promotes data through raw, staging, silver, and gold tiers so each step is auditable and can be rebuilt from the one before it. Incremental movement between layers runs on Snowflake streams and tasks, which capture changes and merge them forward without full reloads. The core employee dimension tracks history using slowly changing dimensions (Type 2), so the warehouse can answer not just what an employee looks like today but what they looked like at any point in time. We also made data ownership explicit by naming a single writer of record for each field, which ended a class of silent conflicts that no amount of after the fact reconciliation had been able to fix. The result is a governed warehouse with clean lineage feeding sales commissions and business reporting.

**Azure and DevOps.** The platform follows Azure landing zone practices with a naming and tagging convention, so a resource name alone tells you what it is and which environment it belongs to. Deployments use a trunk-based model: a single main branch deploys to a development environment automatically and to production behind an approval gate. Data Factory, including its global parameters, deploys through ARM and PowerShell. A private developer portal publishes API documentation automatically from the build. Function Apps handle event and transformation work, a branded email domain sends operational notifications through Azure Communication Services, and an observability stack routes Data Factory diagnostics into Log Analytics with Azure Monitor alerts delivered to Microsoft Teams.

**Security.** Security work was tracked openly as a numbered set of findings with severity and remediation status. Among the items closed: an Azure AD client secret that had been hardcoded in source was migrated to managed identity and certificate based authentication; an API key committed to source was removed and rotated; API key comparison was moved to a constant time implementation to remove a timing side channel; unauthenticated read access to employee data was closed; and a search endpoint vulnerable to wildcard abuse was escaped. The larger architectural fix was removing public internet exposure of on-prem APIs by routing all on-prem access through the Self-Hosted Integration Runtime and private endpoints, which shrinks the attack surface to internal callers only.

**Identity Lifecycle and Offboarding.** When someone is hired, changes roles, or leaves, their record has to stay in step across the corporate directory, the internal HR systems, and the commissions platform. For a long time that reconciliation depended on a person reviewing and releasing a nightly job by hand. We replaced it with a job that runs on its own overnight and only stops to ask for a human when a batch looks abnormal, so a bad batch cannot go out unnoticed. Along the way we found and fixed a few problems that had been quietly causing trouble. Returning employees were sometimes matched to their old terminated records, which threw off commissions and stalled the sync; we traced that to a stale background copy of employee data that had silently stopped updating, rebuilt it, and that one fix cleared the blockage and also healed a related gap where new hires were not showing up for commissions. We sorted out which system is allowed to write which field so two pipelines could not overwrite each other, and made sure new accounts carry the identifier the commissions system needs in order to see them.

Technology Stack: Azure Data Factory, Snowflake (streams, tasks, medallion architecture, slowly changing dimensions), Self-Hosted Integration Runtime, .NET and C# APIs, Azure Functions, Managed Identity, Azure Key Vault, Private Endpoints and Private DNS, Azure Communication Services, Log Analytics, Azure Monitor, Application Insights, Azure DevOps (trunk-based CI/CD, ARM, Bicep, PowerShell), and Active Directory. The work migrated integration off SnapLogic and connects operational systems including CaptivateIQ, PayCor, NetSuite, and JobDiva.

### Key Takeaways / Lessons Learned
Moving orchestration onto a managed platform with security by default lowered cost, improved visibility, and closed an entire category of public exposure at the same time. The most durable data fix was not a cleverer reconciliation but simply deciding who owns each field, a single writer of record, and enforcing it. The failures worth fearing are the silent ones: a single oversized value froze a nightly load for seven weeks before anyone noticed, which is the strongest argument for loud alerting and fail fast guardrails. A warehouse organized into clear layers with change driven promotion and real history is far easier to trust, extend, and reason about than a pile of ad hoc transformations.

#### Skills
Snowflake · Data Warehouse Architecture · Medallion Architecture · Enterprise Data Architecture · ELT / ETL · Slowly Changing Dimensions (SCD Type 2) · Streams and Tasks · Azure Data Factory · Self-Hosted Integration Runtime · Azure Landing Zones · Managed Identity · Azure Key Vault · Private Endpoints · Security Remediation · DevSecOps · Trunk-Based Development · CI/CD · Observability · Active Directory · Identity Lifecycle Automation · Technology Leadership · C# · .NET

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

## Strategic Technology Direction, Roadmap, Application Modernization for a National Youth Baseball Organization

The client is a national organization dedicated to the development and promotion of youth baseball.
They host travel team tournaments and individual showcases, to promote and provide valuable
exposure for young athletes and to gain exposure to college coaches and MLB scouts.

Prior to Bennett Adelson's involvement, the client lacked effective internal software development,
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

The client over the years has put an enormous effort into the software that runs their business without a long-term vision. Bennett Adelson worked with the client to define the future tech stack and direction. This engagement included designing and implementing a scalable enterprise data warehouse to support core business intelligence and reporting, along with preparation for AI search and advanced analytics workloads using Azure Data Factory (ADF) to orchestrate data ingestion, transformation, and embedding pipelines that support vector database capabilities for semantic search and machine learning applications.

#### Skills

Technology Roadmapping · Microsoft Azure · Technology Leadership · Agile Methodologies · C# · .NET Core · Application Modernization · Application Programming Interfaces (API) · NextJS · Strangler Fig · Domain Driven Design · Azure Data Factory · Data Lake · Vector embeddings · Data warehouse architecture 

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
- ChatGPT
- Agentic workflows

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

- Azure Enterprise Architecture / Azure Landing Zones
- Domain Driven Design
- Minimum Apis
- GraphQL
- CI/CD pipelines (DevSecOps)
- API / Microservices
- Events/Messaging
- Mobile development
- Azure Aspire
- git, branching strategies
- Event Storming
- CQRS
- Mediator

### Security
- OAuth
- OpenID Connect (OIDC)
- Entra ID, MSAL
- RBAC
- OWASP
- Managed Identity and workload identity
- Azure Key Vault, secrets management and rotation
- Private endpoints and network isolation
- Security issue tracking and remediation
- PII protection and data access controls
- General best practices as applied to Software Engineering

### Test
- XUnit, NUnit
- Grafana k6 (load test)
- Playwright

### Cloud

- Azure Certified [verify](https://learn.microsoft.com/en-us/users/keithalanrowe/credentials/a314102f78ba1346?ref=https%3A%2F%2Fwww.linkedin.com%2F)
- Storage
- Compute
- Security
- Cost Analysis
- Governance
- Compliance
- PaaS, Serverless
- Private Link and Private Endpoints
- Self-Hosted Integration Runtime (SHIR)
- Function Apps, Logic Apps
- Observability, Application Insights, Log Analytics Workspaces, OpenTelemetry
- Resiliency

### Containers and Virtualization

- Docker, containerization
- Kubernetes, Azure Kubernetes Service (AKS)
- Azure Container Apps
- Azure Container Instances
- Azure Container Registry
- Container orchestration and image build pipelines

### Data Engineering and Warehousing
- Snowflake (Streams, Tasks, medallion architecture, RBAC)
- Azure Data Factory (pipelines, triggers, global parameters, Self-Hosted Integration Runtime)
- Medallion and multi-hop architecture (raw, staging, silver, gold)
- ELT and ETL
- Dimensional modeling, star schema, Slowly Changing Dimensions (Type 2)
- Change data capture and incremental loads
- Data lineage, governance, and writer-of-record ownership modeling
- Data quality and reconciliation
- Databricks
- Python (non-professional)

### Database - Relational, Document

- Microsoft SQL Server
- Data Warehouse, Data Lake
- PostgreSQL
- Mongo/Cosmos
- Oracle / API integrations
- TSQL, stored procedures, indexes, maintenance tasks
- Performance tuning

### Logging / Logging Platforms
- Azure Application Insights / Azure Monitor
- Sentry

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
- Azure Communication Services, Twilio / Sendgrid
- Figma
- SMTP, Sendgrid, Twilio, Azure Communication Services

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
