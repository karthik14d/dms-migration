# Database Migration PoC: EC2 PostgreSQL to AWS RDS PostgreSQL via AWS DMS

This project demonstrates a real-world proof-of-concept (PoC) for database modernization and cloud migration using AWS Database Migration Service (DMS). It covers:

- Deploying PostgreSQL 15 on an EC2 instance (simulating an on-premises source)
- Configuring PostgreSQL for secure external access
- Creating relational database schema (customers, products, orders)
- Setting up AWS RDS PostgreSQL instance (Free Tier)
- Establishing secure endpoints and replication instance via AWS DMS
- Performing a full load migration using AWS DMS
- Troubleshooting and validating data integrity post-migration
- Following best practices for security, connectivity, and cloud migration

---

## Project Structure

aws-dms-ec2-to-rds-migration/
├── README.md
├── migration_steps/
│   ├── ec2_postgresql_setup.md
│   ├── postgresql_configuration.md
│   ├── dms_endpoints_setup.md
│   ├── dms_migration_task.md
│   ├── troubleshooting_encountered.md
│   ├── final_validation_steps.md
├── screenshots/
│   ├── ec2_instance_details.png
│   ├── postgres_conf_edits.png
│   ├── dms_endpoint_test_success.png
│   ├── dms_task_running.png
│   ├── dms_task_load_complete.png
│   ├── target_rds_validation.png
├── cheat_sheets/
│   ├── aws_dms_commands_cheat_sheet.md
│   ├── dms_troubleshooting_checklist.md

## Tools and Services Used
PostgreSQL 15 (running on Amazon Linux 2023 EC2 instance)

AWS RDS PostgreSQL 15 (Free Tier, db.t3.micro)

AWS Database Migration Service (DMS)

AWS Management Console

CloudWatch for DMS monitoring and troubleshooting

GitHub for version control and project documentation

Bash terminal for CLI commands (psql, pg_dump, PostgreSQL service management)

## Migration Overview
Provisioned an EC2 instance with PostgreSQL 15 installed

Configured PostgreSQL server (postgresql.conf, pg_hba.conf) for external DMS access

Created a sample database (sampledb) and loaded relational tables:

customers

products

orders

Created RDS PostgreSQL instance as the target database

Set up AWS DMS Replication Instance and Source/Target Endpoints

Migrated existing data using AWS DMS (Full Load migration)

Solved connection, permission, and SSL challenges

Completed migration successfully and validated data in RDS

## Validation Steps
Connected to AWS RDS PostgreSQL target database using psql.

Verified presence of all migrated tables (customers, products, orders).

Queried row counts and sample data to ensure complete migration success.

DMS task validation completed with zero errors in Table Statistics.

## Key Learnings and Outcomes
Hands-on exposure to PostgreSQL server installation, configuration, and remote access.

Practical experience with AWS DMS, replication instances, and migration tasks.

Importance of SSL and user permission configurations for smooth migration.

Cloud-first operational practices: monitoring via DMS Table Statistics and CloudWatch Logs.

Real-world troubleshooting: permissions grants, table structure matching, endpoint configuration.

Understanding migration types (Full Load, CDC) and best practices for safe cloud migrations.

## Author
Karthik Dharmaraju
Cloud Enthusiast | Senior Database SME | AWS Certified Solutions Architect – Associate

## Related Files in This Project
migration_steps/ec2_postgresql_setup.md → EC2 PostgreSQL server setup steps

migration_steps/postgresql_configuration.md → External access configuration for PostgreSQL

migration_steps/dms_endpoints_setup.md → AWS DMS endpoints creation guide

migration_steps/dms_migration_task.md → DMS Migration Task creation and execution

migration_steps/troubleshooting_encountered.md → Troubleshooting real-world DMS errors

migration_steps/final_validation_steps.md → Data validation queries and methods

cheat_sheets/aws_dms_commands_cheat_sheet.md → Important PostgreSQL + DMS commands

cheat_sheets/dms_troubleshooting_checklist.md → Quick troubleshooting guide for DMS migrations
