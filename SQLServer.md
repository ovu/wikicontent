SQL Server
-----------

## Best practices
### Use nolock on queries
nolock allows other processes to read the same table while your process is still reading. It is a best practice because it will avoid slowing down query execution. 

Sample:

>SELECT t.column1, t.column2
>FROM tableA t (nolock)
>INNER JOIN tableB t2 (nolock) ON (t2.ID = t.ID)

## Query optimization
### Use ltrim
Comparing strings is not something recommended in SQL queries because they are slow. The query completion time will be increased proportional to the size of the table rows that are being compared. When the comparison of strings cannot be avoided, then the ltrim can help to optimize the query.  
Sample:
>SELECT t.column1, t.column2
>FROM tableA t, tableB t2
>WHERE t.fileID = 1
>AND ltrim(t.FirstName) = ltrim(t2.FirstName)

## Useful Queries

### Fragmentation information of a table

> DBCC showcontig(Table)

It will be deprecated. Use sys.dm_db_index_physical_stats instead.

### Get foreign keys referencing a given table

	select t.name as TableWithForeignKey, fk.constraint_column_id as FK_PartNo , c.name as ForeignKeyColumn
	from sys.foreign_key_columns as fk
	inner join sys.tables as t on fk.parent_object_id = t.object_id
	inner join sys.columns as c on fk.parent_object_id = c.object_id and fk.parent_column_id = c.column_id
	where fk.referenced_object_id = (select object_id from sys.tables where name = 'TableOthersForeignKeyInto')
	order by TableWithForeignKey, FK_PartNo

