# 基本CRUD語法

### -- Select

* SELECT t.\* FROM table t WHERE t.name = 'XXX' AND t.number = '1';

### -- Delete

* DELETE FROM table t WHERE t.yearmonth &lt; '20180101';

### -- Insert

* INSERT INTO table t \( column\_a, column\_b \) VALUES \( 'AAA', 'BBB' \);

### -- Update

* UPDATE table t SET column\_a = 'AAA123' WHERE column\_a = 'AAA' AND column\_b = 'BBB';

### -- 查詢條件

* 以及：WHERE...AND
* 或：WHERE...OR
* SELECT DISTINCT year, month FROM table;

### --查詢欄位

* 查詢選擇欄位，並列出不重複的所有組合：SELECT DISTINCT year, month FROM table;
* 欄位另外命名：SELECT year 年度 FROM table;
* 欄位直接給值：SELECT '2018' year FROM table;

### -- 兩項查詢結果組合一起呈現

* UNION：OR 聯集，重複的只會出現一次
* UNION ALL：OR 聯集，允許重複出現
* INTERSECT：AND 交集，都有的才會出現，重複的只會出現一次
* MINUS：相減，第一個有，第二個沒有的才會出現

### -- 查詢條件

#### 欄位符合其中之一項

* IN\('AAA','BBB'\)

#### 欄位模糊查詢

* 內含：LIKE '%AAA%'
* 內不含：NOT LIKE '%AAA%

#### 是否為空

* 為空：IS NULL
* 不為空：IS NOT NULL

#### 區間條件

* num &gt;= '1' AND num &lt;= '3'
* num BETWEEN '1' AND '3'

#### 前幾筆

* ROWNUM = 1;

### -- 結果資料排序

* 大到小：ORDER BY num DESC
* 小到大：ORDER BY num ASC

### -- 計算筆數

* SELECT count\(\*\) FROM table;
* SELECT count\(\*\), year, month FROM table group by year, month;

### -- 群組後，再下條件

* SELECT count\(\*\), year, month FROM table group by year, month having year = '2018';

### -- 時間與字串轉換

* 時間轉字串：TO\_CHAR\(year, 'YYYY'\)
* 字串轉時間 ：TO\_DATE\('20180101','YYYYMMDD'\)

### -- 處理資料

* 擷取欄位資料：SUBSTR\(year, 3, 2\)   _第三位開始，長度為二_
* 欄位資料組合：year\|\|month
* 欄位資料組合：CONCAT\('year', 'month'\)

### -- 欄位值運算

* 欄位加總：SUM\(value\_amt\)
* 欄位平均：AVG\(value\_amt\)
* 欄位最大：MAX\(value\_amt\)
* 欄位最小：MIN\(value\_amt\)

### -- 替換值

* 如果是NULL，則用此值：NVL\(year, '--'\)
* REPLACE\(year, '2018', 'thisyear'\)
* DECODE\(year, '2017', 'lastyear', '2018', 'thisyear', 'whocares'\)
* \(CASE WHEN year = '2017' THEN 'lastyear'  WHEN year = '2018' THEN 'thisyear'  ELSE 'whocares' END\) year





