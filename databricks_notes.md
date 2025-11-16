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


2. COPY INTO (legacy)
- incremental batch
- skips files that have already been loaded

```sql
CREATE TABLE table_name;
COPY INTO table_name --no schema suggested
FROM '<dir_path>'
FILEFORMAT='<file_type>'  -- file format
FORMAT_OPTIONS(<options>) --how source files paresed & interpreted
COPY_OPTIONS(<options>)
```

3. Auto-loader 
- incremental batch or streaming options
- use w/ both Python and SQL
- can process billions of files
- built upon Spark Structured Streaming
