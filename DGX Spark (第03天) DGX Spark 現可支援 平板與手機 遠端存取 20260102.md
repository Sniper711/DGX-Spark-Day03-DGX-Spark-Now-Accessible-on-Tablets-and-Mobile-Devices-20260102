<sub><sup>這是我前幾篇文章 DGX Spark : [第01天A: 外網遠端操控 指南](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9A)%20%E5%A4%96%E7%B6%B2%E9%81%A0%E7%AB%AF%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220A.md) 與 [第01天B: 同子網內網操控 指南](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9B)%EF%BC%9A%E5%90%8C%E5%AD%90%E7%B6%B2%E5%85%A7%E7%B6%B2%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220B.md) 兩種 Server/Client 連線方式，以及 [第02天: 用 Open WebUI 介面 遠端操作 DGX Spark 上的 Ollama](https://github.com/Sniper711/DGX-Spark-Day02-Open-WebUI-with-Ollama-on-Remote-Spark-20251226/blob/main/DGX%20Spark%20(%E7%AC%AC02%E5%A4%A9)%20%E7%94%A8%20Open%20WebUI%20%E4%BB%8B%E9%9D%A2%20%E9%81%A0%E7%AB%AF%E6%93%8D%E4%BD%9C%20DGX%20Spark%20%E4%B8%8A%E7%9A%84%20Ollama%2020251226.md)的延伸文章。以下，我將繼續把 Clients 從 Mac/PC 拓展到 Android/iOS 平板與手機，以大幅提高生產力。希望能給你更多方式參考。</sup></sub>
![Tablets and phones](https://github.com/user-attachments/assets/70810f41-f032-4e81-b67d-72965c07eafa)

# DGX Spark (第03天) DGX Spark 現可支援所有 平板與手機 遠端存取 20260102
## 🟩 中文版
> ## 適用情境 與 優點
> **安卓/蘋果 平板與手機 Clients 開瀏覽器在 Open WebUI 介面上 → 透過自己建立的遠端連線 → 用 DGX Spark Server 的算力跑 Ollama**
> - DGX Spark 現可支援任何 **平板與手機** 遠端存取 (不只有 Mac/PC Client)
>   - 隨時隨地跑 Ollama，大幅提高生產力
>   - 用 `WireGuard` 與 `Termius` APPs
> - **基於前幾篇文章 [第01天A: 外網遠端操控 指南](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9A)%20%E5%A4%96%E7%B6%B2%E9%81%A0%E7%AB%AF%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220A.md) 與 [第01天B: 同子網內網操控 指南](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9B)%EF%BC%9A%E5%90%8C%E5%AD%90%E7%B6%B2%E5%85%A7%E7%B6%B2%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220B.md) 的兩種連線方式，以及 [第02天: 用 Open WebUI 介面 遠端操作 DGX Spark 上的 Ollama](https://github.com/Sniper711/DGX-Spark-Day02-Open-WebUI-with-Ollama-on-Remote-Spark-20251226/blob/main/DGX%20Spark%20(%E7%AC%AC02%E5%A4%A9)%20%E7%94%A8%20Open%20WebUI%20%E4%BB%8B%E9%9D%A2%20%E9%81%A0%E7%AB%AF%E6%93%8D%E4%BD%9C%20DGX%20Spark%20%E4%B8%8A%E7%9A%84%20Ollama%2020251226.md)**
>   - **100% 連線成功率與穩定度，自己掌握 Server/Client 連線的設定細節**
>   - 不使用 NVIDIA SYNC app 的連線方式
> - **重開機之後**
>   - 只要在 平板與手機 Clients 上，依序啟動 `WireGuard` 與 `Termius` APPs，再 瀏覽 `Ollama 服務網址`，超級簡單。 

---

## 目錄 Table of Contents

- [在平板與手機 安裝並設定 WireGuard APP：](#在平板與手機-安裝並設定-wireguard-app)
  - [Step 1. 從 Store 下載安裝 WireGuard APP](#step-1-從-store-下載安裝-wireguard-app)
  - [Step 2. 設定 WireGuard APP](#step-2-設定-wireguard-app)
    - [Step 2A. 若你的 Mac/PC Client 的 WireGuard Client 版本，能以 QR code 匯出設定，最簡單](#step-2a-若你的-macpc-client-的-wireguard-client-版本能以-qr-code-匯出設定最簡單)
    - [Step 2B. 若你的 Mac/PC Client 的 WireGuard Client 版本，不能以 QR code 匯出設定，那就一步步輸入](#step-2b-若你的-macpc-client-的-wireguard-client-版本不能以-qr-code-匯出設定那就一步步輸入)
  - [Step 3. 測試安卓/蘋果 平板與手機 的 WireGuard Client 連線](#step-3-測試安卓蘋果-平板與手機-的-wireguard-client-連線)

- [在平板與手機 安裝並設定 Termius APP：](#在平板與手機-安裝並設定-termius-app)
  - [Step 1. 從 Store 下載安裝 Termius APP](#step-1-從-store-下載安裝-termius-app)
  - [Step 2. 設定 Termius APP 的 Hosts 功能](#step-2-設定-termius-app-的-hosts-功能)
  - [Step 3. 設定 Termius APP 的 Forwarding 功能](#step-3-設定-termius-app-的-forwarding-功能)

- [在平板與手機 依序啟動 WireGuard 與 Termius 服務，再 瀏覽 Ollama 服務網址：](#在平板與手機-依序啟動-wireguard-與-termius-服務再-瀏覽-ollama-服務網址)
  - [Step 1. 先啟動 WireGuard，建立VPN通道](#step-1-先啟動-wireguard建立VPN通道)
  - [Step 2. 再啟動 Termius，SSH 建立 Host 連線 並 設立 Ollama 服務專用的 Port Forwarding 規則](#step-2-再啟動-termius-ssh-建立-host-連線-並-設立-ollama-服務專用的-port-forwarding-規則)
  - [Step 3. 瀏覽 Ollama 服務網址 http://localhost:12000](#step-3-瀏覽-ollama-服務網址-httplocalhost12000)

---

## 在平板與手機 安裝並設定 `WireGuard` APP：

### Step 1. 從 Store 下載安裝 `WireGuard` APP
### Step 2. 設定 `WireGuard` APP 
(分兩種情況，Step 2A 與 Step 2B)
#### Step 2A. 若你的 Mac/PC Client 的 WireGuard Client 版本，能以 QR code 匯出設定，最簡單：
- Step 2A-1. 打開平板與手機 `WireGuard` APP
- Step 2A-2. 按左下角 `+` 號，選  `掃描 QR code`
- Step 2A-3. 掃描 Mac/PC Client 的 WireGuard Client 顯示出的 QR code，完成設定。
#### Step-2B 若你的 Mac/PC Client 的 WireGuard Client 版本，不能以 QR code 匯出設定，那就一步步輸入：
- Step 2B-1. 打開平板與手機 `WireGuard` APP
- Step 2B-2. 按左下角 `+` 號，選  `從空白開始建立`
- Step 2B-3. 剛開始看見 介面端設定，填寫如下：
  - 名稱：        **填Server VPN名稱，我的範例是 `DGXSparkVPN`**
  - 私鑰：        **填 (第01天A) 文章的 Client PrivateKey**
  - 公鑰：        **不用填寫**。會自動算出 Client PublicKey
  - 位址：        **填 'WireGuard Client 在 VPN 內的固定 IP'，在(第01天A) 文章的範例是 10.0.0.2/32** 
  - 監聽連接埠：   **不用填寫** 
  - DNS伺服器：   **填 (第01天A) 文章的 168.95.192.1,8.8.8.8，或改成你國家最常用的DNS伺服器**
  - 最大傳輸單元： **不用填寫**
  - 按 `套用到所有應用程式`，決定 套用或排除 WireGuard VPN 的 APPs
  - 最後按 中間下方 `新增端點`，繼續展開 用戶端設定，填寫如下：
    - 公鑰：      **填 (第01天A) 文章的 Server PublicKey**
    - 預分享金鑰： **不用填寫**
    - 保持連線：   **填 (第01天A) 文章的 25**。這是Keepalive秒數。
    - 終端點：     **填 (第01天A) 文章的 <DGX_SPARK_PUBLIC_IP>:51820**。其中，請把<DGX_SPARK_PUBLIC_IP>換成Server的固定IP
    - 允許IP：    **填 0.0.0.0/0**。所有流量均經過 VPN 隧道。
    - 最後按 右上方 `磁碟圖案`，存檔，完成設定。
### Step 3. 測試安卓/蘋果 平板與手機 的 WireGuard Client 連線：
在 DGX Spark 的 WireGuard Server 已開機情形下
- Step 3-1. 在平板與手機 WireGuard APP找到剛設定好的連線 (我的範例是**`DGXSparkVPN`**)，按下去。
- Step 3-2. 若VPN建立成功。平板與手機 WireGuard APP 內會開始顯示已連線時長的讀秒，且平板與手機右上角會出現一隻鑰匙圖案。

--- 

## 在平板與手機 安裝並設定 `Termius` APP：

### Step 1. 從 Store 下載安裝 `Termius` APP
### Step 2. 設定 `Termius` APP 的 Hosts 功能：
- Step 2-1. 開啟 `Termius` APP，畫面左側此時是按下 `Hosts` 選單。畫面中央顯示文字 `Create host. Save your connection details as hosts to connect in one click. 請你填寫 _____ (Type IP address or hostname)`.
  - 填 (第01天A) 文章的 `<DGX_SPARK_PUBLIC_IP>`，其中，請把<DGX_SPARK_PUBLIC_IP>換成Server的固定IP.
- Step 2-2. 此時畫面出現右邊設定欄位，我們一步步輸入 Hosts 設定資料：
  - Alias： **填Server Host名稱或暱稱，我的範例是 `DGX Spark Host`**
  - Hostname or IP Address：**填 (第01天A) 文章的 <DGX_SPARK_PUBLIC_IP>**。其中，請把<DGX_SPARK_PUBLIC_IP>換成Server的固定IP.
  - Group： **不用填寫**
  - Tags： **不用填寫**
  - Delete sends Ctrl-H： **不用改** 預設是不打勾。
  - SSH： **不用改** 預設是打勾。
  - Mosh： **不用改** 預設是不打勾。
  - Port： **不用改** 預設是22。
  - Credentials：
    - Username： **填 `你的 DGX Spark 開機登入用戶名`**
    - Password： **填 `你的 DGX Spark 開機登入密碼`**
    - 這行以下其他所有的欄位資料都不要改。
    - 最後按右上角 `(打勾符號) Save` 保存。
- Step 2-3. 測試 `Termius` APP 的 Hosts 功能：
  - 開啟 `Termius` APP，左邊選單按下 `Hosts` 按鈕，接著按下剛建立的 Host 名稱按鈕(我的範例是 `DGX Spark Host`)，應看到能成功SSH連線且按鈕底下底下出現小字 `Active`。
### Step 3. 設定 `Termius` APP 的 Forwarding 功能：
- Step 3-1. 開啟 `Termius` APP，此時在主畫面左側按下 `Forwarding` 選單。畫面中央顯示文字 Set up port forwarding. Save port forwarding to access databases, web apps, and other services，與右下方一個 `+` 按鈕。此時，請 **按下 `+` 按鈕**。
- Step 3-2. 此時畫面出現右邊設定欄位，我們一步步輸入 Forwarding 設定資料：
  - 先按下 `Continue`
  - 下一頁是 `Set the local port. This port will be open on the local (current) machine to forward traffic to the remote host.' 請你填寫 Port number : _____, 與 Bind address (optional) : _____.`
    - 前者 **填 `12000`**。依照 (第02天) 文章 Client 這邊的通信埠 設在 12000**
    - 後者 **不用填寫**，按 `Continue`
  - 再按下 `Select a host`，此時畫面右邊顯示剛建立的 Host 名稱按鈕(我的範例是 `DGX Spark Host`)，按下去。
  - 下一頁是 `Set the destination, IP address/hostname and the port number of the remote host where the intermediate host will direct the traffic. Destination address : _____, Destination port : _____.`
    - 前者 **填 `0.0.0.0`**。依照 (第02天) 文章 設在 0.0.0.0**
    - 後者 **填 `3000`**。依照 (第02天) 文章 Server 的通信埠 設在 3000**，按 `Continue`
  - 下一頁是 `Set the label. Label: _____.` 這是給這個 Port Forwarding 服務貼一個標籤。(Server 需要開許多不同的 Port Forwarding，因為 Server 有許多服務，例如 Ollama, Jupyter, ComfyUI....)，我建議填 `Ollama 12000:3000`，說明 服務名與兩端的服務埠，以後加更多服務時能一目瞭然。按下 `Done` 按鈕。
  - 最後按 `右上角打勾圖案 (Save)` 保存。
- Step 3-3. 測試 `Termius` APP 的 Forwarding 功能：
  - 開啟 `Termius` APP，左邊選單按下 `Forwarding` 按鈕，接著按下剛建立的 Forwarding 名稱 灰色按鈕(我的範例是 `Ollama 12000:3000`)，若(且唯若) 灰色按鈕`變成藍色按鈕`表示 測試成功。
    - 重要! 若 灰色按鈕`變成綠色勾勾` 表示仍嘗試連線中，沒有成功也沒有失敗，請稍後。**綠勾勾不是連線成功**，可能因為網路延遲需等待，或請稍後再連一次。) (這裡容易誤解綠色勾勾按鈕的狀態) (直到 灰色按鈕變成藍色按鈕 才算成功)

--- 

## 在平板與手機 依序啟動 `WireGuard` 與 `Termius` 服務，再 瀏覽 `Ollama 服務網址`：

### Step 1. 先啟動 `WireGuard`，建立VPN通道
- 開啟 `WireGuard` APP，按剛建立的 Server VPN 名稱按鈕(我的範例是 `DGXSparkVPN`) 即成功連線。註：若再按第二下，畫面右邊會跳出顯示已成功連線秒數的計時器。
### Step 2. 再啟動 `Termius`， SSH 建立 Host 連線 並 設立 Ollama 服務專用的 Port Forwarding 規則
- Step 2-1. 開啟 `Termius` APP，左邊選單按下 `Hosts` 按鈕，接著按下剛建立的 Host 名稱按鈕(我的範例是 `DGX Spark Host`)，應看到能成功SSH連線且按鈕底下底下出現小字 `Active`。
- Step 2-2. 開啟 `Termius` APP，左邊選單按下 `Forwarding` 按鈕，接著按下剛建立的 Forwarding 名稱 灰色按鈕(我的範例是 `Ollama 12000:3000`)，若(且唯若) 灰色按鈕`變成藍色按鈕`表示 測試成功。
  - 重要! 若 灰色按鈕`變成綠色勾勾` 表示仍嘗試連線中，沒有成功也沒有失敗，請稍後。**綠勾勾不是連線成功**，可能因為網路延遲需等待，或請稍後再連一次。) (這裡容易誤解綠色勾勾按鈕的狀態) (直到 灰色按鈕變成藍色按鈕 才算成功)
### Step 3. 瀏覽 `Ollama 服務網址 http://localhost:12000`

---

# **恭喜你！從此你能在平板與手機隨時隨地，用 DGX Spark 的 GPU 算力，開網頁跑 Ollama 了！**
<sub><sup>＊重開機之後，只要在 平板與手機 Clients 上，依序啟動 `WireGuard` 與 `Termius` APPs，再 瀏覽 `Ollama 服務網址`，超級簡單。</sup></sub>

---
