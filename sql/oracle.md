
- [Oracle常用命令](#oracle常用命令)
  - [从现有的表创建表并复制数据](#从现有的表创建表并复制数据)
  - [oracle时间比较](#oracle时间比较)


# Oracle常用命令
## 从现有的表创建表并复制数据
```
create table newtable
as select * from oldtable;
<br/>

例子:
create table INPATIENT_EMR_SET_HH
as select * from INPATIENT_EMR_SET where ENC_DEPT_ID in (
    select ORG_ID
    from ORGANIZATION
    where ORG_NO in ('9966', '9967', '9968', '9969', '9972', '9973', '9974', '9975', '9976', '9977', '9978', '9979'))
and IS_DEL=0 and INP_EMR_STATUS not in (960074,390030405)
order by CREATED_AT asc
```

## oracle时间比较
```
to_date函数
select * from table CREATED_AT < to_date('2022-12-11 12:39:51','yyyy-mm-dd hh:mi:ss')

```
