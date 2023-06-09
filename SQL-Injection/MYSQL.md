### Version
```
SELECT @@version;
```
### Comments
```
SELECT 1; #comment
SELECT /*comment*/1;
```
### Current User
```
SELECT user();
SELECT system_user;
```
### List Users (PRIV)
```
SELECT user FROM mysql.user;

```
### List Password Hashes (PRIV)
```
SELECT host, user, password FROM mysql.user;

```
### List Privileges (PRIV)
```
#List user privileges
SELECT grantee, privilege_type, is_grantable FROM information_schema.user_privileges
​
#List privs on databases (schemas)
SELECT grantee, table_schema, privilege_type FROM information_schema.schema_privileges;
​
#List privs on columns
SELECT table_schema, table_name, column_name, privilege_type FROM information_schema.column_privileges;
```
### List DBA Accounts (PRIV)
```
SELECT grantee, privilege_type, is_grantable FROM information_schema.user_privileges WHERE privilege_type = 'SUPER';
SELECT host, user FROM mysql.user WHERE Super_priv = 'Y';
```
### Current Database
```
SELECT database();
```
### List Databases
```
SELECT schema_name FROM information_schema.schemata;
SELECT distinct(db) FROM mysql.db
```
### List Tables 
```
SELECT table_schema,table_name FROM information_schema.tables WHERE table_schema != 'mysql' AND table_schema != 'information_schema'
```
### List Columns
```
SELECT table_schema, table_name, column_name FROM information_schema.columns WHERE table_schema != 'mysql' AND table_schema != 'information_schema'
```
### Find Tables from Column Name
```
#If you want to list all the table names that contain a column LIKE '%password%':
SELECT table_schema, table_name FROM information_schema.columns WHERE column_name = 'password';
```
### Hostname, IP Address
```
SELECT @@hostname;
```
### Create Users (PRIV)
```
CREATE USER test1 IDENTIFIED BY 'pass1';
```
### Delete Users (PRIV)
```
DROP USER test1;
```
### Make User DBA (PRIV)
```
GRANT ALL PRIVILEGES ON *.* TO test1@'%';
```
### Location of DB Files
```
SELECT @@datadir;
```
### Read Files (PRIV)
```
SELECT LOAD_FILE('/etc/passwd');
```
### Write Files (PRIV)
```
SELECT * FROM mytable INTO dumpfile '/tmp/somefile';
```
