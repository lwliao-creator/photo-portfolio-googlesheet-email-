# 小柯攝影工作室｜作品集網站

臺中婚紗、婚禮紀錄、形象照攝影作品集。純 HTML + CSS 單頁網站，不需要任何建置工具，可直接部署到 Vercel。

## 資料夾結構

```
ko-photo/
├── index.html      ← 全部 HTML 與 CSS 都在這裡
├── vercel.json     ← Vercel 設定（快取、乾淨網址）
├── README.md
└── images/
    ├── hero.jpg              首頁大圖（建議 1920×1080）
    ├── wedding-01~06.jpg     婚紗（建議 800×1000 直式）
    ├── ceremony-01~06.jpg    婚禮紀錄
    ├── portrait-01~06.jpg    形象照
    ├── case-wedding.jpg      案例圖（建議 900×600 橫式）
    ├── case-ceremony.jpg
    ├── case-portrait.jpg
    └── about.jpg             攝影師照片
```

目前 `images/` 內是灰褐色的示意圖，**用同樣檔名覆蓋成真實照片即可**，不用改程式碼。

## 換照片前的小提醒

- 檔名一律小寫英文＋數字，不要用中文或空格（Vercel 主機分大小寫，`Wedding-01.JPG` 會讀不到）。
- 每張壓縮到 300 KB 以下（可用 [Squoosh](https://squoosh.app)），網頁才會快。
- 照片內容變了，記得一起修改 `index.html` 裡對應的 `alt` 文字，這是 Google 圖片搜尋的依據。

## 上線前要改的地方

在 `index.html` 搜尋並替換：

| 搜尋 | 改成 |
|---|---|
| `YOUR_SCRIPT_ID`（整段 SCRIPT_URL） | Apps Script 網頁應用程式網址（見下方） |
| `hello@kophoto.tw` | 真實 Email |
| `kophoto.tw`（Instagram） | 真實 IG 帳號 |
| `your-domain.vercel.app` | 部署後的網址 |

### 讓表單寫入 Google 試算表

1. 建立一個新的 Google 試算表。
2. 「擴充功能 → Apps Script」，貼上 `google-apps-script.gs` 的全部內容並儲存。
3. 「部署 → 新增部署作業 → 網頁應用程式」：執行身分選「我」，存取權選「所有人」，然後授權。
4. 複製結尾是 `/exec` 的網址，貼到 `index.html` 最下方的 `SCRIPT_URL`。
5. 之後如果修改了 Apps Script，要到「管理部署作業 → 編輯 → 新版本」重新發布，網站才會用到新程式。

## 部署步驟

### 1. 上傳到 GitHub

**不會用指令的話：**
1. 登入 GitHub → 右上角 `+` → **New repository**，取名 `ko-photo`，按 Create。
2. 點 **uploading an existing file**，把整個資料夾的內容（`index.html`、`images` 資料夾等）拖進去。
3. 按 **Commit changes**。

**會用 Git 的話：**
```bash
cd ko-photo
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/你的帳號/ko-photo.git
git push -u origin main
```

### 2. 部署到 Vercel

1. 到 https://vercel.com 用 GitHub 帳號登入。
2. **Add New → Project**，選擇 `ko-photo` repository → **Import**。
3. Framework Preset 選 **Other**，其他設定都不用動 → **Deploy**。
4. 約 30 秒後會拿到 `https://ko-photo-xxx.vercel.app` 網址。

之後只要推送新的 commit 到 GitHub，Vercel 就會自動重新部署。

## 本機預覽

直接雙擊 `index.html` 用瀏覽器開啟即可。

## RWD 斷點

| 裝置 | 寬度 | 作品集欄數 |
|---|---|---|
| 桌機 | 1025px 以上 | 3 欄 |
| 平板 | 769px – 1024px | 2 欄 |
| 手機 | 768px 以下 | 1 欄 |
