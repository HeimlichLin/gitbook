# 基本指令

歷程檔案： .git/object  
branch紀錄： .git/ref

看該檔案的類型： git cat-file -t ssh檔名  
看該檔案的大小： git cat-file -s ssh檔名  
看該檔案清單： git cat-file -e ssh檔名  
看該檔案的內容： git cat-file -p ssh檔名

加入git： git init  
1.txt加入add： git add 1.txt  
此路徑下所有檔案加入add： git add.

加入commit： git commit 1.txt  
加入commit與log： git commit -m "log註記"  
修改最後一次的註記： git commit --amend -m "修改後的log註記"

看歷年動作:切換分支、commit等： git reflog

看檔案清單： git ls-files -s

備份到已存在的分支： git checkout  
備份並新增branch dev： git checkout -b dev  
備份並新增branch backup，當作備份版本： git checkout -b backup  
切換並切換至指定的commit版本： git checkout –b  

看現階段branch指向： git branch  
git branch tiger ssh檔名，建立分支tiger \(分支指向某個commit\)： git branch tiger  
分支tiger改名為cat： git branch -m tiger cat  
刪除分支cat： git branch -d cat

要有編輯器vim才能使用，可以直接在檔案.gitignore中添加要排除的檔案，ex:log/_.log。\(_不希望加入版控的檔案可以在.gitignore加入，讓git忽略\)  
_vim .gitignore  
log/_.log

透過git global 裡的config增加alias，改變你想要的git指令： vim ~/.gitconfig

更改默認的編輯器： git config --global core.editor "notepad"

退出預設編輯器： 按esc 輸入:wq 按enter or 按esc 輸入\(sfitt\)+Z \(sfitt\)+Z 兩次

