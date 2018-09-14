# Stored Procedures

### 組成

* Package： 像JAVA的Package， 用來區隔相同名稱的 Stored Procedure 或是 Function
* Procedure：沒有回傳值
* Function：有回傳值

#### 官網的範例

```sql
-- 定義 PACKAGE
CREATE OR REPLACE PACKAGE TEST_PACKAGE
AS
   -- 宣告 PROCEDURE 與 FUNCTION
   PROCEDURE TEST_PROCEDURE(TEST_PROCEDURE_ID IN NUMBER);
   FUNCTION TEST_FUNCTION(TEST_FUNCTION_ID  IN NUMBER) RETURN NUMBER;
END TEST_PACKAGE;

-- PACKAGE 的實作內容
CREATE OR REPLACE PACKAGE BODY TEST_PACKAGE
AS
   -- PROCEDURE 的實作內容
   PROCEDURE TEST_PROCEDURE(TEST_PROCEDURE_ID IN NUMBER)
   AS
   BEGIN
       -- 實作
       NULL;
   END TEST_PROCEDURE;
  
   --FUNCTION 的實作內容
   FUNCTION TEST_FUNCTION(TEST_FUNCTION_ID  IN NUMBER) RETURN NUMBER
   AS
   BEGIN
       --實作
       RETURN NULL;
   END TEST_FUNCTION;
END TEST_PACKAGE;
```

### Procedure and Function

* 宣告部份： DECLARE」， 定義變數與常數
* 執行部份：「BEGIN」與「END」， 程式執行
* 外處理部份：「EXCEPTION」， 處理程式中可能會發生的錯誤

#### 隨手寫個Procedure示意

```sql
CREATE OR REPLACE PROCEDURE PROC_TEST(
    -- 傳入參數
    IN_STRING IN VARCHAR2,
    IN_NUM IN NUMBER,
    -- 回傳參數
    OUT_STRING OUT VARCHAR2,
    OUT_NUM OUT NUMBER
)
IS
    -- 內部接收參數
    i_string VARCHAR2(50);
    i_num NUMBER;
    
    id VARCHAR2(30);
    num NUMBER;
    
    -- 共用方法
    CURSOR W1 IS
    SELECT id, num
    FROM table_a;
    
BEGIN
    OUT_STRING := '成功';
    OUT_NUM := 1;
    
    BEGIN
    i_string := LTRIM(RTRIM(IN_STRING, ' '), ' ');
    i_num := LTRIM(RTRIM(IN_NUM, ' '), ' ');
    
    EXCEPTION
        WHEN OTHERS THEN
          OUT_STRING := '參數異常';
          OUT_NUM := -1;
          GOTO STOP_PRG;
    END;
    
    IF (i_string IS NULL) THEN
        OUT_STRING := '空值';
        OUT_NUM := 0;
    ELSIF (i_string = 'GO') THEN
        OPEN W1;
          LOOP
            FETCH W1 INTO id, num;
            EXIT WHEN W1%NOTFOUND;
               DELETE FROM table_b WHERE ID = id AND NUM = num;
            COMMIT;
          END LOOP;
          CLOSE W1;
    ELSE
        OUT_STRING := i_string;
        OUT_NUM := i_num;
        INSERT INTO log_table (datetime, error)
        VALUES (SYSDATE, '沒有這選項');
    END IF;
    
    << STOP_PRG >>
    DBMS_OUTPUT.PUT_LINE('err1:'|| OUT_STRING);
    DBMS_OUTPUT.PUT_LINE('err2:'|| OUT_NUM);
    DBMS_OUTPUT.PUT_LINE('err3:'|| '程式異常');
END PROC_TEST;
    
```

### 流程控制

* IF...CASE
* WHILE…LOOP
* LOOP…EXIT WHEN

