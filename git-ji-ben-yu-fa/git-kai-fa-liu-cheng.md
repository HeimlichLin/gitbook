# git 開發流程

GITLAB FLOW  
1. master\(主線\)   
2. develop/feautre/hotfix\(用員工名稱\(不用git push\)\)   
3. r\_sit\(測試環境\)   
4. r\_uat\(驗證環境\)

開發新功能流程步驟   
1. git checkout master   
2. git pull origin master   
3. git checkout \[員工編號\(develop\)\]   
4. git -rebase \[員工編號\(develop\)\]

進行開發....   
1. git commit -m 'feature/XXXX"   
2. git checkout master   
3. git pull origin master   
4. git merge develop   
5. git push -u origin master

每日更新流程   
1. git checkout master   
2. git pull origin master   
3. git checkout 6284 \[員工編號\(develop\)\]   
4. git merge master   
5. git checkout 6284 6. pause

繼續開發 Deploy至MASTER環境   
1. git checkout master   
2. git pull origin master  
3. git merge 6284  
4. git push -u origin master  
5. git checkout 6284  
6. pause

Deploy至SIT環境   
1. git checkout r\_sit   
2. git pull origin r\_sit   
3. git merge master   
4. git push -u origin r\_sit   
5. git checkout 6284  
6. pause

Deploy至UAT環境   
1. git checkout r\_uat   
2. git pull origin r\_uat   
3. git merge master   
4. git push -u origin r\_uat   
5. git checkout 6284  
6. pause

Deploy營運   
1. git checkout master   
2. git pull origin master   
3. git tag -l '版號'   
4. git push -u origin master   
5. 填寫系統變更單 填寫標籤

緊急變更   
1. git checkout master   
2. git checkout 'hotfix/日期'   
3. 修改程式   
4. git commit -m 'hotfix/日期 修改xXXXXX'   
5. git checkout master   
6. git merge hotfix/日期   
7. git tag -l '版號'   
8. git push -u origin master

