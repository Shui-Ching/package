# 第三方套件總覽

本文件用於追蹤團隊專案中實際使用的第三方套件，包含目前版本、最新版本、官方維護狀態與授權條款，作為原碼掃描與授權合規檢查的依據。

- **最後查詢時間**：2026-07-27
- **資料來源**：npm registry（`npm view` / `registry.npmjs.org`）、GitHub 官方 API、nuxt.com 官方模組清單、jsDelivr API（`data.jsdelivr.com`）、各套件官方授權頁面
- **「目前用版本」欄位**：需要團隊成員依實際專案回填，本文件建立時尚未取得，先標記為「待補」
- **「跨框架整合套件對照」章節**：因應公司主要透過 Nuxt、Vue、npm、CDN via jsDelivr 四種方式引入套件而新增，用來標註每個套件是否有「官方」維護的 Nuxt 模組或 Vue 整合套件（判定標準：需有明確證據，例如核心套件官方文件／README 直接連結、或發布在同一個 GitHub org／npm maintainer 底下、或 nuxt.com/modules 標註為 Official；純社群第三方維護者不列入，一律標記「無官方」）

## 套件清單

### ✅ 正常維護中

| 套件（官網） | npm 套件名 | 目前用版本 | 最新版本 | npm 最後發布 | GitHub 最後更新 | 授權 | 狀態 |
|---|---|---|---|---|---|---|---|
| [SweetAlert2](https://sweetalert2.github.io/) | `sweetalert2` | 待補 | 11.26.25 | 2026-05-23 | 2026-07-20 | MIT | ✅ 正常，活躍維護 |
| [Bootstrap](https://getbootstrap.com/) | `bootstrap` | 待補 | 5.3.8 | 2026-06-05 | 2026-07-26 | MIT | ✅ 正常，活躍維護 |
| [Vue Quilly](https://vue-quilly.vercel.app/) | `vue-quilly` | 待補 | 1.1.6 | 2025-12-07 | 2026-03-23 | MIT | ✅ 正常，但專案規模小、更新頻率較低，建議留意 |
| [Swiper](https://swiperjs.com/) | `swiper` | 待補 | 14.0.6 | 2026-07-22 | 2026-07-24 | MIT | ✅ 正常，非常活躍 |
| [GSAP](https://gsap.com/) | `gsap` | 待補 | 3.15.0 | 2026-04-13 | 2026-04-13 | 自訂「Standard No Charge License」 | ✅ 授權特殊但確認可商用，見下方說明 |
| [Apache ECharts](https://echarts.apache.org/) | `echarts` | 待補 | 6.1.0 | 2026-05-19 | 2026-07-26 | Apache-2.0 | ✅ 正常，Apache 基金會專案，非常活躍 |
| [FullCalendar](https://fullcalendar.io/) | `fullcalendar` | 待補 | 7.0.2 | 2026-07-24 | 2026-07-24 | MIT | ✅ 正常，非常活躍 |
| [GLightbox](https://biati-digital.github.io/glightbox/) | `glightbox` | 待補 | 3.3.1 | 2025-01-21 | 2025-12-02 | MIT | ✅ 正常，但 npm 發版頻率較低，建議留意 |

### ⚠️ 已停滯（官方維護能量不足）

| 套件（官網） | npm 套件名 | 目前用版本 | 最新版本 | npm 最後發布 | GitHub 最後更新 | 授權 | 狀態 |
|---|---|---|---|---|---|---|---|
| [AOS](https://michalsnik.github.io/aos/) | `aos` | 待補 | 2.3.4 | 2022-06-13（超過 4 年未發版） | 2024-03-26 | MIT | ⚠️ 已停滯，373 個未解決 issue |
| [V-Calendar](https://vcalendar.io/) | `v-calendar` | 待補 | 2.4.2 | 2023-10-13（近 3 年未發版） | 2024-08-07 | MIT | ⚠️ 已停滯，786 個未解決 issue |
| [Magnific Popup](https://dimsemenov.com/plugins/magnific-popup/) | `magnific-popup` | 待補 | 1.2.0 | 2024-06-08（超過 2 年未發版） | 2024-06-08 | MIT | ⚠️ 已停滯，678 個未解決 issue |
| [EasyZoom](https://i-like-robots.github.io/EasyZoom/) | `easyzoom` | 待補 | 2.6.0 | 2022-12-30（超過 3 年未發版） | 2024-06-19 | MIT | ⚠️ 已停滯，超過 3 年未發版 |
| [Animate.css](https://animate.style/) | `animate.css` | 待補 | 4.1.1 | 2020-09-07（超過 5 年未發版，見下方「npm 發布時間修正」說明） | 2024-07-29 | ⚠️ 見下方說明 | ⚠️ 已停滯 + 授權疑慮，見下方說明 |
| [Flatpickr](https://flatpickr.js.org/) | `flatpickr` | 4.6.13 | 4.6.13 | 2022-04-14（超過 4 年未發版，見下方「npm 發布時間修正」說明） | 2024-08-02 | MIT | ⚠️ 已停滯，852 個未解決 issue |

### ⚠️ 授權疑慮（維護狀態正常，但授權條款需留意）

| 套件（官網） | npm 套件名 | 目前用版本 | 最新版本 | npm 最後發布 | GitHub 最後更新 | 授權 | 狀態 |
|---|---|---|---|---|---|---|---|
| [Fancybox](https://fancyapps.com/fancybox/) | `@fancyapps/ui` | 待補 | 6.1.14 | 2026-04-29 | 2026-04-29 | **非開源／需付費授權** | ⚠️ 高風險，見下方說明（維護仍活躍，問題出在授權而非停滯） |

## 跨框架整合套件對照（Nuxt／Vue／CDN via jsDelivr）

公司主要透過 Nuxt、Vue、npm、CDN via jsDelivr 四種方式引入套件，下表整理每個套件在這四種引入方式下的實際狀況。**結論先講**：15 個套件裡，沒有任何一個擁有官方維護的 Nuxt 模組；Vue 官方整合套件也只有 Apache ECharts、FullCalendar 兩個成立，其餘全部是社群第三方維護，依前述嚴格判定標準不列為官方。CDN via jsDelivr 部分，15 個套件全數可透過 jsDelivr 正常取用，但**jsDelivr 本質是 npm 套件的鏡像 CDN，沒有獨立版本號與更新排程**，通常 npm 發布新版後幾分鐘到數小時內會自動同步，因此下表 CDN 欄位不重複列版本號，只註記「跟隨 npm」。

| 套件 | Nuxt 官方模組 | Vue 官方整合套件 | CDN via jsDelivr |
|---|---|---|---|
| SweetAlert2 | 無官方模組 | 無官方整合套件（官方 README 僅列出 React／Angular／Laravel 三個官方整合，`vue-sweetalert2` 屬社群套件） | 可用，跟隨 npm 11.26.25 |
| Bootstrap | 無官方模組 | 無官方整合套件（BootstrapVue／BootstrapVueNext 為獨立社群專案，非 twbs 官方組織維護，且已停止支援 Vue 3） | 可用，跟隨 npm 5.3.8 |
| Vue Quilly | 無官方模組（README 中的「Nuxt Integration」連結僅為 SSR 設定範例專案，未發布成 npm 套件） | 不適用（本身即為 Vue 專屬元件庫） | 可用，跟隨 npm 1.1.6 |
| Swiper | 無官方模組（nuxt.com 上架的 `nuxt-swiper` 官方頁面明確標示為第三方 `@cpreston321` 維護） | 已內建於核心套件（`swiper/vue` entry point 為官方文件指定用法，非獨立套件，版本與核心套件 14.0.6 一致） | 可用，跟隨 npm 14.0.6 |
| GSAP | 無官方模組 | 無官方整合套件（官方僅發布 `@gsap/react`，官方文件明確說明「there isn't an official @gsap/vue package」） | 可用，跟隨 npm 3.15.0 |
| Apache ECharts | 無官方模組（`nuxt-echarts` 為個人維護，非 apache／ecomfe 組織） | ✅ 有 —— `vue-echarts` 8.0.1（GitHub `ecomfe/vue-echarts`，`apache/echarts` 官方 README 直接連結背書；GitHub 最後更新 2026-07-24） | 可用，`echarts`、`vue-echarts` 皆跟隨各自 npm 版本 |
| FullCalendar | 無官方模組（官方文件僅提供 Nuxt 設定範例 repo，非正式模組） | ✅ 有 —— `@fullcalendar/vue3`，npm 最新 7.0.2，同屬官方 GitHub org `fullcalendar`（⚠️ 版本落差，見下方說明） | 可用，跟隨各自 npm 版本 |
| GLightbox | 無官方模組 | 無官方整合套件 | 可用，跟隨 npm 3.3.1 |
| AOS | 無官方模組（`nuxt-aos` 為第三方維護） | 無官方整合套件（`aos-vue` 為第三方維護） | 可用，跟隨 npm 2.3.4 |
| V-Calendar | 無官方模組（`@samk-dev/nuxt-vcalendar` 為第三方維護，非作者 `nathanreyes` 本人） | 不適用（本身即為 Vue 專屬元件庫） | 可用，跟隨 npm 2.4.2 |
| Magnific Popup | 無官方模組 | 無官方整合套件 | 可用，跟隨 npm 1.2.0 |
| EasyZoom | 無官方模組 | 無官方整合套件 | 可用，跟隨 npm 2.6.0 |
| Animate.css | 無官方模組（社群 `nuxt-animate.css` 非官方 org 維護） | 無官方整合套件（`vue-animate-css`、`vue3-animate-css` 皆為個人套件，且分別已 10 年、4 年未更新） | 可用，跟隨 npm 4.1.1 |
| Flatpickr | 無官方模組（`nuxt-flatpickr` 為個人套件，最後發布於 2018 年） | 無官方整合套件（`vue-flatpickr-component` 雖被官方 README「See also」清單收錄推薦，但非官方 org `flatpickr` 發布，依嚴格標準不算官方） | 可用，跟隨 npm 4.6.13 |
| Fancybox | 無官方模組（官方整合頁 `fancybox/integration/nuxt/` 回傳 404） | 無官方整合套件（官方 Vue 整合頁僅提供範例程式碼供自行複製，未發布正式套件） | 技術上可用，但 ⚠️ `@fancyapps/ui` 仍為付費商業授權，CDN 能取得檔案不代表取得合法使用授權，授權風險不因此改變 |

### ⚠️ FullCalendar `@fullcalendar/vue3` 版本號與 GitHub tag 不同步

`@fullcalendar/vue3` 的 npm 最新版本是 `7.0.2`，發布時間與核心套件 `fullcalendar` 一致（約 2026-07-24），但其獨立支援 repo（`fullcalendar/fullcalendar-vue`）GitHub 上最新的 git tag 只到 `v6.1.21`。研判是 FullCalendar 團隊已將 `@fullcalendar/vue3` 的版本號同步進核心 monorepo 的 7.x 版本線一起發布，但這個獨立 repo 本身沒有另外打上對應的 v7 git tag。實務上以 **npm 上的版本號 7.0.2 為準**，但若團隊之後要去 GitHub 對照原始碼或回報 issue，需要知道 tag 顯示的版本會落後、屬正常現象，不代表套件本身沒更新。

### ℹ️ npm 發布時間修正：Animate.css、Flatpickr

在這次查證跨框架整合套件的過程中，意外發現主表原本「npm 最後發布」欄位裡，Animate.css 與 Flatpickr 兩者填的日期其實是 npm registry 的 `time.modified`（套件 metadata 異動時間，例如描述文字被更動），並非真正的版本發布時間 `time[<最新版本>]`。已直接查詢 `registry.npmjs.org` 覆核並修正：

- **Animate.css** `4.1.1`：真正發布時間是 **2020-09-07**（原表誤植為 2022-11-18，兩者相差超過 2 年，代表這個套件已停滯超過 5 年而非原本估計的 3 年多）
- **Flatpickr** `4.6.13`：真正發布時間是 **2022-04-14**（原表誤植為 2022-06-18，相差約 2 個月，停滯年數估計無實質影響）

主表已同步更新為修正後日期。

## 風險與注意事項

### ⚠️ Fancybox（`@fancyapps/ui`）—— 授權風險，需優先確認

官方 [授權頁面](https://fancyapps.com/license/) 明確寫明：

- 每個專案無論類型、位置或法律形式，都需要**有效的付費授權**
- **不可在開源專案中使用**
- 商業用途、公司內網、SaaS 產品皆需購買「商業授權」或「商業擴展授權」

若團隊目前是直接引用但尚未購買授權，屬於實際法遵風險，建議優先跟法務／PM 確認授權狀態。如需替換，MIT 授權的同類型 lightbox 套件（例如 GLightbox、PhotoSwipe）可列入評估。

### ⚠️ AOS、V-Calendar、Magnific Popup、EasyZoom、Animate.css、Flatpickr —— 維護停滯風險

這六個套件最後一次 npm 發版都超過一年（AOS 已逾 4 年、V-Calendar 近 3 年、Magnific Popup 超過 2 年、EasyZoom、Animate.css 與 Flatpickr 皆超過 3 年），代表官方維護能量可能不足，長期使用有安全性更新跟不上的風險。其中 AOS、V-Calendar、Magnific Popup、Flatpickr 四者 GitHub 上待處理 issue 數量偏高（分別為 373、786、678、852 個）；EasyZoom 待處理 issue 僅 8 個，數量不高，但也已超過 3 年沒有新版發布，同樣建議列入觀察。建議團隊評估是否需要尋找替代方案（例如 Magnific Popup、EasyZoom 可考慮 PhotoSwipe 等仍活躍的同類套件；Flatpickr 可考慮仍活躍維護的 Vanilla Calendar Pro 或 Cally 等日期選擇器套件），或接受此風險並列管觀察。

### ⚠️ Animate.css —— GitHub 原始碼授權已改為 Hippocratic License 2.1，與目前 npm 發布版本的 MIT 不一致

查證時發現一個授權疑慮，需要提醒：

- 目前 npm 上發布的 `animate.css` 套件（4.1.1 版，2022-11-18 發布）`package.json` 內宣告授權為 **MIT**，屬標準開源授權，可安心使用。
- 但 GitHub 官方 repo 的 `main` 分支（尚未發布到 npm 的最新原始碼）已將授權改為 **Hippocratic License 2.1**，這是一種非 OSI 認可的「倫理來源（ethical source）」授權，附加了使用者需遵守人權相關條款的限制，**不是標準的寬鬆式開源授權**，也是 GitHub API 無法辨識其 SPDX 授權代碼（顯示 `NOASSERTION`）的原因。
- 換句話說：**只要團隊是透過 npm 安裝目前版本，授權仍是 MIT，沒有問題**；但如果未來套件從 GitHub 直接引用原始碼、或 npm 發布新版本沿用 repo 目前的授權條款，屆時的授權條件會改變，需要重新確認是否符合公司法遵要求。
- 建議：安裝時鎖定目前 npm 上的 4.1.1（MIT）版本，並在下次此表格例行更新查核時，特別留意 `animate.css` 的授權欄位是否隨新版發布而變動。

### ℹ️ GSAP —— 授權文字非標準 MIT，但確認可商用

GSAP 官方 [授權頁面](https://gsap.com/licensing/) 說明目前所有外掛（含過去付費的 SplitText、MorphSVG）皆已納入免費標準授權，商業用途、SaaS 產品都涵蓋在內。唯一限制是不能用來開發與 Webflow 競爭的視覺化動畫建構工具，與一般前端專案使用情境無關。若原碼掃描工具因授權文字非標準 SPDX 格式而標記為風險，屬於誤報，可備註說明。

## 如何更新這份表格

為避免資料手動維護後跟實際套件狀態脫鉤，建議定期（例如每季）用以下指令重新查詢，而不是憑印象修改：

```bash
# 查詢單一套件的最新版本、最後發布時間、授權
npm view <套件名> version time.modified license

# 查詢 GitHub repo 是否已封存、最後一次程式碼異動時間
curl -s "https://api.github.com/repos/<擁有者>/<repo名稱>" \
  -H "Accept: application/vnd.github+json" \
  | node -e "let d='';process.stdin.on('data',c=>d+=c);process.stdin.on('end',()=>{const j=JSON.parse(d);console.log(JSON.stringify({archived:j.archived,pushed_at:j.pushed_at,open_issues:j.open_issues_count}))})"
```

「目前用版本」欄位無法自動查詢，需要對照各專案的 `package.json` 或 CDN 引用網址手動回填。
