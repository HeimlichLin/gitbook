# 基本Table建立

#### 基本Table建立

**-- Create table**

create table COUNTRYCODE  
\(  
CONTINENT VARCHAR2\(50\) not null,  
COUNTRYID VARCHAR2\(5\) not null,  
COUNTRYNAME VARCHAR2\(100\) not null,  
COUNTRYENAME VARCHAR2\(200\),  
NEWSOUTHCOUNTRY VARCHAR2\(2 BYTE\) default 'N'  
\)  
tablespace DATA  
pctfree 10  
initrans 1  
maxtrans 255  
storage  
\(  
initial 64K  
next 1M  
minextents 1  
maxextents unlimited  
\);

**-- Add comments to the table**

`comment on table COUNTRYCODE  
is '國別代碼表';`

**-- Add comments to the columns**

`comment on column COUNTRYCODE.CONTINENT  
is '洲別';  
comment on column COUNTRYCODE.COUNTRYID  
is '國別代碼';  
comment on column COUNTRYCODE.COUNTRYNAME  
is '國家中文名稱';  
comment on column COUNTRYCODE.COUNTRYENAME  
is '國家英文名稱';  
comment on column COUNTRYCODE.NEWSOUTHCOUNTRY  
is '新南向國家';`

**-- Create/Recreate primary, unique and foreign key constraints**

`alter table COUNTRYCODE  
add constraint COUNTRYCODE_PK primary key (CONTINENT, COUNTRYID)  
using index  
tablespace DATA  
pctfree 10  
initrans 2  
maxtrans 255  
storage  
(  
initial 64K  
next 1M  
minextents 1  
maxextents unlimited  
);`

**-- Create/Recreate indexes**

`create index COUNTRYCODE_IDX_1 on COUNTRYCODE (CONTINENT)  
tablespace DATA  
pctfree 10  
initrans 2  
maxtrans 255  
storage  
(  
initial 64K  
next 1M  
minextents 1  
maxextents unlimited  
);  
create index COUNTRYCODE_IDX_2 on COUNTRYCODE (COUNTRYID, COUNTRYENAME)  
tablespace DATA  
pctfree 10  
initrans 2  
maxtrans 255  
storage  
(  
initial 64K  
next 1M  
minextents 1  
maxextents unlimited  
);`

