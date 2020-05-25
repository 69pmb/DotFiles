## MySql
- Remove liquibase lock:  
`UPDATE CONFIGURATION_ADMINISTRATION_DATABASECHANGELOGLOCK SET LOCKED=0, LOCKGRANTED=null, LOCKEDBY=null ;`
- clean db:  
```sql
DROP SCHEMA ticketmaster;
CREATE SCHEMA ticketmaster;
```
- select  db:  
`use ticketmaster;`
- List tables:  
`show tables;`