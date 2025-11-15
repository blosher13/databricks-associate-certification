# Databricks Certification

## Data Ingestion

### 3 Methods to ingest data:

1. Batch - CREATE TABLE AS (CTAS)
- creates a delta table from cloud storage location 

```sql
CREATE TABLE table_name AS
    SELECT *
    FROM read_files(
        '<path_to_file>',
        format = '<file_type>',
        '<other_format_options>'
    )
```
*read_file*
- function that reads files from location and returns data in tabluar form
- supported formats include JSON, CSV, XML, TXT, PARQUET, AVRO, ORC
- can auto detect file formats and infer schema
- can be used in **streaming tables** to incremently read in data.