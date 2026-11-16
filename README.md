# StockScope｜美股投資研究室（完整版）

繁體中文、美股入門教育靜態網站。依照根目錄 `AGENTS.md` 的開發規範建立，可持續新增股票、ETF、文章及工具。

## 功能
- 深色響應式首頁
- 股票介紹：NVDA、AAPL、TSLA
- ETF 介紹：QQQ、VOO
- 投資知識：ETF 是什麼、定期定額入門
- ETF 雙檔比較：QQQ、QQQM、VOO、SPY（靜態教育資料）
- 定期定額試算器：每月投入、初始本金、年數、假設年化報酬率；動態金額與 SVG 圖表

## 本機預覽
解壓縮後直接打開 `index.html`；不需要 npm 或伺服器。

## GitHub Pages 部署
1. 在 GitHub 建立 **Public** repository，例如 `stockscope`。
2. 上傳**本專案資料夾內的所有檔案**，確保 `index.html` 在 repository 根目錄。
3. 進入 **Settings → Pages**，Source 選 **Deploy from a branch**，Branch 選 `main`，Folder 選 `/(root)`，儲存。
4. 部署完成後開啟 `https://<你的帳號>.github.io/stockscope/`。
5. 測試首頁、工具頁、文章與所有導覽連結。

## 如何讓 AI 擴充
請先閱讀 `AGENTS.md`，然後下指令，例如「依照 AGENTS.md 新增 TSLA 個股介紹頁並更新首頁」。AI 必須沿用共用樣式、頁面模板、相對路徑及風險聲明。

## 計算模型
假設年化有效報酬率 `R`，月報酬率為 `(1 + R)^(1/12) - 1`；每月底投入 `M`，逐月更新資產：`資產 = 上月資產 × (1 + 月報酬率) + M`。實際市場報酬並不固定；試算未計稅、手續費、通膨與匯率。

## 免責聲明
網站為教育用途，不提供即時股價或個人化投資建議。投資可能損失本金。

## AGENTS.md 擴充示範：新增 TSLA
- 依 `stocks/nvda.html` 模板建立 `stocks/tsla.html`，共用 `assets/style.css` 與 `assets/app.js`。
- 在 `index.html` 的股票研究區新增 TSLA 入口。
- 僅使用教育性企業介紹與風險說明，不填入未查證的即時行情。
- 部署後請確認 TSLA 卡片、返回首頁、手機版排版及瀏覽器主控台無錯誤。
