# Kare

Kare is a cloud-based asset registry for managing equipment, technical data, documents, and maintenance-related information in one place.

It replaces scattered Excel files with a structured internal database that is searchable, reportable, and available for integrations with maintenance and business intelligence systems.

Kare is designed for properties and organizations that manage large amounts of technical equipment, such as shopping centres, commercial properties, industrial sites, and property service companies.

## Why Kare Exists

Technical equipment data is often spread across:

* Excel files
* SharePoint folders
* maintenance systems
* equipment documentation
* individual employees and service providers

This makes it difficult to know what equipment exists, where it is located, and whether the available information is current.

Kare provides a central source of truth for equipment data.

## Core Features

* Structured equipment and asset records
* Data loading via Excel import
* Configurable asset types and properties
* Locations and property hierarchy
* Fast search and filtering
* Comments, documents, and attachments
* Microsoft Entra ID authentication
* Integration with external systems

## Architecture Overview

```text
Users and Service Providers
             │
             │ Microsoft Entra ID
             ▼
        Kare Web UI
   (ASP.NET Core on Azure)
             │
             ▼
        Kare Database
          (Azure SQL)
             │
       ┌─────┴─────┐
       ▼           ▼
 Reporting     Integrations
 Power BI      Azure Functions
                   │
                   ▼
          External Systems
     Falcony | REST APIs | Files
```

## Data Model

Kare stores equipment as structured records.

Each asset can include:

* asset identifier
* asset type
* location
* manufacturer and model
* serial number
* installation date
* technical properties
* comments and attachments
* external system identifiers

Asset types can have their own configurable properties, allowing the same system to manage different kinds of equipment without requiring a separate application for each register.

## Integrations

Kare can exchange data with external systems through scheduled jobs, APIs, and webhook-based integrations.

For example, Kare can act as the master data source for equipment and keep asset details in sync with a third-party maintenance ticketing system, ensuring that up-to-date equipment information is available directly on service requests.

The structured database can also be used directly as a source for Power BI reporting.

## Deployment Model

Kare is deployed into the customer’s own Azure environment.

This gives the customer control over:

* data ownership
* user access
* infrastructure
* backups
* integrations
* operating costs

Authentication is handled through the customer’s Microsoft Entra ID environment.

## Project Status

Kare is in production use and under active development.

The first production deployment is used to manage technical asset data and integrate it with an external maintenance ticketing system.
