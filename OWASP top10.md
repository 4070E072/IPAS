# OWASP top 10
## OWASP（The Open Web Application Security Project ，開放網路應用程式安全專案）

# 1.Injection(注入): 
  
 ## 網站應用程式執行來自外部包括資料庫在內的惡意指令，SQL Injection與Command Injection等攻擊包括在內。因為駭客必須猜測管理者所撰寫的方式，因此又稱「駭客的填空遊戲」。
 
  舉例來說，原本管理者設計的登入頁面資料庫語法如下： 
 ```
  $str = "SELECT * FROM Users WHERE Username='“.$user."' and Password=‘”.$pass."'“; 
 ```
　如果說$user以及$pass變數沒有做保護，駭客只要輸入「’ or ‘‘=’」字串，就會變成以下： 
 ```
  $str = “SELECT * FROM Users WHERE Username='' or ''='' and Password= '' or ‘’=‘’”; 
 ```
  如此一來，這個SQL語法就會規避驗證手續，直接顯示資料。 
 
   簡述駭客攻擊流程：

        1.找出未保護變數，作為注入點
        2.猜測完整Command並嘗試插入
        3.推測欄位數、Table名稱、SQL版本等資訊
        4.完整插入完成攻擊程序 
　
   防護建議：

        1.使用Prepared Statements，例如Java PreparedStatement()，.NET SqlCommand(), OleDbCommand()，PHP PDO bindParam()
        2.使用Stored Procedures
        3.嚴密的檢查所有輸入值
        4.使用過濾字串函數過濾非法的字元，例如mysql_real_escape_string、addslashes
        5.控管錯誤訊息只有管理者可以閱讀
        6.控管資料庫及網站使用者帳號權限為何


2. Broken Authentication（身分驗證功能缺失） 
 
　網站應用程式中自行撰寫的身分驗證相關功能有缺陷。例如，登入時無加密、SESSION無控管、Cookie未保護、密碼強度過弱等等。

　例如：  
 ```
　應用程式SESSION Timeout沒有設定。使用者在使用公用電腦登入後卻沒有登出，只是關閉視窗。攻擊者在經過一段時間之後使用同一台電腦，卻可以直接登入。 
 
　網站並沒有使用SSL / TLS加密，使用者在使用一般網路或者無線網路時，被攻擊者使用Sniffer竊聽取得User ID、密碼、SESSION ID等，進一步登入該帳號。
 
　這些都是身分驗證功能缺失的例子。 
 ```
　管理者必須做以下的檢查：
```
    1.所有的密碼、Session ID、以及其他資訊都有透過加密傳輸嗎？
    2.憑證都有經過加密或hash保護嗎？
    3.驗證資訊能被猜測到或被其他弱點修改嗎？
    4.Session ID是否在URL中暴露出來？
    5.Session ID是否有Timeout機制？
```    
  防護建議：

    1.使用完善的COOKIE / SESSION保護機制
    2.不允許外部SESSION
    3.登入及修改資訊頁面使用SSL加密
    4.設定完善的Timeout機制
    5.驗證密碼強度及密碼更換機制 

