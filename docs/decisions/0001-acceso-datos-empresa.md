---
parent: Decisions
nav_order: 100
title: 0002-Data-Segregation-Pattern
status: Proposed
date: 2024-10-29
decision-makers: ["Senior Architect", "Software Engineer Lead", "Project Manager"]
consulted: ["Database Administrator", "Security Expert"]
informed: ["Development Team", "Product Owner"]
---

# Data Segregation Pattern for Customer and Order Data

## Context and Problem Statement

The company needs to migrate its architecture from a monolithic system to a microservices-based architecture. The application must store customer and order data in separate databases to ensure independent management of each data type, improve scalability, and comply with data security and protection standards.

## Decision Drivers

* **Requisito Funcional 01**: Customer and order information must be stored in independent databases.
* **Requisito Funcional 02**: Independent management of each type of information must be ensured.
* **Requisito de Seguridad**: The solution must enhance data security and reduce the risk of data leaks.
* **Requisito de Escalabilidad**: The architecture must facilitate system scalability, improving performance and capacity management.

## Considered Options

* **0002-1: Data Segregation Pattern**: Separate databases for customers and orders.
* **0002-2: Single Database with Separate Tables**: Single database with separate tables for customer and order data.
* **0002-3: Data Warehouse for Historical Data**: Use a data warehouse for historical storage, reducing the need for separate databases.

## Decision Outcome

Chosen option: **0002-1: Data Segregation Pattern**, because it meets the requirement to store customer and order data in separate databases, allowing for independent management of each data type, enhancing data security, and supporting compliance with data protection regulations.

### Consequences

* **Good**: Improves data security and reduces the risk of security breaches.
* **Good**: Facilitates compliance with data protection standards.
* **Good**: Supports scalability and performance improvements by managing each data service independently.
* **Bad**: Increases system complexity and requires additional resources for management and maintenance.
* **Bad**: May incur additional costs, including infrastructure, software, and personnel.
* **Bad**: Requires a data synchronization strategy between both databases.

## Confirmation

Compliance with this decision will be confirmed through design and code reviews, as well as database audits to ensure customer and order data are independently managed and access controls are in place for each database.

## Pros and Cons of the Options

### 0002-1: Data Segregation Pattern

* **Good**: Enhances data security by isolating customer and order data.
* **Good**: Facilitates compliance with data protection standards.
* **Good**: Allows targeted scalability and improves performance by managing data services independently.
* **Bad**: Adds architectural complexity and requires more resources for management.
* **Bad**: Involves additional costs for infrastructure, software, and personnel.
* **Bad**: Needs a robust data synchronization strategy between both databases.

### 0002-2: Single Database with Separate Tables

* **Good**: Lower infrastructure costs and complexity compared to separate databases.
* **Good**: Simplifies management and maintenance by using a single database.
* **Bad**: Reduces data security by storing sensitive customer and order data in the same database.
* **Bad**: Limits independent scalability of each data type.
* **Bad**: Makes compliance with data protection standards more challenging.

### 0002-3: Data Warehouse for Historical Data

* **Good**: Facilitates analysis of historical data without requiring separate operational databases.
* **Good**: Reduces production database load by offloading historical data queries.
* **Bad**: Does not meet the requirement for separate storage of customer and order data in real-time systems.
* **Bad**: Increases architectural complexity by adding a data warehouse component.
* **Bad**: Does not improve real-time data security.

## More Information

For further details on data synchronization strategies, security controls, and the chosen database systems, please refer to the [project documentation link].
