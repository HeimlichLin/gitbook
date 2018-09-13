# 基本CRUD語法

### -- Select

SELECT t.\* FROM table t WHERE t.name = 'XXX' AND t.number = '1';

### -- Delete

DELETE FROM table t WHERE t.yearmonth &lt; '20180101';

### -- Insert

INSERT INTO table t \( column\_a, column\_b \) VALUES \( 'AAA', 'BBB' \);

### -- Update

UPDATE table t SET column\_a = 'AAA123' WHERE column\_a = 'AAA' AND column\_b = 'BBB';

### -- 删除约束

ALTER TABLE table DROP CONSTRAINT TABLE\_PK CASCADE;

### -- 新建主键约束

ALTER TABLE table ADD CONSTRAINT TABLE\_PK PRIMARY KEY\(column\_a, column\_b\);

### -- 新增index

CREATE INDEX TABLE\_IDX\_1 ON table\(column\_a\); 

CREATE INDEX TABLE\_IDX\_2 ON table \(column\_a, column\_b\);

### -- Table調整欄位長度

ALTER TABLE table add column\_a varchar\(200\);

ALTER TABLE table ADD column\_c NUMBER\(12,2\);



