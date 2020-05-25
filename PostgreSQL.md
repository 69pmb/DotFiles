## PostgreSQL
- Log in:  
`psql -h localhost -p 5432 -U Property -w`
- List tables:  
`SELECT * FROM pg_catalog.pg_tables;`
- List namespace:  
`select * from pg_catalog.pg_namespace;`
- Clean db:  
`DROP SCHEMA property CASCADE; CREATE SCHEMA property;`
