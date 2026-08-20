---
name: package-dashboard
description: 只要使用者丟一個套件名稱（例如「加入 Pinia」「查一下 dayjs 能不能用」「plyr 更新一下版本」），就自動查證這個套件的版本／維護狀態／授權／跨框架整合狀況，寫進 `output/dashboard.html` 的 `PACKAGES` 陣列，發布成可搜尋篩選的 Artifact（連結保持不變），並自動 git commit。也適用於既有套件的更新、移除、狀態重新查核。當使用者說「更新套件管理頁面」「重新產生套件儀表板」「新增一個套件到清單」「某個套件的版本／狀態要更新」「套件清單有新增/移除，更新一下團隊看的那份」，或任何要新增、修改、移除套件資料並重新發布給團隊看的情境，都要使用這個 skill，不要憑印象手動改 HTML，也不要去改 README.md 的套件表格（README 已經不維護完整資料，只是簡單說明文件）。
---

# 套件管理頁面同步

`output/dashboard.html` 裡的 `PACKAGES` 陣列是這份套件稽核資料的**唯一真相來源**。整套流程設計成「使用者只給套件名稱，其餘全自動」：查證資料 → 寫入 `PACKAGES` → 發布同一個 Artifact 連結 → git commit，取代過去「填 Excel → 貼 AI 分析 → 推 git → 回貼 Excel」四步驟手動流程。`README.md` 只是一份簡單說明文件（專案用途 + 連結 + 資料來源方法論指標），不放完整套件表格，不用跟著同步。

## 為什麼是這個流程

這份資料最早是先寫在 `README.md` 的 Markdown 表格裡，再靠這個 skill 轉譯進 `PACKAGES` 陣列，改資料前還要先手動查 npm/GitHub、填 Excel、貼給 AI。這中間每一段轉手都是一次分岔風險（表格改了忘記重新產生頁面、Excel 跟 repo 不同步）。現在做法反過來：只維護 `PACKAGES` 這一份資料，查證與寫入都由這個 skill 直接完成，使用者只需要給套件名稱、其餘交給 skill 判斷。

## `PACKAGES` 陣列欄位說明

新增或修改套件時，每個套件是陣列裡的一個物件，欄位如下：

| 欄位 | 內容 | 備註 |
|---|---|---|
| `id` | 套件英文名 kebab-case | 例如 `sweetalert2` |
| `name` | 套件顯示名稱 | 不含括號備註 |
| `isSub` / `subNote` | 只有「掛在核心套件下方」的子模組才需要（例如 Nuxt Swiper 掛在 Swiper 下方） | `subNote` 放括號裡的說明文字，例如「Swiper 的 Nuxt 模組，第三方 @cpreston321 維護」 |
| `homepageUrl` | 官網連結 | |
| `description` | 一句話功能描述 | |
| `npmName` | npm 套件名 | |
| `latestVersion` / `npmLastPublish` / `githubLastUpdate` | 最新版本、npm 最後發布時間、GitHub 最後更新時間 | 停滯或有疑慮時可在字串裡加註年份說明，例如「2022-06-13（超過 4 年未發版）」 |
| `license` | 授權條款 | 有額外說明時填「⚠️ 見下方說明」並在 `notes` 裡補充；`null` 表示待補 |
| `category` | `normal`（正常維護中）／`stalled`（已停滯）／`license-risk`（授權疑慮） | 驅動篩選按鈕與統計數字，改變套件狀態時記得同步改這欄 |
| `licenseFlag` | 授權需要特別留意時設 `true` | 驅動「只看授權需留意」篩選 |
| `statusLabel` | 狀態欄顯示文字（含 ✅／⚠️ 符號） | |
| `nuxt` / `vue` / `cdn` | 跨框架整合對照：Nuxt 官方模組、Vue 官方整合套件、CDN via jsDelivr 各自的狀況 | 純 Vue 元件庫（例如本身即為 Vue 專屬元件庫的套件）`vue` 欄填「不適用（本身即為 Vue 專屬元件庫）」 |
| `notes` | 額外說明段落，一段一個陣列元素 | 沒有額外說明就不寫這個欄位 |
| `alternative` | 建議替代方案，`{name, url, npmName, license, version, note}` | **`category` 是 `stalled` 或 `license-risk` 時必填**（不能採用的套件一定要有替代方案候選，見下方「不能採用時必須找替代方案」）；`normal` 分類沒有建議替代方案就不寫這個欄位 |

所有文字**盡量查證後填寫，不要憑印象亂填**——這份頁面是給團隊看的稽核依據，數字和日期錯一個字都是誤導。查證方法（npm registry、GitHub API）見下方「如何查證套件狀態」。

## 執行步驟

1. **確認套件識別資訊**：使用者只給中文俗名或模糊描述時，先確認 npm 套件名與官網（可用 `npm view <猜測的套件名>` 試查，或 WebSearch 找官網）。找不到明確對應的套件就先跟使用者確認，不要用猜的名稱硬寫進資料。
2. **查證套件狀態**：依「如何查證套件狀態」一節，查 npm registry 與 GitHub API，拿到最新版本、npm 最後發布時間、GitHub 最後更新時間、待處理 issue 數、授權條款。
3. **判斷 `category`**：
   - npm 最後發版與 GitHub 最後更新都在合理區間（無公版標準，但可參考既有資料：超過 1～2 年沒發版、且 issue 堆積明顯，通常判定為 `stalled`）→ 已停滯
   - 授權條款不是標準寬鬆式開源（GPL 需開源回饋、自訂商業授權、非開源需付費等）→ `license-risk`，並設 `licenseFlag: true`
   - 其餘 → `normal`
   - 不確定時把查到的原始資料攤開跟使用者確認分類，不要自己武斷下判斷
