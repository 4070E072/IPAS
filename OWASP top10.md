# OWASP top 10
## OWASP（The Open Web Application Security Project ，開放網路應用程式安全專案）

1.Injection(注入): 
  
 網站應用程式執行來自外部包括資料庫在內的惡意指令，SQL Injection與Command Injection等攻擊包括在內。因為駭客必須猜測管理者所撰寫的方式，因此又稱「駭客的填空遊戲」。
 
舉例來說，原本管理者設計的登入頁面資料庫語法如下： 
 
  $str = "SELECT * FROM Users WHERE Username='“.$user."' and Password=‘”.$pass."'“; 
 
　如果說$user以及$pass變數沒有做保護，駭客只要輸入「’ or ‘‘=’」字串，就會變成以下： 
 
  $str = “SELECT * FROM Users WHERE Username='' or ''='' and Password= '' or ‘’=‘’”; 
 
  如此一來，這個SQL語法就會規避驗證手續，直接顯示資料。 
 
   簡述駭客攻擊流程：
```
        1.找出未保護變數，作為注入點
        2.猜測完整Command並嘗試插入
        3.推測欄位數、Table名稱、SQL版本等資訊
        4.完整插入完成攻擊程序 
```　
   防護建議：
```
        1.使用Prepared Statements，例如Java PreparedStatement()，.NET SqlCommand(), OleDbCommand()，PHP PDO bindParam()
        2.使用Stored Procedures
       3.嚴密的檢查所有輸入值
        4.使用過濾字串函數過濾非法的字元，例如mysql_real_escape_string、addslashes
       5.控管錯誤訊息只有管理者可以閱讀
       6.控管資料庫及網站使用者帳號權限為何
```

2. Broken Authentication(失效的身份驗證):
   
   1.攻擊者透過錯誤的使用者應用程式身份認證和會話管理功能，破解密碼、Session Token，或利用其它開發漏洞，暫時性或永久性冒充用戶身份。
   
   2.許多應用程式經常需要處理身分認證及Session管理，但導入方式若不正確，反而可能會讓駭客取得密碼、金鑰、Session令牌，或者是利用其他導入時的錯誤疏失，      暫時或永久取得使用者的身份資訊。
```
