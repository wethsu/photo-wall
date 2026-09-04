# 📸 班級秘書 - 即時互動相片牆 (Photo Wall)

一套專為**學校教學、成果發表、班級活動、同樂會及各類聚會**量身打造的現代化**即時互動相片牆系統**。
全站採用純前端 + Google Firebase 無伺服器（Serverless）架構，具備多班級房間隱私隔離、多視圖投影、即時大螢幕互動畫筆標註與一鍵高清匯出功能，**完全 0 元免費運作**！

---

## 🌐 線上正式版本

- 🏠 **系統入口（教師大廳 / 學生專屬代碼直達）**：
  👉 [https://photo-wall-tw.web.app/](https://photo-wall-tw.web.app/)
- 📺 **大螢幕投影展示端**：
  👉 [https://photo-wall-tw.web.app/screen.html](https://photo-wall-tw.web.app/screen.html)
- 📱 **學生 / 參與者手機上傳端**：
  👉 [https://photo-wall-tw.web.app/upload.html](https://photo-wall-tw.web.app/upload.html)
- *(GitHub Pages 備援鏡像：[https://wethsu.github.io/photo-wall/](https://wethsu.github.io/photo-wall/))*

---

## ✨ 系統核心亮點

### 1. 📺 大螢幕多模式投影 (screen.html)
- **三種視圖一鍵切換**：
  - **🎭 主舞台焦點模式 (Stage)**：高質感劇院風，焦點照片大圖自動輪播，背景環境動態模糊，完整呈現作者與留言。
  - **🧱 相片時光牆 (Wall)**：全景瀑布流相片牆，右側新照片即時彈跳推播與淡入動畫。
  - **🔲 多圖分割對比網格 (Split Grid)**：專為課堂發表設計，支援 2、4、6、8、9、12 格分割對比，支援格位獨立指派、一鍵清空格位與格位文字隱藏。
- **✏️ 浮動拖曳式畫筆標註工具 (Annotation Board)**：
  - 工具列支援自由拖曳移動，絕不遮擋任何重要照片內容。
  - 支援多色彩選取、筆刷粗細調整、橡皮擦與一鍵清空。
  - **📥 直接下載畫好的圖**：精準裁切目前視圖範圍，自動將底圖與手繪標記完美合成高清 PNG 下載至電腦，絕不要求使用者手動螢幕截圖。
- **📥 一鍵高清截圖存檔**：
  - 支援將大螢幕目前畫面（主舞台/分割對比）直接合成 2K 高解析度圖檔下載。
  - 內建跨域圖片安全保護與無縫備援下載機制。
- **🎯 智慧自適應 QR Code**：
  - 大螢幕會依據目前所在的班級房間代碼（Room ID），自動生成專屬上傳 QR Code 與代碼，免除手動設定麻煩。

### 2. 📱 手機即時上傳 (upload.html)
- **極致友善體驗**：手機瀏覽器免安裝任何 App，掃碼即開即用。
- **拍照與相簿雙支援**：支援後鏡頭直接即時拍攝或從手機相簿批次多選。
- **前端智慧壓縮引擎**：利用 HTML5 Canvas 在手機端自動完成最佳比例壓縮，上傳省流量、秒級完成，低延遲推播至大螢幕。
- **個性化互動**：可填寫上傳者暱稱、心情備註與即時進度條回饋。

### 3. 🔐 教師管理大廳與房間隱私隔離 (index.html)
- **多班級房間隔離**：每個班級擁有專屬代碼（如 sjps-0904-8a），照片資料庫完全獨立隔離，各班互不干擾。
- **教師 Google OAuth 登入**：教師登入後可隨時建立新班級、查看歷史班級清單與快速進入大螢幕/上傳頁。
- **學生免登入直達**：學生或家長只需輸入班級代碼或掃描 QR Code，即可直接進入所屬班級，保障隱私與操作流暢度。

---

## 📁 專案檔案架構

```plaintext
├── index.html            # 系統入口大廳 (教師登入、班級管理、學生代碼直達)
├── screen.html           # 大螢幕展示端 (主舞台、相片牆、分割對比、畫筆標註、截圖下載)
├── upload.html           # 行動端上傳頁 (相機直拍、多圖上傳、壓縮優化)
├── firebase-config.js    # 集中式 Firebase 連線金鑰與設定檔
├── firebase.json         # Firebase Hosting & 規則部署配置
├── .firebaserc           # Firebase 專案環境對應 (test-49c68)
├── firestore.rules       # Firestore 安全存取規則
├── storage.rules         # Cloud Storage 檔案儲存規則
└── README.md             # 專案完整說明文件
```

---

## 🛠️ 技術架構

- **前端技術**：HTML5, CSS3, Tailwind CSS (CDN), Lucide Icons, Canvas API
- **資料庫與同步**：Google Cloud Firestore (即時 Snapshot 監聽秒級推送)
- **檔案儲存**：Google Cloud Storage
- **身分驗證**：Google Firebase Authentication (Google OAuth 2.0)
- **網站託管**：Google Firebase Hosting (亦支援 GitHub Pages、Cloudflare Pages)

---

## 🚀 快速上手教學

### 教師操作流程
1. 打開 [https://photo-wall-tw.web.app/](https://photo-wall-tw.web.app/)。
2. 點擊 **「使用 Google 帳號登入」**。
3. 輸入班級或活動名稱（例如：601 班科學展覽成果），點擊 **「建立班級相片牆」**。
4. 系統將自動配發一組專屬代碼，點擊 **「開大螢幕」** 即可投放大螢幕或電子白板！

### 學生 / 參與者操作流程
1. 用手機相機掃描大螢幕右下角或浮動設定中的 **QR Code**。
2. 拍下精彩照片、填寫暱稱與留言，點擊 **「確認上傳」**。
3. 大螢幕將在 1 秒內自動收到並以動態效果投影呈現！

---

## 📄 授權說明

本專案遵循 MIT License 開源授權，歡迎教育單位、社團、活動籌辦團隊自由使用與二次開發。
