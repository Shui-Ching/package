---
name: package-dashboard
description: 把這個專案 README.md 裡的第三方套件表格（正常維護中／已停滯／授權疑慮、跨框架整合對照、風險與替代方案）轉成一份可搜尋篩選的 HTML 頁面，發布成 Artifact 連結給團隊直接看，取代手動貼到 Google 試算表。當使用者說「更新套件管理頁面」「重新產生套件儀表板」「README 改完了，幫我同步一下套件頁面」「套件清單有新增/移除，更新一下團隊看的那份」，或任何要把這個 README 的套件資料重新發布給團隊看的情境，都要使用這個 skill，不要憑印象手動改 HTML。
---

# 套件管理頁面同步

把 `README.md` 的套件稽核資料轉成團隊能直接瀏覽的唯讀 HTML 頁面（搜尋、依狀態篩選），發布到 Artifact，並且**每次重新發布都用同一個連結**——團隊書籤同一個網址就好，不用每次重傳檔案。

## 為什麼要照這個流程

這個頁面唯一的資料真相來源是 `README.md`；頁面裡的 `PACKAGES` 陣列是從 README 表格轉譯出來的**衍生資料**，不是獨立維護的第二份清單。README 更新後才跑這個 skill，不要反過來手動改 HTML 裡的資料再回頭補 README，否則兩邊會分岔，之後沒人知道哪一份才是對的。

## 執行步驟

1. **讀 `README.md`**，找出以下區塊：
   - 「套件清單」下的三個表格：✅ 正常維護中、⚠️ 已停滯、⚠️ 授權疑慮
   - 「跨框架整合套件對照」表（Nuxt 官方模組／Vue 官方整合套件／CDN via jsDelivr 三欄）
   - 「風險與注意事項」章節裡每個套件對應的說明段落
   - 「開源免費替代方案建議」表
   - 文件開頭的「最後查詢時間」「資料來源」「表格收錄範圍」

2. **讀 `output/dashboard.html`**，找到 `<script>` 區塊裡的 `PACKAGES` 陣列。這是唯一需要重寫資料的地方，CSS 與版面結構不用動，除非使用者明確要求改設計。

3. **把 README 資料轉成 `PACKAGES` 陣列的欄位**，每個套件一個物件：

   | 欄位 | 對應 README 內容 | 備註 |
   |---|---|---|
   | `id` | 套件英文名 kebab-case | 例如 `sweetalert2` |
   | `name` | 表格「套件（官網）」欄的顯示名稱 | 不含括號備註 |
   | `isSub` / `subNote` | 只有 Nuxt Swiper、Nuxt V-Calendar 這類「掛在核心套件下方」的子模組才需要 | `subNote` 放括號裡的說明文字 |
   | `homepageUrl` | 官網連結 | |
   | `description` | 「功能描述」欄 | |
   | `npmName` | 「npm 套件名」欄 | |
   | `latestVersion` / `npmLastPublish` / `githubLastUpdate` | 對應欄位原文照抄，含括號裡的年份說明 | |
   | `license` | 「授權」欄；有額外說明時保留原文（例如「⚠️ 見下方說明」），`null` 表示待補 | |
   | `category` | 這個套件在 README 屬於哪個表格：`normal` / `stalled` / `license-risk` | |
   | `licenseFlag` | 只有 README 特別點出授權疑慮的套件才設 `true`（目前是 Animate.css、Isotope、Fancybox） | 用來驅動「只看授權需留意」篩選 |
   | `statusLabel` | 「狀態」欄原文（含 ✅／⚠️ 符號） | |
   | `nuxt` / `vue` / `cdn` | 「跨框架整合套件對照」表裡這個套件對應的三欄內容 | 純 Vue 元件庫（例如 Vue Quilly、V-Calendar 本身）的 `vue` 欄填「不適用（本身即為 Vue 專屬元件庫）」 | |
   | `notes` | 「風險與注意事項」章節裡屬於這個套件的段落，一段一個陣列元素 | 沒有額外說明就不寫這個欄位 |
   | `alternative` | 「開源免費替代方案建議」表裡這個套件對應的那一列，轉成 `{name, url, npmName, license, version, note}` | 沒有建議替代方案就不寫這個欄位 |

   所有文字**照 README 原文轉譯，不要改寫或摘要**——這份頁面是給團隊看的稽核依據，數字和日期錯一個字都是誤導。

4. **更新頁面頂部的 masthead 中繼資料**：`<dl class="masthead-meta">` 裡的「最後查詢時間」要換成 README 最新的日期；如果「資料來源」「收錄範圍」文字也變了，一併同步。

5. **確認 `PACKAGES` 陣列筆數與 README 一致**（README 目前是 18 個核心套件 + 2 個 Nuxt 子模組 = 20 筆）。stat 統計數字（套件總數／正常維護中／已停滯／授權疑慮）是頁面 JS 自動從陣列算出來的，不用手動改。

6. **讀 `state.json`**，拿到 `artifactUrl`。

7. **用 Artifact 工具發布**：`file_path` 指向 `output/dashboard.html`，`url` 帶 `state.json` 裡的 `artifactUrl`（**一定要帶 `url`，不帶的話會建立一個新連結而不是更新原本那個**），`favicon` 沿用 `📦`。

8. **更新 `state.json`**：`lastGeneratedAt` 填今天日期，`lastSourceQueryDate` 填 README 的「最後查詢時間」，`sourcePackageCount` 填目前的套件筆數。

9. **回報使用者**：講清楚這次同步了哪些變動（新增/移除/狀態變更的套件），連結維持不變就直接說「同一個連結」，不要重新貼一次網址造成使用者以為是新連結。

## 邊界情況

- **README 表格結構本身變了**（新增欄位、拆表格、改分類邏輯），不要自己猜著套進現有的 `PACKAGES` schema——先跟使用者確認新結構要怎麼反映在頁面上，schema 要跟著調整時，這份 SKILL.md 的欄位對照表也要同步更新。
- **使用者要開放線上編輯**（例如讓團隊成員直接在頁面上填某個欄位並即時同步給所有人看），這個頁面目前是純讀取的靜態 Artifact，不支援這件事——需要先呼叫 `artifact-capabilities` skill 評估共享狀態機制，屬於另一個決定，不要自己加。
- **頁面的視覺設計**（配色、字體、版面）已經定案，純資料更新不用重新設計；使用者明確要求改版面時才動 CSS，並遵守 `frontend-design` 與 `frontend-standards` 兩支 skill 的規範。
