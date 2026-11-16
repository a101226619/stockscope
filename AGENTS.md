# StockScope — AGENTS.md（AI 專案協作規範）

> **每次 AI 修改專案前必讀。** 這份文件是可持續擴充網站的規格，而非一次性提示詞。

## 1. 使命與使用者
StockScope 是繁體中文美股入門研究網站，提供股票／ETF 的教育性介紹、ETF 雙檔比較、定期定額試算與投資文章。目標使用者是初學者；不能提供保證獲利或個人化買賣建議。

## 2. 技術約束
- 使用 HTML5、CSS3、原生 JavaScript；零建置步驟、零後端、零必要第三方依賴。
- GitHub Pages 的 `/<repository>/` 子路徑必須可用；內部連結使用相對路徑。
- 以 `assets/style.css` 管理共用樣式、`assets/app.js` 管理共用互動。避免複製整份 CSS/JS 到新頁面。
- 全站 `lang="zh-Hant"`，手機優先，語意化 HTML，表單有 label，互動支援鍵盤。
- 不增加登入、追蹤、Cookie、API 金鑰或個資收集。

## 3. 視覺設計規則
- 深藍黑背景 `#090f1b`、卡片 `#111e2f`、薄荷綠重點 `#68e5c1`、柔和灰藍文字。
- 使用現有 `.container`、`.nav`、`.section`、`.grid`、`.card`、`.panel` 與工具頁共用元件。
- 排版要有明確層級、足夠對比、hover/focus 回饋；窄螢幕不橫向溢出。
- 新增功能應延續既有設計，不要自行改成其他配色或 UI 框架。

## 4. 目錄與命名
```text
index.html                 首頁、所有主要入口
AGENTS.md                  本規範
README.md                  安裝、測試、部署與擴充
assets/style.css           全站樣式
assets/app.js              工具互動程式
stocks/{ticker}.html       股票介紹，如 nvda.html
etfs/{ticker}.html         ETF 介紹，如 qqq.html
articles/{topic}.html      知識文章，如 what-is-etf.html
tools/compare.html         ETF 比較
tools/calculator.html      定期定額試算
```
檔名一律英文小寫，單字用連字號，股票代碼檔名小寫；不要使用空格或中文檔名。

## 5. 頁面內容模板
- 每個內容頁至少包含：標題、簡短摘要、核心概念、特色、風險、查證方向、回首頁入口、免責聲明。
- 新股票頁參照 `stocks/nvda.html`；新 ETF 頁參照 `etfs/qqq.html`；新文章參照 `articles/what-is-etf.html`。
- 新工具頁參照 `tools/compare.html` 或 `tools/calculator.html`，需要表單驗證、空值處理、結果說明。
- 在 `index.html` 加入對應入口；所有子頁使用 `../assets/...`，首頁使用 `./assets/...`。

## 6. 資料與財務安全
- 禁止編造即時價格、殖利率、費用率、持股權重、報酬或財報數字。
- ETF 比較目前使用靜態、概念性資料；若新增會變動數值，必須註明來源與截至日期。
- 試算器是數學模型：輸入金額、年數、假設年化報酬率；採每月底投入、每月複利，使用 `(1+年化率)^(1/12)-1` 換算月率。
- 試算必須區分本金與收益，支援零利率與負利率，明示未計入稅、費用、通膨及匯率。
- 不得把試算報酬率稱為「預測」或「保證」。頁尾必須保留教育用途免責聲明。

## 7. AI 工作流程（每次都要遵守）
1. 先讀 AGENTS.md、README.md、相關既有頁面。
2. 確認修改範圍，優先複用現有元件與樣式。
3. 依既有模板新增頁面或功能，不破壞原有路由。
4. 更新首頁導覽、README（如果有新增功能）及相關交叉連結。
5. 檢查所有本地 href/src 路徑、表單驗證、手機版、鍵盤操作、財務風險聲明。
6. 簡述改動檔案與測試結果；未測試的項目必須明說。

## 8. 驗收清單
- [ ] index.html 能直接打開，GitHub Pages 無需建置即可部署。
- [ ] QQQ、VOO、NVDA、AAPL、兩篇文章及兩個工具頁均可進入。
- [ ] ETF 選單切換後資訊同步更新。
- [ ] 試算器調整輸入後更新金額與折線圖；0% 利率與負報酬可運作。
- [ ] 所有連結正確、無 console error、手機版不溢出。
- [ ] 不聲稱資料為即時報價；有風險提醒。

## 9. 擴充任務示範
使用者要求「新增 TSLA 股票介紹」：先參照 `stocks/nvda.html`，建立 `stocks/tsla.html`，沿用相同 HTML 結構與 CSS，介紹業務、特色與風險，加入查證來源，在首頁股票區加入卡片，檢查相對路徑；不得填入未驗證的即時股價。

使用者要求「ETF 比較新增 IVV」：在 `assets/app.js` 的比較資料中增加 IVV 的追蹤指數、投資範圍、特色及風險；在 `tools/compare.html` 的兩個選單都新增 IVV；測試所有配對，保持靜態資料註記。
