# Trigger

### 組成

* 觸發事件：在何種情況下觸發Trigger，例如：INSERT，UPDATE，DELETE
* 觸發時間：觸發事件和Trigger時間關係，BEFORE，AFTER
* 觸發執行的動作：例如：INSERT，UPDATE，DELETE
* 觸發頻率：STATEMENT觸發一次，ROW每一行數據影響一次

```sql
create or replace trigger TGA_TEST
  after update OR delete 
on testmgr.test_year
REFERENCING NEW AS New OLD AS Old
FOR EACH ROW
BEGIN
   if updating then
        Insert Into testmgr.test_year_month (year, month, processstate)
                VALUES ( :OLD.year,:OLD.month,'UPDATE');
   elsif deleting then
        Insert Into testmgr.test_year_month (year, month, processstate)
                VALUES ( :OLD.year,:OLD.month,'DELETE');        
   end if;
   
   EXCEPTION
     WHEN OTHERS THEN
       RAISE;  
end TGA_TEST;
```

