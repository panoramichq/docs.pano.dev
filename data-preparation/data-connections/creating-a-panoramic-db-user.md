# Creating a Panoramic DB User

## Why do I need to Create a DB User?

TBD

#### What Permissions will I need?

* Read Access \(GRANT SELECT permission\)
  * Data Preparation
  * Data Definition
  * Data Transformation
  * Data Monitoring & Insights
* Read & Write Access \(GRANT ALL PRIVILEGES permission\)
  * Data Integration

## SQL Helpers to create users & grant permissions

Panoramic recommends creating a dedicated user for the Panoramic platform. This makes it easier for your engineering team to manage access controls and monitor usage & performance. 

### MySQL

```sql
-- create user
CREATE USER 'PANORAMIC'@'%' IDENTIFIED BY 'USE_A_NICE_STRONG_PASSWORD_PLEASE';

-- grant select for this user
GRANT SELECT ON mydb.* TO 'PANORAMIC'@'%';

-- grant all for this user
GRANT ALL PRIVILEGES ON mydb.* TO 'PANORAMIC'@'%';
```

### PostgreSQL

```sql
-- create user
CREATE ROLE PANORAMIC WITH LOGIN ENCRYPTED PASSWORD 'USE_A_NICE_STRONG_PASSWORD_PLEASE';

-- grant connect privilege
GRANT CONNECT ON DATABASE mydb TO PANORAMIC;

-- repeat this for other schemas too
GRANT USAGE ON SCHEMA public TO PANORAMIC;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO PANORAMIC;

-- remember to repeat this for other schemas too
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO PANORAMIC;
```

### Snowflake

### Google BigQuery

### Amazon Redshift

```sql
-- create user
CREATE USER PANORAMIC PASSWORD 'USE_A_NICE_STRONG_PASSWORD_PLEASE';

-- repeat this for other schemas too
GRANT USAGE ON SCHEMA public TO PANORAMIC;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO PANORAMIC;

-- remember to repeat this for other schemas too
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO PANORAMIC;
```

