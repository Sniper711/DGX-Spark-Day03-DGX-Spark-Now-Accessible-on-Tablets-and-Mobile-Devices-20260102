<sub><sup>This is an extension of my previous articles on the two Server/Client connection methods for DGX Spark: [Day01A: Remote Access from Internet Guide](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(Day01A)%20Remote%20Access%20from%20Internet%20Guide%2020251220A.md) and [Day01B: Local Access from Same Subnet Guide](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(Day01B)%EF%BC%9ALocal%20Access%20from%20Same%20Subnet%20Guide%2020251220B.md), and the article [Day02: Open WebUI with Ollama on Remote Spark](https://github.com/Sniper711/DGX-Spark-Day02-Open-WebUI-with-Ollama-on-Remote-Spark-20251226/blob/main/DGX%20Spark%20(Day02)%20Open%20WebUI%20with%20Ollama%20on%20Remote%20Spark%2020251226.md) **Here, I'll expand support from Mac/PC Clients to Android/iOS Tablet Clients**, to significantly boost your productivity. I hope this gives you more options for reference.</sup></sub> 

<sub><sup>這是我前幾篇文章 DGX Spark : [第01天A: 外網遠端操控 指南](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9A)%20%E5%A4%96%E7%B6%B2%E9%81%A0%E7%AB%AF%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220A.md) 與 [第01天B: 同子網內網操控 指南](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9B)%EF%BC%9A%E5%90%8C%E5%AD%90%E7%B6%B2%E5%85%A7%E7%B6%B2%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220B.md) 兩種 Server/Client 連線方式，以及 [第02天: 用 Open WebUI 介面 遠端操作 DGX Spark 上的 Ollama](https://github.com/Sniper711/DGX-Spark-Day02-Open-WebUI-with-Ollama-on-Remote-Spark-20251226/blob/main/DGX%20Spark%20(%E7%AC%AC02%E5%A4%A9)%20%E7%94%A8%20Open%20WebUI%20%E4%BB%8B%E9%9D%A2%20%E9%81%A0%E7%AB%AF%E6%93%8D%E4%BD%9C%20DGX%20Spark%20%E4%B8%8A%E7%9A%84%20Ollama%2020251226.md)的延伸文章。**以下，我將繼續把 Mac/PC Clients，拓展到 Android/iOS Tablet Clients**，以大幅提高生產力。希望能給你更多方式參考。</sup></sub>
![Support Tablets](https://github.com/user-attachments/assets/36acd4a2-437a-4daa-ac27-d382a700d2de)
# DGX Spark (Day03) Expand Support for Android iOS Tablet Clients 20260101 🟩 [English](https://github.com/Sniper711/DGX-Spark-Day03-Expend-Support-for-Android-iOS-Tablets-20260101/blob/main/DGX%20Spark%20(Day03)%20Expand%20Support%20for%20Android%20iOS%20Tablet%20Clients%2020260101.md)
# DGX Spark (第03天) 把 Client 擴展到 安卓 蘋果 平板上 20260101 🟩 [中文版](https://github.com/Sniper711/DGX-Spark-Day03-Expend-Support-for-Android-iOS-Tablets-20260101/blob/main/DGX%20Spark%20(%E7%AC%AC03%E5%A4%A9)%20%E6%8A%8A%20Client%20%E6%93%B4%E5%B1%95%E5%88%B0%20%E5%AE%89%E5%8D%93%20%E8%98%8B%E6%9E%9C%20%E5%B9%B3%E6%9D%BF%E4%B8%8A%2020260101.md)


> ## Scenarios & Advantages
> **Android/iOS Tablet Client browser uses the Open WebUI interface → through the self-established remote connections → to run Ollama on DGX Spark Server**
> - Expand Support for Android/iOS Tablet Clients (Beyond Just Mac/PC Clients)
>   - Run Ollama anytime, anywhere — significantly boost your productivity.
>   - Install and configure `WireGuard` and `Termius` APPs on your tablet.
> - **Based on the interconnection methods of DGX Spark: [Day01A: Remote Access from Internet Guide](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(Day01A)%20Remote%20Access%20from%20Internet%20Guide%2020251220A.md) and [Day01B: Local Access from Same Subnet Guide](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(Day01B)%EF%BC%9ALocal%20Access%20from%20Same%20Subnet%20Guide%2020251220B.md), and the article [Day02: Open WebUI with Ollama on Remote Spark](https://github.com/Sniper711/DGX-Spark-Day02-Open-WebUI-with-Ollama-on-Remote-Spark-20251226/blob/main/DGX%20Spark%20(Day02)%20Open%20WebUI%20with%20Ollama%20on%20Remote%20Spark%2020251226.md)**. 
>   - Guaranteed stability through the self-estabilished remote connections
>   - No reliance on NVIDIA SYNC
> - After rebooting
>   - Simply have the Android/iOS Tablet Clients run `WireGuard` and `Termius`, then browse the `Ollama service URL` - it's super easy.
### Congratulations - Now you can run Ollama via your tablet's browser, anytime and anywhere — powered by DGX Spark's GPU!
<br>

> ## 適用情境 與 優點
> **安卓/蘋果 平板 Clients 開瀏覽器在 Open WebUI 介面上 → 透過自己建立的遠端連線 → 用 DGX Spark Server 的算力跑 Ollama**
> - 擴展到 **Android/iOS PAD Clients** (不只有 Mac/PC Client)
>   - 隨時隨地跑 Ollama，大幅提高生產力
>   - 在平板安裝並設定 `WireGuard` 與 `Termius` APPs
> - **基於前幾篇文章 [第01天A: 外網遠端操控 指南](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9A)%20%E5%A4%96%E7%B6%B2%E9%81%A0%E7%AB%AF%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220A.md) 與 [第01天B: 同子網內網操控 指南](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(%E7%AC%AC01%E5%A4%A9B)%EF%BC%9A%E5%90%8C%E5%AD%90%E7%B6%B2%E5%85%A7%E7%B6%B2%E6%93%8D%E6%8E%A7%20%E6%8C%87%E5%8D%97%2020251220B.md) 的兩種連線方式，以及 [第02天: 用 Open WebUI 介面 遠端操作 DGX Spark 上的 Ollama](https://github.com/Sniper711/DGX-Spark-Day02-Open-WebUI-with-Ollama-on-Remote-Spark-20251226/blob/main/DGX%20Spark%20(%E7%AC%AC02%E5%A4%A9)%20%E7%94%A8%20Open%20WebUI%20%E4%BB%8B%E9%9D%A2%20%E9%81%A0%E7%AB%AF%E6%93%8D%E4%BD%9C%20DGX%20Spark%20%E4%B8%8A%E7%9A%84%20Ollama%2020251226.md)**
>   - **100% 連線成功率與穩定度，自己掌握 Server/Client 連線的設定細節**
>   - 不使用 NVIDIA SYNC app 的連線方式
> - **重開機之後**
>   - 只要在 安卓/蘋果 平板上，依序啟動 `WireGuard` 與 `Termius` APPs，再 瀏覽 `Ollama 服務網址`，超級簡單。
### 恭喜你！從此你能在平板隨時隨地，用 DGX Spark 的 GPU 算力，開網頁跑 Ollama 了！
<br>

---

## 喜歡這個專案嗎？ 如果對您有幫助，請給一個 ★ Star 吧！這對我非常重要！

## If you find this project helpful, please give it a Star ★! Your support means a lot to me!

---
Davis Lin (Sniper711) .
Unauthorized article copying, distribution, or modification is prohibited.
