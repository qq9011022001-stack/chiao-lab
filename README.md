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


