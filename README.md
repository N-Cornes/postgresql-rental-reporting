# PostgreSQL Rental Reporting

A PostgreSQL reporting project that transforms transactional rental data into detailed and summarized reporting tables using SQL, stored functions, procedures, and database triggers.

## Tech Stack

- PostgreSQL
- SQL
- PL/pgSQL
- Relational database design
- Stored functions
- Stored procedures
- Database triggers

## Project Focus

The project builds an automated reporting layer on top of a rental database. Transactional records are transformed into reporting-friendly structures that support both detailed analysis and monthly summaries.

## Reporting Tables

### `detailed_rentals`

Stores detailed rental and payment information used as the source for reporting and aggregation.

### `summary_rentals`

Stores summarized rental information grouped by reporting month so higher-level trends can be reviewed without repeatedly processing the full transactional dataset.

## Custom Date Function

A PostgreSQL function named `get_rental_month(timestamp)` converts a rental timestamp into a standardized reporting month in `YYYY-MM` format.

```text
Rental Timestamp
      ↓
get_rental_month(...)
      ↓
YYYY-MM Reporting Month
```

This keeps month formatting consistent throughout the reporting process.

## Report Refresh Procedure

The `refresh_report_tables()` procedure rebuilds the reporting data from the underlying rental database.

The refresh process:

1. Clears existing report data
2. Rebuilds the detailed reporting table from source records
3. Recalculates the summarized monthly report
4. Leaves both report tables synchronized with the transactional data

## Trigger Automation

A database trigger is attached to payment inserts so reporting data can be refreshed automatically when new payment activity is recorded.

```text
New Payment Insert
       ↓
Database Trigger
       ↓
Report Refresh Logic
       ↓
Detailed Report Updated
       ↓
Monthly Summary Updated
```

## Database Concepts Demonstrated

- Multi-table SQL queries
- Relational joins
- Data transformation
- Aggregation and grouping
- Reporting-table design
- PL/pgSQL functions
- Stored procedures
- Trigger-driven automation
- Transactional data vs. reporting data separation
- Repeatable report refresh workflows

## Architecture

```text
Transactional Rental Database
            ↓
     SQL Transformation
            ↓
     detailed_rentals
            ↓
       Aggregation
            ↓
      summary_rentals
```

## Technical Highlights

This project demonstrates how database-side logic can automate reporting without requiring a separate application layer. PostgreSQL functions standardize transformed values, procedures manage repeatable refresh operations, and triggers keep reporting workflows connected to incoming transactional activity.

## Source Code

The original academic SQL implementation is maintained privately. Source access can be provided for professional review upon request.

## Author

**Nicholas Cornes**  
B.S. Software Engineering
