## Layer-1:Physical layer(實體層)
### 實體層確保原始的資料可在各種物理媒體上傳輸，它用來定義網路裝置之間的位元資料傳輸，也就是在電線或其他物理線材上，傳遞0與1電子訊號，形成網路

#### 硬體: 集線器（Hub）、網路線、網路卡

攻擊
```
      攻擊方式:
              1.搭接線路(網路與電話)進行訊號竊聽
              2.私接線路變成隱匿通道(非控管中的線路)
      防護建議:
              1.機房、機櫃、線路室及管道間進行存取控管
              2.採用不同顏色區隔不同網段(安全區域)
              3.定期的線路盤查
```
## Layer-2:Data link layer(資料連結層)
### 資料連結層介於實體層與網路層之間，主要是在網路之間建立邏輯連結，並且在傳輸過程中處理流量控制及錯誤偵測，讓資料傳送與接收更穩定

#### TCP/IP:（Asynchronous Transfer Mode，ATM）、點對點協定（Point-to-Point Protocol，PPP）
#### 硬體: 網路交換器(Switch)

攻擊
```
一.
     攻擊手法:
       透過工具或軟體被動蒐集Collision Domain中的網路封包
  
      監聽工具:
              1.Sniffer
              2.MailSnarf
              3.URLSnarf
              4.WebSpy
              5.Tcpdump
              6.Windump
              7.Wireshark(Ethereal)
              8.Ettercap
              9.NetIntercept

      防護建議:
              1.採用加密連線(最佳方法)
              2.改用Switch
              3.網路線路的實體存取控制，避免搭接或私接問題
二.
ARP Spoofing
      是指攻擊者取得區域網路上的資料封包甚至篡改封包，可讓網路上特定電腦或所有電腦無法正常連線

              -又稱為ARP flooding、ARP poisoning或ARP Poison Routing
              -在Broadcast Domain下無法被動監聽其他電腦間連線封包
              -ARP Spoofing攻擊強迫偽冒其他IP，讓攻擊者有機會監測到其他電腦間的通訊
        
      攻擊手法:
              1.攻擊者使用ARP Broadcast封包告訴其他電腦，192.168.1.1的MAC是Attacker的MAC
              2其他電腦要傳送給192.168.1.1的封包會被送到Attacker
              3.Attacker將封包錄下後轉送到真正的192.168.1.1
 
      防護建議:
              1.強制使用靜態ARP Table(小型網路)
              2.採用VLAN縮小Broadcast Domain的範圍
              3.啟用Switch中的Port、MAC及IP的對應控管
______________________________________________________________________________________________________
與ARP Spoofing 相似的攻擊-IP Spoofing
  
  IP Spoofing:使用偽造的來源位址來傳送IP封包，可能會採用受信任來源的IP 位址來嘗試規避防火牆
```
## Layer-3:network layer(網路層)
### 網路層定義網路路由及定址功能，讓資料能夠在網路間傳遞

#### TCP/IP: IP
#### 硬體: 路由器(Router)、非對稱數位用戶線路路(ADSL)

攻擊
```
一.
Source Route
      攻擊手法:
              1.IP封包的路由通常是由Router所決定，啟用Source Route可以讓傳送者指定IP封包的傳送路徑
              2.攻擊者運用Source Route的功能進行來源IP的偽冒(IP Spoofing)
              3.讓偽冒來源IP的封包可照指定路徑送到目的伺服器
              4.FW信任偽冒的來源IP未加以阻擋
      防護建議:
              1.在防火牆或路由器上阻擋採用Source Route的封包
二.
Smurf Attack
      藉由Ping封包塞爆受害者網路頻寬的阻斷服務攻擊
      
      攻擊手法:
              1.攻擊者偽冒受害者IP發送大量回應請求(Echo Request)給B網段的廣播(Broadcast)IP位址 (B.255或B.0) 
                B網段所有電腦收到回應請求(Echo Request)封包，都回覆(Echo Reply)封包給Victim，導致Victim端頻寬被大量的回復(Echo Reply)封包所占用


      防護建議:
              1.在防火牆或路由器上阻擋Network/Broadcast IP的傳送

三.
Ping of Death
      屬於一種阻斷服務攻擊，只要一個Ping封包就讓作業系統當機
      
      攻擊手法:
              1.一般正常的Ping封包大小為56位元(含IP標頭為84位元)
              2.攻擊者故意傳送一個大小超過65536位元的Ping封包給受害者(IP協定允許封包大於65536)
              3.受害作業系統無法處理大於65536位元的Ping封包，導致系統當機或重新開機
              4.攻擊者的來源IP經常是偽冒的IP位址
      防護建議:
              1.修補作業系統弱點(目前大部份作業系統都已修補這個弱點)
```
## Layer-4:Transport layer(傳輸層)
### 傳輸層主要負責電腦整體的資料傳輸及控制，它可以將一個較大的資料切割成多個適合傳輸的資料，替模型頂端的第五、六、七等三個通訊層提供流量管制及錯誤控制

#### TCP/IP: TCP{具有三向交握(Three-way Handshake)安全速度較慢}、UDP(不安全速度較快)
攻擊
```
SYN Flood
      攻擊手法:
              1.攻擊者傳送大量的TCP SYN請求封包到受害伺服器
              2.受害伺服器為每一個連線請求分配系統記憶體資源，導致系統連線資源被耗用殆盡，正常的連線無法建立
              3.大量惡意的TCP SYN封包，其來源IP通常也都是偽冒的，因此無法以封鎖來源IP阻擋攻擊
      防護建議:
              1.防火牆限制同來源IP的連線數量
              2.請求ISP協助
```
## Layer-5:session layer(會議層)
### 這個層級負責建立網路連線，等到資料傳輸結束時，再將連線中斷，運作過程有點像召集多人開會（建立連線），然後彼此之間意見交換（資料傳輸），完成後，宣布散會（中斷連線）

#### TCP/IP: NetBIOS names、網路芳鄰(TCP 445)
```
```
## Layer-6:Presentation layer(表現層)
### 應用層收到的資料後，透過展示層可轉換表達方式，例如將ASCII編碼轉成應用層可以使用的資料，或是處理圖片及其他多媒體檔案，如JPGE圖片檔或MIDI音效檔

#### 功能: 轉檔 加密 解密
```
```
## Layer-7:Application layer(應用層)
### 應用層主要功能是處理應用程式，進而提供使用者網路應用服務

#### 不安全的協定:telnet(23) ftp(20/21) http(80) DNS(53)
#### 安全的協定:ssh(22) sftp(22?) https(443) DNSsec(53)
```
```
