# CLAUDE.md — pe-dashboard 右昌國小體育班系統入口

> 此文件供 Claude Code 使用，說明專案用途、結構與開發慣例。

---

## 專案目標

單頁式入口網站（Portal），把右昌國小體育班相關的各個獨立系統整理成卡片，方便老師從一個網址快速跳轉到需要的工具，不用記一堆不同的網址。

## 技術棧

純前端單一 HTML 檔案，無建置流程、無依賴套件。

## 檔案結構

```
pe-dashboard/
├── CLAUDE.md
└── index.html   ← 全部程式碼（HTML + CSS + JS）都在這一個檔案
```

## 卡片連結的系統

`index.html` 目前收錄以下卡片，各自連到對應的獨立 repo/系統：

- 體育班專項成績評分系統 → `pe-grading-system`
- 體育組資料上傳系統
- 體育組經費管控系統
- 體適能常模對照工具 → `fitness-check`
- 體育班評鑑文件總覽 → `pe-tools`
- 評鑑文件產生工具
- 評鑑工具使用說明

新增/移除子系統時，記得同步更新卡片區塊（`class="card"`）與對應的展開預覽（`class="card-popup"`）。

## 開發慣例

- 卡片有 hover 展開效果（`.card-popup`），修改卡片說明文字時兩處（截斷版與展開版）都要改
- 顏色用 badge class（`badge-gold`/`badge-blue`/`badge-green`/`badge-orange`/`badge-purple`）區分系統類別
- 純前端，沒有後端 API，改完直接部署（GitHub Pages 或直接 commit push）即可生效

## 版本控制

- GitHub 遠端：`asics49/pe-dashboard`
- `.gitignore` 排除 `.claude/`、`.DS_Store`（2026-07-20 新增）
- `.gitattributes` 統一換行符為 LF，避免不同裝置編輯造成整檔案換行符差異的假 diff（2026-07-20 新增）
- 專案原始碼位於 Google Drive 同步資料夾，多台裝置編輯時請留意先 `git pull`/`fetch` 確認沒有其他裝置的未同步提交，再 push
