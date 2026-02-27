# ADF
Azure Data Factory project showcasing reusable ingestion, orchestration, routing, and transformation pipelines built for common enterprise ETL and analytics workflows.

## Project Overview

This repository contains Azure Data Factory (ADF) assets that demonstrate how to build scalable, parameter-driven data pipelines for ingesting data from APIs, databases, and cloud storage into curated analytical layers.
The project focuses on practical ETL/ELT design patterns such as:
- REST API ingestion with dynamic pagination
- Incremental data loading with last-load tracking
- Parent-child pipeline orchestration
- Event-driven file ingestion
- Metadata-driven schema mapping
- Data transformation into Delta format using Mapping Data Flows

These pipelines are designed to highlight both technical ADF implementation skills and real-world business use cases relevant to modern data engineering workflows.


## Pipeline Use Cases
### API pipeline
<img width="2316" height="1266" alt="image" src="https://github.com/user-attachments/assets/c9b45b33-159a-455a-92b7-f70c4075f0f2" />
**Purpose:** Ingest data from paginated REST APIs into a target destination.

**What it does:**
- Uses a Web activity to fetch the total available record count
- Dynamically calculates offset ranges
- Loads paginated data through Copy Data activity

**Typical business use cases:**
- Pulling customer, sales, marketing, or operational data from SaaS platforms
- Ingesting API-based source data into a data lake for reporting
- Automating periodic extraction from external systems without manual intervention


### Ingestion pipeline
<img width="2308" height="1288" alt="image" src="https://github.com/user-attachments/assets/694c8746-062b-4af2-8dcb-025f0c82ef71" />
**Purpose:** Perform parameterized and incremental data loads from source tables.

**What it does:**
- Accepts schema, table, and manual-load parameters
- Runs a dynamic query to identify records updated since the last load
- Conditionally loads new or changed records
- Updates the last-load timestamp after successful completion

**Typical business use cases:**
- Loading ERP, CRM, or transactional tables into a reporting layer
- Reducing full-refresh costs by only processing changed data
- Supporting production ETL pipelines for ongoing operational reporting


### Schedule pipeline
<img width="2224" height="1286" alt="image" src="https://github.com/user-attachments/assets/3cc1be0a-f9ec-4340-921d-fb67745ac760" />
**Purpose:** Trigger other pipelines in a reusable parent-child orchestration pattern.

**What it does:**
- Accepts another pipeline as an input
- Executes the target pipeline through orchestration logic
- Can be linked to time-based triggers for automated scheduling

**Typical business use cases:**
- Scheduling daily, hourly, or weekly data refreshes
- Standardizing the execution pattern for multiple pipelines
- Centralizing operational control for batch data workflows

### Router pipeline
<img width="2304" height="950" alt="image" src="https://github.com/user-attachments/assets/328b5609-f1c5-46bb-a03b-3a70e5288cd5" />
**Purpose:** Route uploaded files from a landing container to destination zones based on file type or logic.

**What it does:**
- Starts when new files are uploaded
- Uses Get Metadata to identify incoming files
- Iterates through files using ForEach
- Uses Switch logic to route each file to the correct destination
- Deletes processed files from the source container at the end

**Typical business use cases:**
- Landing zone to raw/curated zone file routing
- Automating ingestion for multi-format inbound files
- Handling batch uploads from vendors, applications, or external partners


### Schema pipeline
<img width="2246" height="1252" alt="image" src="https://github.com/user-attachments/assets/66e91a99-232a-43a5-8c7d-54ead8a9efa8" />
**Purpose:** Load files dynamically using schema mapping passed as parameters.

**What it does:**
- Accepts table/schema mapping as input
- Retrieves file names from the source location
- Iterates through each file
- Applies dynamic mapping based on file name and input metadata
- Copies data into the correct destination structure

**Typical business use cases:**
- Processing multiple source files with different schemas
- Building scalable ingestion frameworks for recurring batch feeds
- Standardizing ingestion for semi-structured or structured file drops

### Delta Flow 
<img width="2380" height="1172" alt="image" src="https://github.com/user-attachments/assets/21a357df-0264-4bb3-9f06-3213f2c54a3b" />
**Purpose:** Transform source data and store it as Delta-formatted output.

**What it does:**
- Runs a Mapping Data Flow
- Reads source data
- Applies transformations needed for standardized output
- Writes transformed data into the destination as Delta tables

**Typical business use cases:**
- Converting raw files into analytics-ready curated datasets
- Standardizing transformation before consumption in dashboards
- Building scalable transformation layers on cloud storage





**Summary**
This Azure Data Factory project demonstrates end-to-end data pipeline development using reusable orchestration, ingestion, routing, and transformation patterns. It showcases practical ADF skills across API ingestion, incremental loads, event-driven file handling, metadata-driven processing, and Delta-based transformation—making it a strong portfolio project for data engineering and cloud ETL use cases.
