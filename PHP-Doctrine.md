- **Explain: `migrations:migrate YYYYMMDDHHMMSS`**  
Specify the version you wish to migrate to.  
Read more:  
https://stackoverflow.com/questions/9632701/doctrine2-migrations-migrate-down-and-migrate-from-browser-and-not-command-line  

- **Explain: `migrations:execute YYYYMMDDHHMMSS  --up`**  
Execute a migration up.  
Read more:  
https://stackoverflow.com/questions/9632701/doctrine2-migrations-migrate-down-and-migrate-from-browser-and-not-command-line  

- **Explain: `migrations:execute YYYYMMDDHHMMSS  --down`**  
Execute a migration down.  
Read more:  
https://stackoverflow.com/questions/9632701/doctrine2-migrations-migrate-down-and-migrate-from-browser-and-not-command-line  

- **Explain: `migrations:status`**  
Check for migrations versions (current and last).  
Read more:  
https://stackoverflow.com/questions/9632701/doctrine2-migrations-migrate-down-and-migrate-from-browser-and-not-command-line  

- **Explain `bin/console doctrine:mapping:info`**  
???  
Read more:  
???  

- **What is the difference betwen `doctrine:schema:create` and `doctrine:schema:update --force --no-interaction`?**  
`doctrine:schema:create` - Executes (or dumps) the SQL needed to generate the database schema.  
`doctrine:schema:update` - Executes (or dumps) the SQL needed to update the database schema to match the current mapping metadata.  
The updating of databases uses a Diff Algorithm for a given Database Schema.  
Read more:  
https://www.doctrine-project.org/projects/doctrine-orm/en/2.6/tutorials/getting-started.html  

