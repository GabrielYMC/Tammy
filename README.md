# ✈️ FourLeg — 四腿票規劃器

> 讓四腿票不再燒腦。輸入你想去的地方，系統自動比較所有外站組合的真實總成本。

![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-prototype-orange)
![Made in](https://img.shields.io/badge/made%20in-Taiwan%20🇹🇼-blue)

## 這是什麼？

**四腿票**（外站四段票）是一種利用航空定價策略的省錢購票方式：從台灣以外的城市出發，經台灣飛往長程目的地再飛回，最後回到外站，總計四段航程。因為不同出發地套用不同市場定價，四段加起來反而比台北直飛來回便宜——一家四口飛一趟美西，省下的錢可能超過十萬。

**FourLeg** 是一個幫你自動比較所有四腿票組合的網頁工具：

- 🔍 **智慧搜尋**：輸入目的地和日期，自動掃描所有外站方案
- 💰 **真實總成本**：四腿票價 + 啟動廉航 = 你實際要花的錢（不是只給你四腿票價讓你自己加）
- 👨‍👩‍👧‍👦 **家庭友善**：支援旅行人數，直接顯示全家的省錢金額
- 🔀 **起終點可不同**：沖繩出發、札幌結束，一張票串三趟旅行
- 💡 **AI 建議**：每個方案附上自然語言的分析和注意事項
- 📋 **訂票引導**：教你到 Skyscanner 怎麼搜，一鍵複製四段路線

## 截圖

| 搜尋表單 | 結果比較 | 教學頁 |
|---------|---------|-------|
| 結構化輸入，外站卡片帶說明 | 真實總成本排序，展開看明細 | 概念圖解 + FAQ 延伸閱讀 |

> *目前為 UI Prototype 階段，票價為模擬資料。*

## 技術棧

| 層級 | 選型 | 理由 |
|-----|------|------|
| 前端 | **SvelteKit** | 表單互動 reactivity 天生簡潔，SSG 支援教學頁 SEO |
| 後端 | **PocketBase** | 單一 binary，自帶 auth + realtime，VPS 月費 ~NT$150 |
| 票價 API | **Kiwi Tequila** | 原生支援多城市查詢，有免費額度，回傳含 booking link |
| 部署 | **Vercel** + VPS | 前端 Vercel 免費方案，PocketBase 跑在 Hetzner/Linode |
| AI | **Claude Haiku** | 需求解析 + 結果詮釋，每次查詢成本 < NT$0.3 |

## 專案結構（規劃中）

```
fourleg/
├── src/
│   ├── routes/
│   │   ├── +page.svelte          # 搜尋工具頁
│   │   ├── teach/+page.svelte    # 教學頁（SSG）
│   │   └── track/+page.svelte    # 票價追蹤頁
│   ├── lib/
│   │   ├── components/
│   │   │   ├── Nav.svelte
│   │   │   ├── SearchForm.svelte
│   │   │   ├── StationCard.svelte
│   │   │   ├── ResultCard.svelte
│   │   │   ├── CostBreakdown.svelte
│   │   │   ├── FaqAccordion.svelte
│   │   │   └── Timeline.svelte
│   │   ├── data/
│   │   │   └── route_matrix.json  # 外站適配矩陣
│   │   ├── search-engine.ts       # 搜尋 + 排序邏輯
│   │   ├── price-api.ts           # Kiwi API 封裝
│   │   └── pocketbase.ts          # PocketBase SDK
│   └── app.html
├── pb/                             # PocketBase 資料與設定
├── static/
│   ├── manifest.json              # PWA
│   └── icons/
├── prototype/                      # 目前的 HTML prototype
│   ├── index.html                 # 搜尋工具
│   └── teach.html                 # 教學頁
├── WBS.md                          # 專案進度追蹤
└── README.md
```

## 開發進度

| Phase | 狀態 | 說明 |
|-------|-----|------|
| 0. 概念驗證 | ✅ 完成 | 需求分析、架構設計、技術選型 |
| 1. UI Prototype | ✅ 完成 | 完整互動 HTML prototype（搜尋頁 + 教學頁 + FAQ） |
| 2. SvelteKit 建置 | ⬜ 下一步 | 拆 components、SSG、PWA |
| 3. PocketBase 後端 | ⬜ | 資料表、auth、CRUD |
| 4. 票價 API 串接 | ⬜ | Kiwi Tequila API，替換假資料 |
| 5. Affiliate 串接 | ⬜ | Skyscanner/Kiwi 聯盟行銷連結 |
| 6. 部署上線 | ⬜ | Vercel + VPS，域名、SSL、Analytics |
| 7. 票價追蹤 | ⬜ | 監控清單、趨勢圖、LINE Notify 推播 |
| 8. 進階功能 | ⬜ | 帳號系統、付費訂閱、AI 行程規劃 |

完整 WBS 見 [`WBS.md`](./WBS.md)。

## 營收模式

| 管道 | 說明 |
|------|------|
| **Affiliate 佣金** | 使用者透過工具的連結在 Skyscanner / Kiwi / Trip.com 訂票，平台回饋佣金（1-3%） |
| **Freemium 訂閱** | 免費版：搜尋 + 3 組票價追蹤。付費版（~NT$99/月）：無限追蹤 + 趨勢圖 + AI 買點建議 |
| **廉航啟動票 Affiliate** | 啟動票的廉航連結（樂桃、虎航、酷航）同樣帶追蹤碼 |

## 本地開發（Prototype）

目前階段只有靜態 HTML，直接打開即可：

```bash
# Clone
git clone https://github.com/your-username/fourleg.git
cd fourleg

# 打開 prototype
open prototype/index.html
# 或
open prototype/teach.html
```

SvelteKit 版本建置後：

```bash
npm install
npm run dev
```

## 核心概念：外站適配矩陣

工具的推薦品質取決於一張「外站 × 目的地 × 航空公司」的適配矩陣。這張表記錄了哪些組合是可行的、預估啟動成本、適合的艙等、以及該外站的特性說明。初期手動維護約 20-30 個外站 × 10-15 個熱門目的地，隨使用者回報和票價資料累積逐步擴充。

```json
{
  "OKA": {
    "name": "沖繩",
    "activation_cost_range": [2200, 3500],
    "activation_carriers": ["樂桃", "虎航"],
    "compatible_destinations": {
      "LAX": { "carriers": ["長榮", "星宇"], "class": ["Y", "C"] },
      "CDG": { "carriers": ["長榮"], "class": ["Y", "C"] }
    },
    "tips": "廉航班次最多、啟動成本最低，新手首選"
  }
}
```

## 貢獻

目前為個人專案的早期階段。歡迎開 Issue 討論功能方向或回報四腿票的實際經驗，特別是：

- 各航空公司最新的中停/轉機規則變動
- 新的外站 × 目的地組合經驗分享
- UI/UX 改善建議

## 授權

MIT License

---

*Built with ☕ in Taiwan*
