# Connect to your Database

## Why do I need to Create a DB User?

In order to utilize Pano, we need access to your data warehouse. While it's certainly possible to use an existing database user, our recommended best practice is to create a user specifically for Pano.

This enables you to give Pano only the access required to help you understand & transform your data. It also makes it easy for you to monitor every query that is run and the data Pano accesses.

#### What Permissions will I need?

* Read Access \(GRANT SELECT permission\)
  * Data Preparation
  * Data Definition
  * Data Transformation
  * Data Monitoring & Insights
* Read & Write Access \(GRANT ALL PRIVILEGES permission\)
  * Data Integration

## SQL Helpers to create users & grant permissions

Pano recommends creating a dedicated user for the Pano platform. This makes it easier for your engineering team to manage access controls and monitor usage & performance. 

### MySQL

```sql
-- create user
CREATE USER 'PANO'@'%' IDENTIFIED BY 'USE_A_NICE_STRONG_PASSWORD_PLEASE';

-- grant select for this user
GRANT SELECT ON mydb.* TO 'PANO'@'%';

-- grant all for this user
GRANT ALL PRIVILEGES ON mydb.* TO 'PANO'@'%';
```

### PostgreSQL

```sql
-- create user
CREATE ROLE PANO WITH LOGIN ENCRYPTED PASSWORD 'USE_A_NICE_STRONG_PASSWORD_PLEASE';

-- grant connect privilege
GRANT CONNECT ON DATABASE mydb TO PANO;

-- repeat this for other schemas too
GRANT USAGE ON SCHEMA public TO PANO;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO PANO;

-- remember to repeat this for other schemas too
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO PANO;
```

### Snowflake

In order to prepare a Snowflake connection, Pano needs the following rights in your warehouse:

* USER and ROLE with appropriate access
* SELECT access to any tables or views you wants to read
* USAGE access on any schemas or databases you want to read
* ALL access on the write schema (by default we call it “PANORAMIC”)
* USAGE, OPERATE, MONITOR on a warehouse
* IP whitelist (if configured)

The following SQL can be used to accomplish everything above.

```sql
BEGIN;
-- IMPORTANT: update the in-line password below with a random password (at least 20 characters)

-- create variables for user / password / role / warehouse / database (needs to be uppercase for objects)
SET ROLE_NAME = 'PANORAMIC_ROLE';
SET USER_NAME = 'PANORAMIC_USER';
SET WAREHOUSE_NAME = 'PANORAMIC_WH';
SET DATABASE_NAME = 'PANORAMIC_DB';

-- Change role to securityadmin for user / role steps
USE ROLE SECURITYADMIN;

-- optional create network policy
CREATE NETWORK POLICY IF NOT EXISTS PANORAMIC_NETMASKS
    ALLOWED_IP_LIST=('3.234.248.56/30','3.123.12.148/30')
    BLOCKED_IP_LIST=() COMMENT='Panoramic Network Addresses';

-- Create role for pano & give access to role
CREATE ROLE IF NOT EXISTS IDENTIFIER($ROLE_NAME);
GRANT ROLE IDENTIFIER($ROLE_NAME) TO ROLE SYSADMIN;

-- Create a new user for Pano
CREATE USER IF NOT EXISTS IDENTIFIER($USER_NAME)
-- !!!! This line needs password string as marked !!!!
    PASSWORD = '{PASSWORD STRING GOES HERE}'
-- !!!! This line needs password string as marked !!!!
    DEFAULT_ROLE = $ROLE_NAME
    DEFAULT_WAREHOUSE = $WAREHOUSE_NAME;
GRANT ROLE IDENTIFIER($ROLE_NAME) TO USER IDENTIFIER($USER_NAME);

-- change role to sysadmin for warehouse / database steps
USE ROLE SYSADMIN;

-- create warehouse & grant permissions
-- note: grant all permissions to enable us to modify & control warehouse size if needed
CREATE WAREHOUSE IF NOT EXISTS IDENTIFIER($WAREHOUSE_NAME)
    WAREHOUSE_SIZE = XSMALL WAREHOUSE_TYPE = STANDARD
    AUTO_SUSPEND = 60 AUTO_RESUME = TRUE INITIALLY_SUSPENDED = TRUE;
GRANT ALL PRIVILEGES ON WAREHOUSE IDENTIFIER($WAREHOUSE_NAME) TO ROLE IDENTIFIER($ROLE_NAME);

-- create database
CREATE DATABASE IF NOT EXISTS IDENTIFIER($DATABASE_NAME);
USE DATABASE IDENTIFIER($DATABASE_NAME);

-- grant pano full access to database
GRANT ALL PRIVILEGES ON DATABASE IDENTIFIER($DATABASE_NAME) TO ROLE IDENTIFIER($ROLE_NAME);

COMMIT;
```

Once you create the user and role for Panoramic, you must grant the Panoramic role access to the data you want to view in the platform. The recommended method is to grant roles for other services to the Panoramic role. For example, if you use Fivetran you can use the following to grant Pano access to your Fivetran data:

```sql
GRANT ROLE PC_FIVETRAN_ROLE TO ROLE PANORAMIC_ROLE;
```

### Google BigQuery

When connecting BigQuery, we will generate a Google Cloud [service account](https://cloud.google.com/iam/docs/service-accounts) unique to your company. You will then need to grant that user access to the Google Cloud Project that contains your BigQuery data.

Pano requires the following roles in Google Cloud:

| Role | Where | Reason |
| :--- | :--- | :--- |
| BigQuery User | Project | Gives Pano permission to see the schema of tables in your account, and gives us permission to create jobs to query the data from your account |
| BigQuery Data Viewer | Project or tables | Gives Pano permission to access the data in your account. The recommended approach is to grant this role on the project level, but if you prefer to limit the access that Pano has to your data, you can use the [sharing feature](https://cloud.google.com/bigquery/docs/dataset-access-controls) to only grant this role on specific tables you want us to access. |

You will need to create a new BigQuery connection in the console. This will give you your unique service account email address. You will need to put this into the Google IAM console:

![](../../.gitbook/assets/google-iam-overview.png)

After clicking the "Add" button, you will be presented with a screen where you must input the service account and grant roles to it. Once you grant the correct roles, your screen should look like the following:

![](../../.gitbook/assets/bq-add-user2.png)

Finally, click the "Save" button and verify the account is added correctly:

![](../../.gitbook/assets/google-iam-final.png)

### Amazon Redshift

```sql
-- create user
CREATE USER PANO PASSWORD 'USE_A_NICE_STRONG_PASSWORD_PLEASE';

-- repeat this for other schemas too
GRANT USAGE ON SCHEMA public TO PANO;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO PANO;

-- remember to repeat this for other schemas too
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO PANO;
```

