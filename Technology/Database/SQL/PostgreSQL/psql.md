psql - PostgreSQL interactive terminal
"psql is a terminal-based front-end to PostgreSQL. It enables you to type in queries interactively, issue them to PostgreSQL, and see the query results. Alternatively, input can be from a file or from command line arguments."

Connect to db:
```shell
psql -h blade.internal.bladeranger.com -U reader logs
```
- `-h` sets the hostname. `blade.internal.bladeranger.com` - is the host.
- `-U` sets the user. `reader` - is the user
- `logs` - database name
Password will be prompted for.

### Example queries:
last 35 runs
```sql
select * from run order by id desc limit 35;
```
last 30 runs of robot rubin and user ava
```sql
select * from run where recording_user='ava' and robot = 'rubin' order by start desc limit 30;
```
see similar keys
```sql
select distinct key from fluent_all where run_id = 2721 and key like '%angle_from_up%';
```
limit by time and fluent(key like..)
```sql
select * from fluent_all where run_id = 1293 and tstamp > '2022-03-24 10:00:00' and (key like '/sensors/brush_speed' or key like '/sensors/brush_current_front');
```
see any fluents similar to angle_from_line
```sql
select key, value_text, tstamp from fluent_all where run_id = 2819  and (key like '%angle_from_line%' );
```

show all tables:  `\d`
display table's columns: `\d+ fluent_all;` or `\d fluent_all` 

##### some samples from [[psql_queries|blade-ranger]] usage.
Get the **left** number from cell containing string "[left,right]":
```sql
select tstamp, right(split_part(value_text, ',', 1), -1) from fluent_all where run_id = 1426 and tstamp > '2022-03-30' and key = '/sensors/brush_speed' and value_text != 'None';
```
Get the **right** number from cell containing string "[left,right]"
```sql
select tstamp, left(split_part(value_text, ',', 2), -1) from fluent_all where run_id = 1426 and tstamp > '2022-03-30' and key = '/sensors/brush_speed' and value_text != 'None';
```
how to use variables:
```sql
WITH my_values (_run_id, _from_day, _fluent_name) as (
   values (1426, '2022-03-30', '/sensors/brush_speed')
)

select tstamp, value_text from fluent_all, my_values where run_id = _run_id and tstamp > '2022-03-30' and key = _fluent_name and value_text != 'None';
```
using now(). Getting rows from the last 3 days:
`WHERE TSTAMP >= now() - interval '3 day' and tstamp <= now() `
To describe a table:
`\d+ fluent_all;`  -this doesn't work in *pgAdmin*. The follwoing does.
```sql
select column_name, data_type, character_maximum_length, column_default, is_nullable
from INFORMATION_SCHEMA.COLUMNS where table_name = '<table_name>';
```

backup a table:
```sql
create table BF_BAN_BKP as select * from BF_BAN;
```