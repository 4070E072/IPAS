----------------------------------------------------------------------------------
# 簡述駭客攻擊流程：
```
1.找出未保護變數，作為注入點
2.猜測完整Command並嘗試插入
3.推測欄位數、Table名稱、SQL版本等資訊
4.完整插入完成攻擊程序 
```
# 防護建議：
```
1.使用Prepared Statements，例如Java PreparedStatement()，.NET SqlCommand(), OleDbCommand()，PHP PDO bindParam()
2.使用Stored Procedures
3.嚴密的檢查所有輸入值
4.使用過濾字串函數過濾非法的字元，例如mysql_real_escape_string、addslashes
5.控管錯誤訊息只有管理者可以閱讀
6.控管資料庫及網站使用者帳號權限為何
```
2.Broken Authentication: 
