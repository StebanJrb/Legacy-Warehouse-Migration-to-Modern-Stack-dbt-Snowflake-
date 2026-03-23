# Legacy Warehouse Migration to Modern Stack (dbt + Snowflake)

## Overview
A realistic data warehouse modernization project. Migrates a legacy PostgreSQL warehouse with stored procedures and embedded business logic to a modern dbt + Snowflake (or DuckDB) architecture. Includes IaC with Terraform and full documentation of the legacy-to-modern mapping.

## Architecture
- **Legacy System**: PostgreSQL warehouse with 15+ stored procedures, materialized views, and triggers implementing business logic
- **Migration Mapping**: Documented 1:1 mapping from each stored procedure to dbt models
- **Target Stack**: dbt Core for transformations (staging → intermediate → marts), Snowflake or DuckDB as warehouse
- **Testing**: dbt tests (unique, not_null, accepted_values, relationships) plus custom data tests validating migration parity
- **Infrastructure**: Terraform modules for Snowflake/AWS resources
- **Orchestration**: Airflow DAG triggering dbt runs with model-level retries

## Tech Stack
- PostgreSQL 15 (legacy source)
- dbt Core (transformations)
- Snowflake or DuckDB (modern warehouse)
- Terraform (infrastructure as code)
- Apache Airflow 2.x
- Docker & Docker Compose
- GitHub Actions (CI/CD for dbt)

## What This Demonstrates
- Warehouse migration planning and execution
- dbt project structure (staging/intermediate/marts)
- Translating stored procedure logic to dbt models
- Migration validation and parity testing
- Infrastructure as Code with Terraform
- CI/CD for data transformations

## Status
🚧 In Development

## Project Structure
├── legacy/
│   ├── stored_procedures/
│   └── migration_mapping.md
├── dbt_project/
│   ├── models/
│   │   ├── staging/
│   │   ├── intermediate/
│   │   └── marts/
│   ├── tests/
│   └── macros/
├── terraform/
├── dags/
│   └── dbt_run_dag.py
├── docker-compose.yml
└── README.md
