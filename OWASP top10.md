# OWASP top 10
## OWASP（The Open Web Application Security Project ，開放網路應用程式安全專案）
```
1.Injection: Injection 發生，通常是使用者提供的資料傳輸到interpreter， 被當成指令或是查詢。
  攻擊者就能用惡意的資料欺騙 interpreter，達到執行指令或竄改資料目的

例如:
$str = "SELECT * FROM Users WHERE Username='“.$user."' and Password=‘”.$pass."'“;

如果說$user以及$pass變數沒有做保護，駭客只要輸入「’ or ‘‘=’」字串，就會變成以下：

$str = “SELECT * FROM Users WHERE Username='' or ''='' and Password= '' or ‘’=‘’”; 

這樣就會直接顯示資料庫的內容
```
