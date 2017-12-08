Postgresql
==========

## Connect in the console to Postgresql
sudo su - postgres -c psql

## Verify if user has table or database privilege
select has_table_privilege('YourUser', 'YourTable', 'insert');

select has_database_privilege('YourUser', 'YourDatabase', 'connect');

## List all privileges of a user
select *  FROM information_schema.table_privileges where grantee = 'YourUser or YourRole'

## Verify if a user or role exists
select count(*) from pg_roles where rolname='YourUser or YourRole'

## Assign a role to a user
GRANT YourRole TO YourUser

## Grant privileges to a user or role
GRANT INSERT, DELETE, UPDATE, SELECT ON ALL TABLES IN SCHEMA YourSchema to YourUser

## Revoke privileges from a user or role
REVOKE INSERT, DELETE, UPDATE, SELECT ON ALL TABLES IN SCHEMA YourSchema from YourUser
