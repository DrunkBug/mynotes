## oracle
- 创建表空间   
```sql
    create tablespace TABLESPACE_NAME datafile '/oradata/datafile/xxx.dbf' size 1024m --表空间默认初始值。
    autoextend on next 2000M  --自动增长量。
    maxsize unlimited  --最大上限。
    extent management local autoallocate   
    segment space management auto ;
``` 
- 指定单个用户默认表空间   
   1. 建立用户时直接指定   
   ```sql 
    create user xiaojiu identified by xiaojiu default tablespace TABLESPACE_NAME;
    ```
    or
    ```sql 
    create user xiaojiu  identified by xiaojiu ;                         
    alter user xiaojiu  default tablespace TABLESPACE_NAME;
    ```
    2. 查看所有用户的默认表空间
    ``` sql 
    select username,default_tablespace from dba_users;   
    ```
*USERS表空间也就是默认用户表空间。
在创建一个用户并没有指定此用户使用表空间时，该用户所有信息都会放入到users表空间中*