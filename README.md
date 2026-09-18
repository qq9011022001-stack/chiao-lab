# 焦信達實驗室網站

東海大學資訊工程學系焦信達助理教授研究室網站。純靜態網頁，所有內容來自 `data/` 內的 JSON，改資料不需要改程式。

## 檔案結構

```
index.html            網站主頁（單頁式，以 #/ 路由切換分頁）
admin.html            資料後台：表單編輯 → 下載 JSON
assets/style.css      樣式
assets/app.js         讀取 JSON 並渲染畫面
data/profile.json     教師基本資料、學歷、經歷、獲獎、演講
data/publications.json  論文著作（123 筆）
data/projects.json    研究計畫（47 項）
data/patents.json     已獲證專利（19 件）
data/site.json        最新消息、實驗室成員、授課科目
```

## 部署到 GitHub Pages

1. 在 GitHub 建立新 repository，例如 `chiao-lab`（設為 Public）。
2. 把本資料夾內的所有檔案上傳到 repo 根目錄（網頁介面可直接拖曳整包檔案）。
3. 進入 repo 的 **Settings → Pages**。
4. Source 選 **Deploy from a branch**，Branch 選 `main`、資料夾選 `/ (root)`，按 Save。
5. 等一到兩分鐘，網址會是 `https://<你的帳號>.github.io/chiao-lab/`。

若想用系上或自有網域，在 Settings → Pages 的 Custom domain 填入即可。

## 日常更新資料

### 方式一：用後台介面（推薦）

1. 開啟 `https://<你的帳號>.github.io/chiao-lab/admin.html`
2. 上方選分頁（論文著作／研究計畫／專利／最新消息／成員／獲獎／演講／基本資料）
3. 按「＋ 新增一筆」或點開既有項目直接修改
4. 按「下載目前分頁的 JSON」
5. 回到 GitHub repo 的 `data/` 資料夾 → 點進同名檔案 → 右上角 **Upload files** 或編輯 → 覆蓋上傳
6. 約一到兩分鐘後網站自動更新

> 後台不會自動存檔，關掉分頁未下載的修改會消失。每次編輯完請先下載。

### 方式二：直接編輯 JSON

在 GitHub 上點開 `data/xxx.json`，按鉛筆圖示線上編輯後 Commit 即可。格式範例：

```json
{
  "type": "conf_intl",
  "year": 2026,
  "title": "論文標題",
  "authors": "作者一, 作者二, Hsin-Ta Chiao",
  "venue": "研討會全名, July 2026",
  "note": "SCI, IF 3.5",
  "corresponding": true
}
```

`type` 可用值：`journal_intl`（國際期刊）、`conf_intl`（國際研討會）、`standard`（國際標準提案）、`journal_zh`（國內期刊與專書）、`conf_zh`（國內研討會）、`report`（技術報告與法規）。

## 本機預覽

不能用滑鼠雙擊 `index.html`（瀏覽器會擋住讀取本機 JSON）。請在資料夾內執行：

```bash
python3 -m http.server 8000
```

然後開啟 `http://localhost:8000`。

## 想要真正的線上後台？

目前的 `admin.html` 是「編輯後下載檔案再上傳」的流程，零設定、零費用。
若希望教授登入後直接存檔、不用碰 GitHub 檔案，可以改接 Decap CMS（需額外架一個 OAuth 授權服務，或改用 Netlify 部署）。現有的 JSON 資料結構可以完整沿用。
