# 其他語法

### 較常用基本資料型態

* char：固定長度字串
* varchar2：可變長度字串
* long：長資料
* number\(x, y\)：可以存儲浮點值或整數值，x整數位數，y小數位數
* date ： 日期，DD-MON-YY
* rowid：列標籤，系統自建，唯一值
* boolean：布林值

### 註解

* 單行註解：「--」
* 多行註解：「/_」開始 ，「_/」結束

### 删除约束

* ALTER TABLE table DROP CONSTRAINT TABLE\_PK CASCADE;

### 新建主键约束

* ALTER TABLE table ADD CONSTRAINT TABLE\_PK PRIMARY KEY\(column\_a, column\_b\);

### 新增index

* CREATE INDEX TABLE\_IDX\_1 ON table\(column\_a\); 
* CREATE INDEX TABLE\_IDX\_2 ON table \(column\_a, column\_b\);

### Table調整欄位資料

* 增加字串欄位：ALTER TABLE table ADD column\_a VARCHAR\(200\);
* 增加數字欄位：ALTER TABLE table ADD column\_c NUMBER\(12,2\);
* 改變欄位名稱：ALTER TABLE table CHANGE column\_a column\_d;
* 改變欄位：ALTER TABLE table CHANGE column\_a NUMBER\(12,2\);
* 刪除欄位：ALTER TABLE table DROP column\_a;

### 清除Table

* DROP TABLE table;

### 清除Table內的資料

* TRUNCAFTE TABLE table;
*  DELETE FROM table;

### Table與Column查詢

1. SELECT \* FROM ALL\_TAB\_COMMENTS;
2. SELECT \* FROM ALL\_COL\_COMMENTS;
3. SELECT \* FROM ALL\_CONS\_COLUMNS;
4. SELECT \* FROM ALL\_TAB\_COLS;
5. SELECT \* FROM ALL\_IND\_COLUMNS;
6. SELECT \* FROM ALL\_INDEXES;

