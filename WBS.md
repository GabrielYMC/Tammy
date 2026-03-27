# FourLeg 四腿票規劃器 — 專案 WBS

## Phase 0：概念驗證與設計 ✅ 完成

- [x] 四腿票概念研究與資料收集
- [x] 使用者情境分析（四種典型使用者）
- [x] 產品功能規劃與架構設計
- [x] AI 介入環節評估與分層策略
- [x] 技術棧評估（SvelteKit + PocketBase）
- [x] 營收模式規劃（Affiliate + Freemium）

## Phase 1：UI Prototype ✅ 完成

- [x] 教學頁 — 四腿票概念圖解
  - [x] 航程結構圖（四段 + 中停）
  - [x] 起終點可不同的範例（OKA→LAX→CTS）
  - [x] 「誰適合？」區塊
  - [x] 票價比較（單人 / 一家四口切換）
  - [x] 優勢與注意事項
  - [x] 划算公式（玩法 A / B）
  - [x] 一年行事曆時間軸
  - [x] 常見問題 FAQ（航空規範、行李、簽證、改退票、搜票教學）
  - [x] CTA 連結到搜尋工具
- [x] 搜尋工具頁 — 核心功能
  - [x] Step 1：目的地、日期、艙等、旅行人數
  - [x] Step 2：外站選擇卡片（含說明、啟動成本、推薦理由）
  - [x] 起終點可不同模式（勾選切換）
  - [x] 模擬搜尋引擎（假資料 + 隨機浮動）
  - [x] 結果卡片（含人數乘數、省錢金額）
  - [x] 展開明細：四段航程圖、成本拆解（玩法 A/B）
  - [x] AI 建議區塊
  - [x] Skyscanner 操作引導 + 一鍵複製
  - [x] 排序功能（最低成本 / 省最多 / 飛時最短）
- [x] 兩頁導覽列互相串接
- [x] 視覺風格統一（Skyscanner-like）

## Phase 2：SvelteKit 專案建置 ⬜ 待進行

- [ ] 初始化 SvelteKit 專案
- [ ] 將 HTML prototype 拆成 Svelte components
  - [ ] `Nav.svelte` 導覽列
  - [ ] `SearchForm.svelte` 搜尋表單
  - [ ] `StationCard.svelte` 外站選擇卡片
  - [ ] `ResultCard.svelte` 結果卡片
  - [ ] `CostBreakdown.svelte` 成本拆解
  - [ ] `FaqAccordion.svelte` FAQ 手風琴
  - [ ] `Timeline.svelte` 時間軸
- [ ] 教學頁做成 SSG（`+page.ts` 中 `prerender = true`）
- [ ] 外站適配矩陣 JSON 檔（`route_matrix.json`）
- [ ] 搜尋邏輯模組化（`lib/search-engine.ts`）
- [ ] PWA manifest + service worker
- [ ] 基本 SEO（meta tags、Open Graph、結構化資料）

## Phase 3：PocketBase 後端 ⬜ 待進行

- [ ] PocketBase 安裝與設定
- [ ] 資料表設計
  - [ ] `route_matrix` — 外站適配矩陣
  - [ ] `price_cache` — 票價快取（TTL 4-6hr）
  - [ ] `price_history` — 歷史票價紀錄
  - [ ] `monitors` — 使用者票價追蹤清單
  - [ ] `users` — PocketBase 內建 auth
- [ ] PocketBase SDK 整合到 SvelteKit
- [ ] 基本 CRUD API 完成

## Phase 4：票價 API 串接 ⬜ 待進行

- [ ] 申請 Kiwi Tequila API（或 Skyscanner Partner API）
- [ ] 多城市票價查詢實作
- [ ] 廉航啟動票價查詢實作
- [ ] 查詢結果快取機制
- [ ] 錯誤處理與 fallback
- [ ] 將假資料引擎替換為真實 API

## Phase 5：Affiliate 串接 ⬜ 待進行

- [ ] 註冊 Skyscanner Affiliate / Kiwi Affiliate
- [ ] 取得 Partner ID 和追蹤碼
- [ ] 「前往訂票」按鈕替換為 affiliate link
- [ ] 「查廉航」按鈕替換為 affiliate link
- [ ] 確認追蹤碼正確觸發（測試轉換追蹤）

## Phase 6：部署上線 ⬜ 待進行

- [ ] 購買域名（fourleg.tw 或類似）
- [ ] Vercel 部署 SvelteKit 前端
- [ ] VPS 部署 PocketBase（Hetzner / Linode）
- [ ] SSL 憑證設定
- [ ] Google Analytics / Plausible 埋點
- [ ] Google Search Console 提交 sitemap
- [ ] 上線前功能測試
- [ ] 正式上線 🚀

## Phase 7：票價追蹤功能 ⬜ 待進行

- [ ] 「票價追蹤」頁面 UI
  - [ ] 追蹤清單卡片（路線、建立價格、最新價格）
  - [ ] 迷你趨勢折線圖（sparkline）
  - [ ] 價格方向指標（上漲/下降/持平）
  - [ ] AI 判讀建議（觀望/下手）
- [ ] 設定目標價機制
- [ ] Cron job 定時掃描（每 6 小時）
- [ ] LINE Notify 整合
  - [ ] 使用者綁定 LINE token
  - [ ] 價格低於目標時推播通知
- [ ] 免費版限制 3 組 / 付費版不限

## Phase 8：進階功能 ⬜ 未來規劃

- [ ] 使用者帳號系統（PocketBase auth）
- [ ] 儲存方案功能
- [ ] 歷史票價趨勢圖（完整版）
- [ ] AI 複雜行程規劃（對話式，Sonnet 等級）
- [ ] 多人不同出發地規劃
- [ ] 付費訂閱功能（綠界 / PAYUNi）
- [ ] 部落格 / 教學文章 CMS
- [ ] 社群分享功能（行程摘要圖）

---

*最後更新：2026-03-27*
