## MySql
- Connect to a db: 
`mysql -uticketmaster -pticketmaster`
- Remove liquibase lock: 
`UPDATE CONFIGURATION_ADMINISTRATION_DATABASECHANGELOGLOCK SET LOCKED=0, LOCKGRANTED=null, LOCKEDBY=null ;`
- clean db: 
```sql
DROP database ticketmaster;
CREATE database ticketmaster;
```
- select db: 
`use ticketmaster;`
- List tables: 
`show tables;`