# PROPOSAL: {{cookiecutter.project_name}}

## Overview

The process is simple: first we define the problem, and based on that we propose one or more possible solutions.

## Problem Statement

What problem do we want to solve?

### Requirements

#### Functional Requirements

- FR001:
- FR002:

#### Technical Requirements

- TR001:
- TR002:

#### Out of Scope

- OOS001:
- OOS002:

### Business Process

```mermaid
sequenceDiagram
	actor ActorA
	participant Salesforce

	ActorA ->> Salesforce: Create Account
```

## Proposed Solution

### Workflow

```mermaid
graph LR;
	SourceDB[("source-database")];
	dbt["dbt"];
	Snowflake[("Snowflake")];

	SourceDB --> dbt --> Snowflake;
	raw --> clean --> augmented;
```

### Architecture

We use the [C4 model](https://c4model.com/) to define the architecture, and mermaid charts as the technology of choice to easily define this using markdown.

#### Level 1 - System Context Diagram

```mermaid
C4Context
	title System Context diagram for Demo Data Platform

	Person(personUser, "User", "A user of the Dream Data Platform, e.g. Data Engineer or Business Analyst")

    System_Boundary(sbCI, "Demo Data Platform") {
		System(SystemOrchestrator, "Orchestrator App", "Manages Pipelines")
		System(SystemDataCatalog, "Data Catalog App", "Stuff about data")

	}

    Rel(personUser, SystemOrchestrator, "Uses")
    Rel(personUser, SystemDataCatalog, "Uses")

```

#### Level 2 - Container Diagram

```mermaid
C4Container
title Container diagram for Demo Data Platform

Person(personUser, "User", "A user of the Dream Data Platform, e.g. Data Engineer or Business Analyst")

Container_Boundary(c1, "Orchestrator") {
	Container(ContainerOrchestrator, "Orchestrator App", "kestra.io", "Provides orchestration functionality to users via their web browser")
	Container(ContainerDataQuality, "Data Quality App", "Great Expectations", "Tests Data Quality")
	Container(ContainerDataCatalog, "Data Catalog App", "Great Expectations", "Tests Data Quality")
	ContainerDb(database, "Database", "DuckDB", "Stores X data")
}

Rel(personUser, ContainerOrchestrator, "Uses")

```

#### Level 3 - Component Diagram

```mermaid
C4Component
title Component diagram for Internet Banking System - API Application

Container(spa, "Single Page Application", "javascript and angular", "Provides all the internet banking functionality to customers via their web browser.")
Container(ma, "Mobile App", "Xamarin", "Provides a limited subset ot the internet banking functionality to customers via their mobile mobile device.")
ContainerDb(db, "Database", "Relational Database Schema", "Stores user registration information, hashed authentication credentials, access logs, etc.")
System_Ext(mbs, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

Container_Boundary(api, "API Application") {
	Component(sign, "Sign In Controller", "MVC Rest Controller", "Allows users to sign in to the internet banking system")
	Component(accounts, "Accounts Summary Controller", "MVC Rest Controller", "Provides customers with a summary of their bank accounts")
	Component(security, "Security Component", "Spring Bean", "Provides functionality related to singing in, changing passwords, etc.")
	Component(mbsfacade, "Mainframe Banking System Facade", "Spring Bean", "A facade onto the mainframe banking system.")

	Rel(sign, security, "Uses")
	Rel(accounts, mbsfacade, "Uses")
	Rel(security, db, "Read & write to", "JDBC")
	Rel(mbsfacade, mbs, "Uses", "XML/HTTPS")
}

Rel_Back(spa, sign, "Uses", "JSON/HTTPS")
Rel(spa, accounts, "Uses", "JSON/HTTPS")

Rel(ma, sign, "Uses", "JSON/HTTPS")
Rel(ma, accounts, "Uses", "JSON/HTTPS")

UpdateRelStyle(spa, sign, $offsetY="-40")
UpdateRelStyle(spa, accounts, $offsetX="40", $offsetY="40")

UpdateRelStyle(ma, sign, $offsetX="-90", $offsetY="40")
UpdateRelStyle(ma, accounts, $offsetY="-40")

	UpdateRelStyle(sign, security, $offsetX="-160", $offsetY="10")
	UpdateRelStyle(accounts, mbsfacade, $offsetX="140", $offsetY="10")
	UpdateRelStyle(security, db, $offsetY="-40")
	UpdateRelStyle(mbsfacade, mbs, $offsetY="-40")
```

#### Level 4 - Dynamic Diagram

![something like this](https://github.com/nikeshnaik/streaming_cricket_analysis/blob/main/high_level_data_architecture.png)

#### Level 5 - Deployment Diagram

### Deliverables

### Roadmap