4. **不能採用時必須找替代方案**：只要判定為 `stalled`（太久沒維護／沒更新時間過長）或 `license-risk`（非開源／需付費），這個套件就是「不建議直接採用」——**不可以只回報「這套件不能用」就結束**，一定要接著查證至少一個「仍持續更新維護、且免費（MIT／Apache／BSD 等標準寬鬆式開源）」的替代方案，用同一套「如何查證套件狀態」方法確認它的最新版本、npm 發布時間、GitHub 最後更新、授權，填進 `alternative` 欄位（`{name, url, npmName, license, version, note}`）。找不到夠格的替代方案時，明確跟使用者說「查過但沒找到活躍維護的免費替代品」，而不是漏掉這一步。回報使用者時（見步驟 13）要把「原套件不能用」與「建議改用什麼」放在同一句話講完，不要拆開讓使用者自己拼湊結論。
5. **查證跨框架整合欄位（`nuxt` / `vue` / `cdn`）**：判定「官方」的標準要嚴格——需有明確證據（核心套件官方文件／README 直接連結、發布在同一個 GitHub org／npm maintainer 底下、或 nuxt.com/modules 標註為 Official），純社群第三方維護者一律標記「無官方」。CDN 欄位若能透過 jsDelivr 取得，寫「可用，跟隨 npm `<版本號>`」。
6. **讀 `output/dashboard.html`**，找到 `<script>` 區塊裡的 `PACKAGES` 陣列，依上表欄位對照新增／修改／刪除對應的套件物件。CSS 與版面結構不用動，除非使用者明確要求改設計。
7. **如果新增或移除套件，順手檢查**：
   - `category` 分類是否正確（會直接影響篩選按鈕與統計數字，兩者都是頁面 JS 自動算的，不用手動改）
   - `stalled` / `license-risk` 的套件是否已依步驟 4 填好 `alternative`
8. **更新頁面頂部 masthead 的「最後查詢時間」**（`<dl class="masthead-meta">` 裡）為今天日期。
9. **讀 `state.json`**，拿到 `artifactUrl`。
10. **用 Artifact 工具發布**：`file_path` 指向 `output/dashboard.html`，`url` 帶 `state.json` 裡的 `artifactUrl`（**一定要帶 `url`，不帶的話會建立一個新連結而不是更新原本那個，使用者要求過連結必須維持一致**），`favicon` 沿用 `📦`。
11. **更新 `state.json`**：`lastGeneratedAt` 填今天日期，`lastSourceQueryDate` 填這次查證資料的日期，`sourcePackageCount` 填目前的套件筆數。
12. **git commit（僅 commit，不 push）**：`git add` 異動到的檔案（`output/dashboard.html`、`state.json`，若 README 有改也一併加入），用能清楚說明這次新增/更新/移除了哪個套件的訊息建立 commit。**不要 push**——使用者已明確要求這一步只自動 commit 到本地，push 由使用者自行決定時機執行。
13. **回報使用者**：講清楚這次新增/移除/狀態變更了哪些套件（含查到的版本、維護狀態、授權結論）；套件屬於 `stalled` 或 `license-risk` 時，在同一句話裡把「為什麼不能用」跟「建議改用什麼套件」一起講完，不要分開讓使用者自己拼湊。連結維持不變就直接說「同一個連結」，不要重新貼一次網址造成使用者以為是新連結；並提醒變更已 commit 但尚未 push。

## 如何查證套件狀態

不要憑印象或記憶填版本、日期、授權，改資料前先用以下指令查證：

```bash
# 查詢單一套件的最新版本、最後發布時間、授權
npm view <套件名> version time.modified license

# 查詢 GitHub repo 是否已封存、最後一次程式碼異動時間
curl -s "https://api.github.com/repos/<擁有者>/<repo名稱>" \
  -H "Accept: application/vnd.github+json" \
  | node -e "let d='';process.stdin.on('data',c=>d+=c);process.stdin.on('end',()=>{const j=JSON.parse(d);console.log(JSON.stringify({archived:j.archived,pushed_at:j.pushed_at,open_issues:j.open_issues_count}))})"
```

`npm view` 的 `time.modified` 是套件 metadata 異動時間（可能只是描述文字被改），不一定等於真正的版本發布時間；要精確查發布時間用 `npm view <套件名> time.<版本號>`，或直接查 `registry.npmjs.org/<套件名>` 的 `time` 欄位。

## 邊界情況

- **使用者想改 `README.md`**：README 現在只放專案用途、儀表板連結、資料來源方法論這類不常變的說明文字，不放套件明細。如果使用者要求把套件細節寫回 README，先跟使用者確認是否真的要恢復雙重維護，因為那正是這次改流程想避免的問題。
- **使用者要開放線上編輯**（例如讓團隊成員直接在頁面上填某個欄位並即時同步給所有人看），這個頁面目前是純讀取的靜態 Artifact，不支援這件事——需要先呼叫 `artifact-capabilities` skill 評估共享狀態機制，屬於另一個決定，不要自己加。
- **頁面的視覺設計**（配色、字體、版面）已經定案，純資料更新不用重新設計；使用者明確要求改版面時才動 CSS，並遵守 `frontend-design` 與 `frontend-standards` 兩支 skill 的規範。
