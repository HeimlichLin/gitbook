# 其他語法

### -- 删除约束

* ALTER TABLE table DROP CONSTRAINT TABLE\_PK CASCADE;

### -- 新建主键约束

* ALTER TABLE table ADD CONSTRAINT TABLE\_PK PRIMARY KEY\(column\_a, column\_b\);

### -- 新增index

* CREATE INDEX TABLE\_IDX\_1 ON table\(column\_a\); 
* CREATE INDEX TABLE\_IDX\_2 ON table \(column\_a, column\_b\);

### -- Table調整欄位資料

* 增加字串欄位：ALTER TABLE table ADD column\_a VARCHAR\(200\);
* 增加數字欄位：ALTER TABLE table ADD column\_c NUMBER\(12,2\);
* 改變欄位名稱：ALTER TABLE table CHANGE column\_a column\_d;
* 改變欄位：ALTER TABLE table CHANGE column\_a NUMBER\(12,2\);
* 刪除欄位：ALTER TABLE table DROP column\_a;

### -- 清除Table

* DROP TABLE table;

### -- 清除Table內的資料

* TRUNCAFTE TABLE table;
*  DELETE FROM table;

