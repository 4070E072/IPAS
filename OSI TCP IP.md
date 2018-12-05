## Layer-1:Physical layer(實體層)
### 實體層確保原始的資料可在各種物理媒體上傳輸，它用來定義網路裝置之間的位元資料傳輸，也就是在電線或其他物理線材上，傳遞0與1電子訊號，形成網路
```
硬體:集線器（Hub）、網路線、網路卡
```
## Layer-2:Data link layer(資料連結層)
### 資料連結層介於實體層與網路層之間，主要是在網路之間建立邏輯連結，並且在傳輸過程中處理流量控制及錯誤偵測，讓資料傳送與接收更穩定
```
TCP/IP:（Asynchronous Transfer Mode，ATM）、點對點協定（Point-to-Point Protocol，PPP）
硬體: 網路交換器(Switch)
```
## Layer-3:network layer(網路層)
### 網路層定義網路路由及定址功能，讓資料能夠在網路間傳遞
```
TCP/IP:IP
硬體: 路由器(Router)、非對稱數位用戶線路路(ADSL)
```
## Layer-4:Transport layer(傳輸層)
### 傳輸層主要負責電腦整體的資料傳輸及控制，它可以將一個較大的資料切割成多個適合傳輸的資料，替模型頂端的第五、六、七等三個通訊層提供流量管制及錯誤控制
```
TCP/IP: TCP{具有三向交握(Three-way Handshake)安全速度較慢}、UDP(不安全速度較快)
```
## Layer-5:session layer(會議層)
### 這個層級負責建立網路連線，等到資料傳輸結束時，再將連線中斷，運作過程有點像召集多人開會（建立連線），然後彼此之間意見交換（資料傳輸），完成後，宣布散會（中斷連線）
```
TCP/IP: NetBIOS names、網路芳鄰(TCP 445)
```
## Layer-6:Presentation layer(表現層)
### 應用層收到的資料後，透過展示層可轉換表達方式，例如將ASCII編碼轉成應用層可以使用的資料，或是處理圖片及其他多媒體檔案，如JPGE圖片檔或MIDI音效檔
```
功能: 轉檔 加密 解密
```
## Layer-7:Application layer(應用層)
### 應用層主要功能是處理應用程式，進而提供使用者網路應用服務
```
不安全的協定:telnet(23) ftp(20/21) http(80) DNS(53)
安全的協定:ssh(22) sftp(22?) https(443) DNSsec(53)
```
