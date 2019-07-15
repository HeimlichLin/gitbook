# git 建立新的 Repository 指令



name : git config --global user.name "jerry"  
mail : git config --global user.email "jerry791229@gamil.com"  
乎略空白 : git config --global apply.whitespace nowarn  
開啟顏色輸出 : git config --global color.ui true

建立一個新的 Repository -- Create a new repository  
複製別人的 Repository : git clone ssh://git@gitlab.intranet.com.tw:10022/PFTZB/PFTZB\_AP.git  
複製並改名為PFTZC  :  -- git clone ssh://git@gitlab.intranet.com.tw:10022/PFTZB/PFTZB\_AP.git PFTZC  
到該資料夾 : cd PFTZB\_AP  
新增README.md : touch README.md  
於本機加入至管控 : git add README.md  
於本機加入註記 : git commit -m "add README"  
合併回git的上server : git push -u origin master

到animal，並將他用git管理   
-- cd animal  
-- git init Initialized empty Git repository in c:/Users/xxxx/workspace/animal/.git/

現有的檔案建立一個新的 Repository -- Existing folder  
cd existing\_folder  
git init  
git remote add origin ssh://git@gitlab.intranet.com.tw:10022/PFTZB/PFTZB\_AP.git  
git add .  
git commit -m "Initial commit"  
git push -u origin master

現有的檔案建立一個新的 Repository -- Existing Git repository  
cd existing\_repo  
git remote rename origin old-origin  
git remote add origin ssh://git@gitlab.intranet.com.tw:10022/PFTZB/PFTZB\_AP.git  
git push -u origin --all  
git push -u origin --tags

