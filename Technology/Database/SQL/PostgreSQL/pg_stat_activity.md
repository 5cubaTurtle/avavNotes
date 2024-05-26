[guide](https://www.commandprompt.com/education/how-to-get-list-of-running-queries-in-postgresql/#:~:text=Conclusion-,PostgreSQL%20provides%20a%20system%20view%20named%20pg_stat_activity%20that%20retrieves%20information,and%20performance%20of%20a%20database.)
PostgreSQL provides a system view named `pg_stat_activity` that retrieves information about the currently running queries and active sessions on the database server.
`pg_stat_activity` view is listed below:
- **datid**: It displays the OID of the database with which the session is associated.
- **datname**: This column shows the name of the database.
- **pid**: An integer-type column that shows the process ID of the session.
- **usename**: It represents the user name.
- **client_addr**: It retrieves the IP address information.
- **application_name**: This column retrieves the application/client name.
- **query**: this column shows the information about the currently executing query/command.
- **state**: Shows the session’s current state, like "active", "idle", etc.).
- **wait_event_type** and **wait_event**: these are Text-type columns that show the type of event a session is waiting for and the name of the event, respectively.

get the `pg_stat_activity` table:
```sql
select * from pg_catalog.pg_stat_activity;
```
