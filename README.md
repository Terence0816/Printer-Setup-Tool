這是一份為您的 GitHub 專案準備的 README.md 範本。我已經將功能特色、使用流程以及您剛剛提供的圖片邏輯都整合進去了。

您只需要在 GitHub 上建立一個新的 Repository，然後將以下內容複製到 README.md 檔案中，並將圖片檔案上傳到專案的 images 資料夾（或您喜歡的路徑）即可。

萬用印表機自動部署工具 (All-in-One Printer Deployment Tool)
PrtEasySetup 是一個輕量化、自動化的印表機部署工具，專為 IT 管理員與 MSP 服務商設計。它解決了繁瑣的驅動程式 INF 解析問題，並將「設定檔建立」、「驅動安裝」、「設定備份與還原」整合在一個執行檔中。

✨ 主要功能
智慧 INF 解析：內建針對 HP、Epson、Brother、Kyocera、TSC 等品牌的專用解析引擎，能自動過濾雜訊（如 Utility、Fax 驅動），精準抓取印表機型號。

自動化安裝：一鍵完成 TCP/IP 或 USB 連接埠建立、驅動程式註冊 (使用 printui 暴力安裝技術，確保成功率) 及印表機新增。

設定備份與還原：可備份印表機的細部設定（如單/雙面、紙匣選擇、黑白/彩色），並在部署時自動還原 (set.dat)，確保所有使用者設定一致。

路徑感知：支援從網路共用資料夾 (NAS/Server Share) 直接執行，自動處理權限與路徑問題。

簡單易用：無須安裝，單一 EXE 檔案即可運作。

🚀 快速開始
1. 準備工作
將 PrtEasySetup.exe 與印表機的驅動程式檔案（.inf, .dll, .cat 等）放在同一個資料夾中。

2. 執行程式
以「系統管理員身分」執行 PrtEasySetup.exe。

情境 A：初次建立設定檔
如果是第一次在該資料夾執行，程式會偵測不到 ip.ini，並引導您建立。

輸入連線資訊： 輸入印表機的 IP 位址，如果是 USB 印表機，請輸入 usb (程式會自動偵測對應埠口)。

(請將圖片重新命名並上傳，例如：images/step1_input.png)

選擇型號： 程式會自動掃描目錄下的 INF 檔。如果包含多個型號，會跳出選單供您選擇。

支援多種廠牌解析 (Epson, Brother, TSC 等) (範例：TSC TX210)

確認設定： 設定檔 ip.ini 建立完成，視窗會顯示解析出的型號與連接埠。

立即安裝： 程式會詢問是否立即進行安裝，點選「是」即可開始部署。

情境 B：快速部署 (已有設定檔)
當資料夾內已經存在 ip.ini 時，執行程式將自動跳過設定步驟，直接讀取設定並開始安裝印表機。這非常適合大量部署到客戶端電腦。

情境 C：維護與備份
備份設定：如果偵測到電腦已安裝該印表機，但資料夾內沒有 set.dat，程式會詢問是否備份目前的設定（包含紙張、浮水印等進階設定）。

還原設定：如果偵測到 set.dat 存在，安裝完畢後會自動將設定還原到印表機。

📂 檔案說明
PrtEasySetup.exe: 主程式。

ip.ini: 自動生成的設定檔，格式如下：

程式碼片段

ip, [IP或USB埠], [印表機名稱], [驅動名稱], [INF檔案名稱], [參數標記]
set.dat: (選用) 印表機設定的二進位備份檔，由 rundll32 printui.dll 生成。

🛠️ 技術細節
本工具使用 PowerShell 編寫並封裝為 Win32 應用程式。核心技術包括：

Windows SetupAPI 模擬：模擬 Windows 讀取 INF 的邏輯，支援 [Strings] 變數替換與 [Manufacturer] 區段鎖定，解決 Epson/Brother 等特殊 INF 結構解析錯誤的問題。

PrintUI.dll 整合：使用微軟官方 rundll32 printui.dll,PrintUIEntry /ia 指令進行驅動安裝，比 PowerShell 的 Add-PrinterDriver 更穩定且支援度更高。

⚠️ 注意事項
由於本程式是由 PowerShell 封裝而成，某些防毒軟體 (如 Windows Defender SmartScreen) 可能會誤判為不明軟體。

本程式已通過基本的 OV 程式碼簽章 (Code Signing)，建議加入信任清單以確保執行順利。

安裝過程範例：

<img width="531" height="284" alt="2025-12-08_155744" src="https://github.com/user-attachments/assets/2d85b2e1-2b16-4110-bf17-11cc90f6c5b7" />
<br>

---
<img width="269" height="131" alt="2025-12-08_155759" src="https://github.com/user-attachments/assets/3cc10cf4-bae9-4c52-b364-64932f30a361" />
<br>

---
<img width="327" height="369" alt="2025-12-08_155813" src="https://github.com/user-attachments/assets/ef97e697-3504-4b70-af85-a23af356e633" />
<br>

---
<img width="174" height="135" alt="2025-12-08_155821" src="https://github.com/user-attachments/assets/4fd98b1c-471b-4721-8001-1504a936bb40" />
<br>

---
<img width="177" height="116" alt="2025-12-08_155831" src="https://github.com/user-attachments/assets/64c14a35-5a24-411a-a25c-6de755a25d34" />
<br>

---
<img width="392" height="205" alt="2025-12-08_155857" src="https://github.com/user-attachments/assets/d3107cdc-be3a-41b4-9ca2-a7ccb8a7be2b" />
<br>

---
Developed for MSP Internal Use.
