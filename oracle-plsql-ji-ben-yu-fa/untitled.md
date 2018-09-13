# Trigger

```text
create or replace trigger TGA_FOSP_QUEOPERATEYEAR
  after update OR delete 
on pfospmgr.fosp_queoperateyear
REFERENCING NEW AS New OLD AS Old
FOR EACH ROW
BEGIN
   if updating then
        Insert Into pfospmgr.fosp_queoperateyear_h (year, month, bondno, ftzmode, prodnotemain, prodnotesec, ftzemploynum, totalemploynum, landarea, buildarea, totalrev, oprev, unoprev, totalcost, salarycost, depcost, taxcost, purchasecost, rentcost, othercost, opmode, transpercent, logipercent, pluspercent, fixpercent, trandepercent, exhibitpercent, otherpercent, othernote, netassets, fixassetscost, advancenote, filluser, fillusertit, fillusertel, filluserfax, filluseremail, createdate, createuserid, confflag, confuserid, confdate, confdesc, dealflag, dealdate, easyprocecode, easyprocedesc, easyprocepercent, easyproceqty, easyprocevalue, returndesc, updatetime, processstate)
                VALUES ( :OLD.year,:OLD.month,:OLD.bondno,:OLD.ftzmode,:OLD.prodnotemain,:OLD.prodnotesec,:OLD.ftzemploynum,:OLD.totalemploynum,:OLD.landarea,:OLD.buildarea,:OLD.totalrev,:OLD.oprev,:OLD.unoprev,:OLD.totalcost,:OLD.salarycost,:OLD.depcost,:OLD.taxcost,:OLD.purchasecost,:OLD.rentcost,:OLD.othercost,:OLD.opmode,:OLD.transpercent,:OLD.logipercent,:OLD.pluspercent,:OLD.fixpercent,:OLD.trandepercent,:OLD.exhibitpercent,:OLD.otherpercent,:OLD.othernote,:OLD.netassets,:OLD.fixassetscost,:OLD.advancenote,:OLD.filluser,:OLD.fillusertit,:OLD.fillusertel,:OLD.filluserfax,:OLD.filluseremail,:OLD.createdate,:OLD.createuserid,:OLD.confflag,:OLD.confuserid,:OLD.confdate,:OLD.confdesc,:OLD.dealflag,:OLD.dealdate,:OLD.easyprocecode,:OLD.easyprocedesc,:OLD.easyprocepercent,:OLD.easyproceqty,:OLD.easyprocevalue,:OLD.returndesc
                ,to_char(sysdate,'YYYYMMDDHH24MISS'),'UPDATE');
   elsif deleting then
        Insert Into pfospmgr.fosp_queoperateyear_h (year, month, bondno, ftzmode, prodnotemain, prodnotesec, ftzemploynum, totalemploynum, landarea, buildarea, totalrev, oprev, unoprev, totalcost, salarycost, depcost, taxcost, purchasecost, rentcost, othercost, opmode, transpercent, logipercent, pluspercent, fixpercent, trandepercent, exhibitpercent, otherpercent, othernote, netassets, fixassetscost, advancenote, filluser, fillusertit, fillusertel, filluserfax, filluseremail, createdate, createuserid, confflag, confuserid, confdate, confdesc, dealflag, dealdate, easyprocecode, easyprocedesc, easyprocepercent, easyproceqty, easyprocevalue, returndesc, updatetime, processstate)
                VALUES ( :OLD.year,:OLD.month,:OLD.bondno,:OLD.ftzmode,:OLD.prodnotemain,:OLD.prodnotesec,:OLD.ftzemploynum,:OLD.totalemploynum,:OLD.landarea,:OLD.buildarea,:OLD.totalrev,:OLD.oprev,:OLD.unoprev,:OLD.totalcost,:OLD.salarycost,:OLD.depcost,:OLD.taxcost,:OLD.purchasecost,:OLD.rentcost,:OLD.othercost,:OLD.opmode,:OLD.transpercent,:OLD.logipercent,:OLD.pluspercent,:OLD.fixpercent,:OLD.trandepercent,:OLD.exhibitpercent,:OLD.otherpercent,:OLD.othernote,:OLD.netassets,:OLD.fixassetscost,:OLD.advancenote,:OLD.filluser,:OLD.fillusertit,:OLD.fillusertel,:OLD.filluserfax,:OLD.filluseremail,:OLD.createdate,:OLD.createuserid,:OLD.confflag,:OLD.confuserid,:OLD.confdate,:OLD.confdesc,:OLD.dealflag,:OLD.dealdate,:OLD.easyprocecode,:OLD.easyprocedesc,:OLD.easyprocepercent,:OLD.easyproceqty,:OLD.easyprocevalue,:OLD.returndesc
                ,to_char(sysdate,'YYYYMMDDHH24MISS'),'DELETE');
   end if;
   
   EXCEPTION
     WHEN OTHERS THEN
       RAISE;  
end TGA_FOSP_QUEOPERATEYEAR;
```

