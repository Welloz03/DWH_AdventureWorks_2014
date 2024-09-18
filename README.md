# AdventureWorks Data Warehouse

A comprehensive data warehouse built using Microsoft SQL Server and SSIS for the AdventureWorks OLTP database.

---

## Introduction

### What is a Data Warehouse?

> A data warehouse is a system used for reporting and data analysis and is considered a core component of Business Intelligence.

**BI Relationship with Data Warehouses**

Data Warehouses play a crucial role in enabling effective Business Intelligence. They serve as the central repository for structured, historical data collected from various operational systems within an organization.

* Data Consolidation & Organization: Data warehouses consolidate data from disparate sources, cleaning and transforming it into a consistent format. This allows BI tools to easily access and analyze the information.
* Historical Context: Data warehouses store historical data, enabling BI users to track trends, compare performance over time, and gain insights into long-term patterns.
* Performance Optimization: Data warehouses are designed for analytical queries, providing optimized performance for complex BI analysis.
* Data Accessibility: Data warehouses provide a single, unified source of truth, ensuring everyone within the organization is working with the same consistent data.

### Why We Need a Data Warehouse

* Centralized Data: Eliminates silos, provides a single source of truth
* Historical Context: Enables trend analysis & forecasting
* BI Optimized: Structured for complex queries & insights
* Performance & Scalability: Handles large analytical workloads
* Advanced Analytics: Supports data mining & predictive modeling
* Cost-Effective: Streamlines data management
* Data Governance: Enhances security & compliance

---

## Overview of the BI Solution Architecture

The following diagram illustrates the overall architecture of the Business Intelligence solution, showcasing the flow of data from various sources to the final presentation layer:

