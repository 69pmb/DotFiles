## PostgreSQL
- Log in:  
`psql -h localhost -p 5432 -U <user> -d <database>`
- List db:  
`\list` or `\c`  
- Switch db:  
`\connect dbname` or `\c db`
- List table:  
`\dt`
- Docker all in:  
`docker exec -it <container_id> psql -U <user> -d <db>`
- List tables:  
`SELECT * FROM pg_catalog.pg_tables;`
- List namespace:  
`select * from pg_catalog.pg_namespace;`
- Clean db:  
`DROP SCHEMA property CASCADE; CREATE SCHEMA property;`
- Show columns:  
`SELECT table_name, column_name, data_type, is_nullable FROM information_schema.columns WHERE table_name = '' order by column_name;`
- Show constraints:  
`SELECT con.* FROM pg_catalog.pg_constraint con INNER JOIN pg_catalog.pg_class rel ON rel.oid = con.conrelid INNER JOIN pg_catalog.pg_namespace nsp ON nsp.oid = connamespace WHERE rel.relname = '';`
- Create db:  
`create database <db>;`
