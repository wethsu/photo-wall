# 📸 互動相片牆（方案 A：純前端 + Firebase 無伺服器架構）

這是一套為活動、班級、婚禮或聚會設計的**即時互動相片牆**系統。採用純前端單一檔案架構（Single-File HTML），無需架設後端伺服器，配合 Google Firebase 免費服務即可秒級同步！

---

## 📁 檔案清單

| 檔案名稱 | 用途 | 說明 |
| :--- | :--- | :--- |
| **`upload.html`** | 📱 手機拍照上傳端 | 支援後鏡頭直拍、相簿選取、前端 Canvas 智慧壓縮、即時進度條與祝福留言。 |
| **`screen.html`** | 📺 大螢幕投影展示端 | 焦點大圖主舞台、右側相片時光軸、即時新照片彈跳動效、自動輪播與專屬 QR Code。 |

---

## 🚀 3 分鐘快速啟用步驟

### 第一步：Firebase 前置設定（一次性）
1. 前往 [Firebase Console](https://console.firebase.google.com/) 並新增一個專案。
2. **啟用 Firestore Database**：
   - 點擊左側選單「Firestore Database」➔「建立資料庫」。
   - 規則選「**測試模式** (Test mode)」➔ 選擇離你最近的伺服器地點（例如 `asia-east1`）並完成建立。
3. **啟用 Storage**：
   - 點擊左側選單「Storage」➔「開始使用」。
   - 規則選「**測試模式** (Test mode)」並完成建立。
4. **取得金鑰 (firebaseConfig)**：
   - 點擊左上方 ⚙️「專案設定」➔「一般」➔ 滑到最下方新增「網頁應用程式 (</>)」。
   - 複製給你的 `firebaseConfig` 物件。

---

### 第二步：設定金鑰（二選一）

#### 方式一：直接在網頁介面輸入（最直覺）
- 直接雙擊打開 `upload.html` 或 `screen.html`，網頁會自動跳出設定彈窗。
- 將 `firebaseConfig` 的 JSON 貼上並點擊「儲存」即可！（設定會自動記錄在瀏覽器）。

#### 方式二：直接編輯 HTML 程式碼
用記事本或編輯器打開 `upload.html` 與 `screen.html`，將開頭的 `firebaseConfig` 物件替換為你的金鑰：
```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project",
  storageBucket: "your-project.firebasestorage.app",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

---

## 🌐 如何部署上線讓大家的手機掃碼？

由於手機需要連線至 `upload.html`，建議將檔案放到任何免費的靜態網頁空間：

1. **GitHub Pages**：建立 Repository 並開啟 Pages，直接免費取得 HTTPS 網址。
2. **Vercel / Netlify**：直接把資料夾拖拉上傳，10 秒完成部署。
3. **Firebase Hosting**：直接使用 Firebase 內建的免費 Hosting。

> 💡 **小提示**：大螢幕 `screen.html` 會自動抓取同網域下的 `upload.html` 網址並即時在右下角繪製 QR Code！