![Image Alt Text](https://github.com/Welloz03/DWH_AdventureWorks_2014/blob/e130f9b5aca0ca5283d9ee569b844569ad3041ad/Images/Solution.png)

---

## Star Schema Modeling
![Image Alt Text](https://github.com/Welloz03/DWH_AdventureWorks_2014/blob/e130f9b5aca0ca5283d9ee569b844569ad3041ad/Images/Satr%20Schema.png)


---

## Data Warehouse Terminologies

* ### ETL vs ELT
    * ETL (Extract, Transform, Load): Traditional approach where data is extracted from sources, transformed in a staging area, and then loaded into the data warehouse
    * ELT (Extract, Load, Transform): Modern approach leveraging the power of the data warehouse to perform transformations after loading the raw data

* ### Staging vs ODS
    * Staging Area: Temporary storage for data during the ETL/ELT process, used for cleansing, validation, and transformation
    * ODS (Operational Data Store): Integrated data repository serving near-real-time reporting and operational needs, often a source for the data warehouse

* ### OLTP vs OLAP
    * OLTP (Online Transaction Processing): Systems designed for day-to-day business transactions, focused on data integrity and speed
    * OLAP (Online Analytical Processing): Systems optimized for complex queries and analysis, often utilizing multidimensional data structures

* ### Fact Tables vs Dimension Tables
    * Fact Tables: Store the measurements or metrics of the business process, typically containing numeric values and foreign keys to dimension tables
    * Dimension Tables: Provide context to the facts, describing the "who, what, where, when, and how" of the business events

* ### Star Schema vs Snowflake
    * Star Schema: Simple dimensional model with a central fact table connected to multiple dimension tables, ideal for performance and ease of use
    * Snowflake Schema: Extension of the star schema where some dimension tables are further normalized, offering flexibility but potentially impacting query performance

---

## Company Overview

* Multinational manufacturing company
* Territory
    * 3 Group 6 Region 10 Territory
* Product
    * 4 Category 30+ Sub Category 500+ Products
* Customers
    * 15k+
* Department
    * Purchase and Production
    * Human Resource
    * Sales
---

## How to Design a Data Warehouse

Designing a data warehouse is a multi-faceted process that involves careful planning and execution. Here's a breakdown of the key phases:

## 1. Business Analysis

This phase focuses on understanding the business needs and requirements that will drive the data warehouse design.

* **Business Objectives:** 
    * **Key questions to answer:**  Clearly define the business questions the data warehouse needs to help answer. This will guide the data modeling and ensure the warehouse delivers actionable insights.
    * **Processes/areas to benefit:** Identify the specific business processes or areas that will leverage the data warehouse for decision-making and analysis.
    * **Reporting needs:** Determine the types of reports and dashboards that users will need, including the required metrics, dimensions, and levels of detail.

* **Data Requirements:**
    * **Data types needed:**  Identify the specific data elements (e.g., sales data, customer information, product details) necessary to support the business objectives. 
    * **Granularity level:**  Determine the level of detail at which data should be stored (e.g., daily, weekly, transaction-level). This impacts storage requirements and query performance.
    * **Metrics & dimensions:** Define the key performance indicators (KPIs) and the dimensions (e.g., time, product, customer) that will be used for analysis.

* **Data Governance:** 
    * **Ownership & responsibilities:** Establish clear ownership and responsibilities for managing and maintaining the data warehouse, ensuring data quality and consistency.
    * **Quality standards:**  Define data quality rules and processes to ensure the accuracy, completeness, and timeliness of the data in the warehouse.
    * **Privacy & security:** Implement measures to protect sensitive data and comply with relevant privacy and security regulations.

## 2. Technical Analysis

This phase involves evaluating the technical aspects of the data warehouse implementation.

* **Technology Stack:**
    * **Data warehouse platform:**  Choose the appropriate data warehouse platform (e.g., Microsoft SQL Server, Azure Synapse Analytics, Snowflake) based on requirements and budget.
    * **ETL/ELT tools:** Select the tools for extracting, transforming, and loading data into the warehouse. Consider factors like performance, ease of use, and integration capabilities.
    * **BI & reporting tools:** Choose the tools for visualizing and analyzing the data in the warehouse (e.g., Power BI, Tableau, QlikView).

* **Hardware & Infrastructure:**
    * **Storage & processing power:**  Estimate the storage and processing requirements based on data volume, growth projections, and query complexity.
    * **Scalability:** Design the infrastructure to accommodate future growth and increasing data volumes.

* **Data Modeling:**
    * **Modeling approach:** Decide on the data modeling approach (e.g., dimensional modeling, data vault) that best suits the business requirements and analytical needs.
    * **Dimensional design:** Design the dimension and fact tables, ensuring proper normalization and relationships.
    * **Data types & indexes:** Choose appropriate data types and create indexes to optimize query performance.

## 3. Source System Analysis

This phase involves understanding the source systems from which data will be extracted.

* **Identify Sources:**
    * **Inventory of relevant systems:**  Compile a list of all the source systems that contain data relevant to the data warehouse. 
    * **Data structures & formats:**  Understand the data structures, formats, and relationships within each source system.

* **Data Extraction & Integration:**
    * **Extraction feasibility:**  Assess the feasibility of extracting data from each source system, considering technical constraints and data access limitations.
    * **Extraction methods:**  Determine the most appropriate extraction methods (e.g., database replication, API calls, file transfers) for each source system.
    * **Data cleansing & transformation:**  Plan for data cleansing and transformation activities to ensure data quality and consistency before loading into the warehouse.

* **Data Quality:**
    * **Quality analysis:**  Perform data profiling and analysis to identify data quality issues in the source systems. 
    * **Potential issues:**  Document potential data quality problems, such as missing values, inconsistencies, and duplicates.
    * **Addressing strategies:**  Develop strategies to address data quality issues, including data cleansing, validation, and enrichment techniques.
---

## Data Warehouse Implementation

1. Creating Database Objects: Design and create the necessary database objects in SQL Server, including tables, views, stored procedures, and functions.
2. ETL Source to Staging: Extract data from various source systems and load it into the staging area using SSIS packages. Perform initial data cleansing and validation in the staging area.
3. ETL Staging to DWH: Transform and load data from the staging area into the data warehouse, ensuring data integrity and applying business rules.
4. Creating SSAS Tabular: Develop a Tabular model in SSAS to provide a semantic layer for business users, enabling them to create reports and perform analysis easily.
5. Creating Power BI Reports: Design and develop interactive reports and dashboards in Power BI, connecting to the SSAS Tabular model or the data warehouse.

--- 

## ETL Process
![Image Alt Text](https://github.com/Welloz03/DWH_AdventureWorks_2014/blob/e130f9b5aca0ca5283d9ee569b844569ad3041ad/Images/Fisrt.png)
![Image Alt Text](https://github.com/Welloz03/DWH_AdventureWorks_2014/blob/e130f9b5aca0ca5283d9ee569b844569ad3041ad/Images/Second.png)
![Image Alt Text](https://github.com/Welloz03/DWH_AdventureWorks_2014/blob/e130f9b5aca0ca5283d9ee569b844569ad3041ad/Images/Third.png)
![Image Alt Text](https://github.com/Welloz03/DWH_AdventureWorks_2014/blob/e130f9b5aca0ca5283d9ee569b844569ad3041ad/Images/Fourth.png)
![Image Alt Text](https://github.com/Welloz03/DWH_AdventureWorks_2014/blob/e130f9b5aca0ca5283d9ee569b844569ad3041ad/Images/Fifth.png)
