Postgresql
==========

## Connect in the console to Postgresql
```bash
sudo su - postgres -c psql
```

## Verify if user has table or database privilege

```sql
select has_table_privilege('YourUser', 'YourTable', 'insert');

select has_database_privilege('YourUser', 'YourDatabase', 'connect');
```

## List all privileges of a user
```sql
select *  FROM information_schema.table_privileges where grantee = 'YourUser or YourRole'
```

## Verify if a user or role exists
```sql
select count(*) from pg_roles where rolname='YourUser or YourRole'
```

## Assign a role to a user
```sql
GRANT YourRole TO YourUser
```

## Grant privileges to a user or role
```sql
GRANT INSERT, DELETE, UPDATE, SELECT ON ALL TABLES IN SCHEMA YourSchema to YourUser
```
## Revoke privileges from a user or role

```sql
REVOKE INSERT, DELETE, UPDATE, SELECT ON ALL TABLES IN SCHEMA YourSchema from YourUser
```

## Detect deadlocks
```sql
SELECT blocked_locks.pid     AS blocked_pid,
         blocked_activity.usename  AS blocked_user,
         blocking_locks.pid     AS blocking_pid,
         blocking_activity.usename AS blocking_user,
         blocked_activity.query    AS blocked_statement,
         blocking_activity.query   AS current_statement_in_blocking_process
   FROM  pg_catalog.pg_locks         blocked_locks
    JOIN pg_catalog.pg_stat_activity blocked_activity  ON blocked_activity.pid = blocked_locks.pid
    JOIN pg_catalog.pg_locks         blocking_locks 
        ON blocking_locks.locktype = blocked_locks.locktype
        AND blocking_locks.DATABASE IS NOT DISTINCT FROM blocked_locks.DATABASE
        AND blocking_locks.relation IS NOT DISTINCT FROM blocked_locks.relation
        AND blocking_locks.page IS NOT DISTINCT FROM blocked_locks.page
        AND blocking_locks.tuple IS NOT DISTINCT FROM blocked_locks.tuple
        AND blocking_locks.virtualxid IS NOT DISTINCT FROM blocked_locks.virtualxid
        AND blocking_locks.transactionid IS NOT DISTINCT FROM blocked_locks.transactionid
        AND blocking_locks.classid IS NOT DISTINCT FROM blocked_locks.classid
        AND blocking_locks.objid IS NOT DISTINCT FROM blocked_locks.objid
        AND blocking_locks.objsubid IS NOT DISTINCT FROM blocked_locks.objsubid
        AND blocking_locks.pid != blocked_locks.pid
 
    JOIN pg_catalog.pg_stat_activity blocking_activity ON blocking_activity.pid = blocking_locks.pid
   WHERE NOT blocked_locks.GRANTED;
```

## Kill blocking processes

```sql
SELECT
    pg_terminate_backend(pid) 
FROM
    pg_stat_activity 
WHERE
    -- don’t kill my own connection!
    pid = YourPID
    -- don’t kill the connections to other databases
    AND datname = 'YourDatabase'
    ;
```
## Get the last value of a sequence
```sql
select last_value from "YourSchema"."YourSequenceName";
```
## Alter the counter of a sequence
```sql
ALTER SEQUENCE "YourSchema"."YourSequenceName" RESTART WITH NewSequenceCounter;
```

Note: to alter correctly the NewSequenceCounter should be last_value + 1
