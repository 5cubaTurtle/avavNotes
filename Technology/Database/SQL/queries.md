#sql #db

Present data types of a table:`describe NAME_OF_TABLE`  
sort by column:`select * from RC_SIML_CHARGE order by ENT_SEQ_NO desc;`  

### Oracle SQL developer GUI
define variables:
```sql
define jobName = 'CSREGMIGR';
define operId = 'vstwrk39';
define jobReq = 'BYREQ';
```
use variables:  
```sql
Insert into OPPROG_DB
  (OPPROG_DB_JOB_NAME,OPPROG_DB_PREFIX,OPPROG_DB_REQUEST_FLAG,OPPROG_DB_RUN_ID,OPPROG_DB_LAST_DATE,CREATION_DATE,UPDATE_DATE,OPERATOR_ID)
  values
  ('&jobName','VST','1',null,null,SYSDATE,SYSDATE,'OPER');
```

