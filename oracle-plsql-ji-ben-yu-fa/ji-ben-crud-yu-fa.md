# 基本CRUD語法

### -- Select

SELECT t.\* FROM table t WHERE t.name = 'XXX' AND t.number = '1';

### -- Delete

DELETE FROM table t WHERE t.yearmonth &lt; '20180101';

### -- Insert

INSERT INTO table t \( column\_a, column\_b \) VALUES \( 'AAA', 'BBB' \);

### -- Update

UPDATE table t SET column\_a = 'AAA123' WHERE column\_a = 'AAA' AND column\_b = 'BBB';

### -- 查詢條件

* 以及：WHERE...AND
* 或：WHERE...OR

### --查詢出的欄位另外命名

SELECT year 年度 FROM table;

### --查詢出的欄位直接給值

SELECT '2018' year FROM table;

### -- 兩項查詢結果組合一起呈現

UNION ALL

### -- 欄位符合其中之一項

IN\('AAA','BBB'\)

### -- 欄位模糊查詢

* 內含：LIKE '%AAA%'
* 內不含：NOT LIKE '%AAA%

### -- 是否為空

* 為空：IS NULL
* 不為空：IS NOT NULL

### -- 區間條件

* num &gt;= '1' AND num &lt;= '3'
* num BETWEEN '1' AND '3'

### -- 結果資料排序

* 大到小：ORDER BY num DESC
* 小到大：ORDER BY num ASC

### -- 前幾筆

ROWNUM = 1;

### -- 如果是NULL,則用此值

NVL\(year, '--'\)

### -- 時間與字串轉換

* 時間轉字串：TO\_CHAR\(year, 'YYYY'\)
* 字串轉時間 ：TO\_DATE\('20180101','YYYYMMDD'\)

### -- 擷取資料

SUBSTR\(year, 3, 2\)   _第三位開始，長度為二_

### -- 加總每筆資料的此欄位值

SUM\(value\_amt\)

### -- 替換值

* DECODE\(year, '2017', 'lastyear', '2018', 'thisyear', 'whocares'\)
* \(CASE WHEN year = '2017' THEN 'lastyear'  WHEN year = '2018' THEN 'thisyear'  ELSE 'whocares' END\) year





