Postgresql
==========

# Connect in the console to Postgresql
sudo su - postgres -c psql

# Verify if user has table or database privilege
select has_table_privilege('<user>', '<table>', 'insert');

select has_database_privilege('<user>', '<database>', 'connect');

# List all privileges of a user
select *  FROM information_schema.table_privileges where grantee = '<User or Role>'

# Verify if a user or role exists
select count(*) from pg_roles where rolname='<User or Role>'

# Assign a role to a user
GRANT <Role> TO <User>

# Grant privileges to a user or role
GRANT INSERT, DELETE, UPDATE, SELECT ON ALL TABLES IN SCHEMA <Schema> to <User>

# Revoke privileges from a user or role
REVOKE INSERT, DELETE, UPDATE, SELECT ON ALL TABLES IN SCHEMA <Schema> from <User>
