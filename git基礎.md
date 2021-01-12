# git/github基礎

## git/github是什麼？
git是一個版本控制系統，而github則是以git為核心技術基礎的雲端版本控制服務平台
開發一個軟體通常是由很多個工程師一起合作完成，軟體由很多檔案組成，git可以把檔案的狀態作為更新歷史記錄保存起來，因此可以把編輯過的檔案復原到以前的狀態，也可以顯示編輯過內容的差異。為了能更好的讓不同工程師管理檔案而使用git。

## git的數據庫
數據庫 (Repository) 是記錄檔案或目錄狀態的地方，可以記錄各版本的差異。數據庫分為遠端數據庫和本地端數據庫。
遠端數據庫：可以讓很多人一起使用的而建立的數據庫
本地端數據庫：在自己的機器上，方便個人使用的數據庫。

## 註冊帳號與連結帳號
請先到github的官網註冊一組github帳號吧！[github](https://github.com/)  
註冊好之後，需要設定git的使用者名稱和信箱，在進行程式碼的版本更新時，git會紀錄修改者是誰，因此需要登錄你的 name 和 email  
**指令：  
git config --global user.name "your name"  
git config --global user.email "your email"**  
可以使用指令確認輸入資料是否正確
**指令：git config --list**

## 流程
 * 首先在要在目標目錄裡建立數據庫。沒有目錄的話請先新增一個目錄。
 **指令：git init**
 * 將編輯好的檔案加入到索引
 **指令：git add .**(將全部檔案加入索引)
 **指令：git add 檔名**(將該檔案加入索引)
 * 透過指令可以提交新的版本。
 **指令：git commit -m "名稱"**
 * 提交新版本之後 可以查詢版本。
 **指令：git log**
 * 更新遠端數據庫資料
 **指令：git push <數據庫簡稱> <分支名稱>**(這裡終於了解老師上課常用的git push origin master是什麼意思了！)

 
## 其他常用指令
 * 顯示修改的檔案有哪些
 **指令：git status**
 * 查看修改檔案的差異
 **指令：git diff**
 * 修改/移動一個檔案/目錄的名稱
 **指令：git mv <舊檔名> <新檔名>**
 * 刪除檔案
  **指令：git rm <檔案>**
  * 還原在工作目錄已更改的檔案
  **指令：git checkout -- <檔案>**
  * 克隆遠端數據庫
  **指令：git clone <網址>**
  * 從遠端數據庫下載最新的檔案版本，同步到自己的本地端數據庫。
  **指令：git pull 或git pull origin master**(更新老師上課的教材也常用這個指令！)
  
  
  
  
  
  
  參考資料：  
  https://backlog.com/git-tutorial/tw/intro/intro4_4.html  
  https://w3c.hexschool.com/git/7b64aa34  
  https://w3c.hexschool.com/git/b9be5b1e  
  https://tw.alphacamp.co/blog/git-github-version-control-guide
  
 ## Master、Branch和Merge
 Master是專案的主要版本，Branch是專案的分支版本，Merge則是把兩個不同的分支版本，合併到其中一個分支上。
 通常在Master上開發主要功能，並在Master分出去的Branch上開發副功能。當某個Branch的功能已經開發完整時，要把Branch上的功能套回Master上，就會執行Merge，把Branch的版本合併回Master上。  
 使用branch指令：  
 * **git branch**：git branch後面不加參數，可以查詢目前在這個專案有哪些Branch。預設會設定一個叫master的分支。
 * **git branch test**：增加一個名叫test的Branch。
 * **git branch -m 舊Branch名 新Branch名**：更改Branch名稱
 * **git branch -d Branch名**：刪除Branch(用 -D 參數可以強制刪除)
 * **git checkout Branch名**：切換Branch(前面'*'表示目前Branch)
 
 
 
 
