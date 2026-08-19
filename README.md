# 第三方套件總覽

本文件用於追蹤團隊專案中實際使用的第三方套件，包含最新版本、官方維護狀態與授權條款，作為原碼掃描與授權合規檢查的依據。

- **最後查詢時間**：2026-07-28
- **資料來源**：npm registry（`npm view` / `registry.npmjs.org`）、GitHub 官方 API、nuxt.com 官方模組清單、jsDelivr API（`data.jsdelivr.com`）、各套件官方授權頁面
- **表格欄位結構**：以團隊 Google Sheet（三個工作表：正常維護中／已停滯／授權疑慮）的七欄「套件（官網）、npm 套件名、最新版本、npm 最後發布、GitHub 最後更新、授權、狀態」為基礎，另新增「功能描述」欄（放在「套件（官網）」之後），共八欄，方便快速辨識每個套件的用途
- **表格收錄範圍**：19 個核心套件，外加 2 個團隊實際引入的 Nuxt 模組（`nuxt-swiper`、`@samk-dev/nuxt-vcalendar`），列在各自對應的核心套件下方
- **「跨框架整合套件對照」章節**：因應公司主要透過 Nuxt、Vue、npm、CDN via jsDelivr 四種方式引入套件而新增，用來標註每個套件是否有「官方」維護的 Nuxt 模組或 Vue 整合套件（判定標準：需有明確證據，例如核心套件官方文件／README 直接連結、或發布在同一個 GitHub org／npm maintainer 底下、或 nuxt.com/modules 標註為 Official；純社群第三方維護者不列入，一律標記「無官方」）。上方套件清單不另設 Nuxt／Vue 欄位，整合狀況一律以該章節為準

## 套件清單

### ✅ 正常維護中

| 套件（官網） | 功能描述 | npm 套件名 | 最新版本 | npm 最後發布 | GitHub 最後更新 | 授權 | 狀態 |
|---|---|---|---|---|---|---|---|
| [SweetAlert2](https://sweetalert2.github.io/) | 客製化彈出視窗與警示訊息（alert／confirm／toast）元件庫，取代瀏覽器原生 alert | `sweetalert2` | 11.26.25 | 2026-05-23 | 2026-07-20 | MIT | ✅ 正常，活躍維護 |
| [Bootstrap](https://getbootstrap.com/) | CSS／JS UI 框架，提供網格系統、預設元件樣式與響應式版面工具 | `bootstrap` | 5.3.8 | 2026-06-05 | 2026-07-26 | MIT | ✅ 正常，活躍維護 |
| [Vue Quilly](https://vue-quilly.vercel.app/) | Quill 富文本編輯器的 Vue 3 元件包裝，讓 Quill 能以 Vue 元件形式直接使用 | `vue-quilly` | 1.1.6 | 2025-12-07 | 2026-03-23 | MIT | ✅ 正常，但專案規模小、更新頻率較低，建議留意 |
| [Quill](https://quilljs.com/) | 富文本編輯器（WYSIWYG）核心引擎，提供可自訂的內容編輯與格式化功能 | `quill` | 2.0.3 | 2024-11-30（近 1 年 8 個月未發版） | 2025-07-25 | BSD-3-Clause | ✅ 正常，但 npm 發版頻率低，建議留意（見下方說明） |
| [Swiper](https://swiperjs.com/) | 觸控滑動輪播元件，支援圖片輪播、多頁籤切換等多種滑動互動情境 | `swiper` | 14.0.6 | 2026-07-22 | 2026-07-24 | MIT | ✅ 正常，非常活躍 |
| [Nuxt Swiper](https://github.com/cpreston321/nuxt-swiper)（Swiper 的 Nuxt 模組，第三方 `@cpreston321` 維護） | Swiper 的 Nuxt 模組封裝，簡化在 Nuxt 專案中安裝與設定 Swiper 的流程 | `nuxt-swiper` | 2.0.2 | 2026-05-18 | 2026-07-27 | 待補 | ✅ 正常，維護活躍，但非 Swiper 官方模組（見下方對照章節） |
| [GSAP](https://gsap.com/) | JavaScript 動畫引擎，用於製作高效能的網頁動畫與時間軸控制 | `gsap` | 3.15.0 | 2026-04-13 | 2026-04-13 | 自訂「Standard No Charge License」 | ✅ 授權特殊但確認可商用，見下方說明 |
| [Apache ECharts](https://echarts.apache.org/) | 資料視覺化圖表庫，提供折線圖、長條圖、地圖等多種圖表類型 | `echarts` | 6.1.0 | 2026-05-19 | 2026-07-26 | Apache-2.0 | ✅ 正常，Apache 基金會專案，非常活躍 |
| [FullCalendar](https://fullcalendar.io/) | 行事曆／排程元件，支援月/週/日檢視、事件拖曳與跨資源排程 | `fullcalendar` | 7.0.2 | 2026-07-24 | 2026-07-24 | MIT | ✅ 正常，非常活躍 |
| [GLightbox](https://biati-digital.github.io/glightbox/) | 圖片／影片燈箱（lightbox）彈出檢視元件，用於放大瀏覽媒體內容 | `glightbox` | 3.3.1 | 2025-01-21 | 2025-12-02 | MIT | ✅ 正常，但 npm 發版頻率較低，建議留意 |
| [Shuffle.js](https://shuffle.js.org) | 網格版面篩選、排序與動態佈局函式庫，官方定位為 Isotope／Packery 的替代品，用於分類展示卡片式內容（見下方 Isotope 替代方案說明） | `shufflejs` | 7.0.0 | 2026-02-13 | 2026-05-12 | MIT | ✅ 正常，活躍維護，無 jQuery 或其他 runtime 相依，內建 TypeScript 型別 |

### ⚠️ 已停滯（官方維護能量不足）

| 套件（官網） | 功能描述 | npm 套件名 | 最新版本 | npm 最後發布 | GitHub 最後更新 | 授權 | 狀態 |
|---|---|---|---|---|---|---|---|
| [AOS](https://michalsnik.github.io/aos/) | 捲動觸發動畫效果庫（Animate On Scroll），元素捲動進入視窗時觸發動畫 | `aos` | 2.3.4 | 2022-06-13（超過 4 年未發版） | 2024-03-26 | MIT | ⚠️ 已停滯，373 個未解決 issue |
| [V-Calendar](https://vcalendar.io/) | Vue 日期選擇與行事曆元件，支援日期範圍選取與行事曆檢視 | `v-calendar` | 2.4.2 | 2023-10-13（近 3 年未發版） | 2024-08-07 | MIT | ⚠️ 已停滯，786 個未解決 issue |
| [Nuxt V-Calendar](https://github.com/samk-dev/nuxt-vcalendar)（V-Calendar 的 Nuxt 模組，第三方 `samk-dev` 維護） | V-Calendar 的 Nuxt 模組封裝，簡化在 Nuxt 專案中安裝與設定 V-Calendar 的流程 | `@samk-dev/nuxt-vcalendar` | 1.0.4 | 2024-07-13（近 2 年未發版） | 2024-07-30 | 待補 | ⚠️ 已停滯，維護狀態與核心套件 V-Calendar 一致 |
| [Magnific Popup](https://dimsemenov.com/plugins/magnific-popup/) | 響應式燈箱（lightbox）彈出視窗外掛，支援圖片、影片、iframe 等內容展示 | `magnific-popup` | 1.2.0 | 2024-06-08（超過 2 年未發版） | 2024-06-08 | MIT | ⚠️ 已停滯，678 個未解決 issue |
| [EasyZoom](https://i-like-robots.github.io/EasyZoom/) | 圖片局部放大鏡效果外掛，滑鼠移入時放大顯示圖片細節 | `easyzoom` | 2.6.0 | 2022-12-30（超過 3 年未發版） | 2024-06-19 | MIT | ⚠️ 已停滯，超過 3 年未發版 |
| [Animate.css](https://animate.style/) | 純 CSS 動畫效果類別庫，套用預設 class 即可讓元素套用動畫效果 | `animate.css` | 4.1.1 | 2020-09-07（超過 5 年未發版，見下方「npm 發布時間修正」說明） | 2024-07-29 | ⚠️ 見下方說明 | ⚠️ 已停滯 + 授權疑慮，見下方說明 |
| [Flatpickr](https://flatpickr.js.org/) | 輕量日期／時間選擇器，無其他相依套件，支援多種日期格式與範圍選取 | `flatpickr` | 4.6.13 | 2022-04-14（超過 4 年未發版，見下方「npm 發布時間修正」說明） | 2024-08-02 | MIT | ⚠️ 已停滯，852 個未解決 issue |
| [Vue Easy Lightbox](https://onycat.com/vue-easy-lightbox/) | Vue 3 圖片燈箱（lightbox）元件，支援縮放、拖曳、旋轉與多圖切換 | `vue-easy-lightbox` | 1.19.0 | 2024-03-05（近 2 年 5 個月未發版） | 2024-04-03 | MIT | ⚠️ 已停滯，GitHub 亦逾 2 年無 commit，2026 年的社群修正 PR 未被處理（見下方說明） |
| [Isotope](https://isotope.metafizzy.co/) | 網格版面篩選、排序與動態佈局函式庫，支援 masonry（不同高度自動填補間隙）等多種版面模式 | `isotope-layout` | 3.0.6 | 2018-04-06（超過 8 年未發版） | 2021-09-24（超過 4 年未更新） | ⚠️ 見下方說明 | ⚠️ 已停滯 + 授權疑慮，見下方說明 |

### ⚠️ 授權疑慮（維護狀態正常，但授權條款需留意）

| 套件（官網） | 功能描述 | npm 套件名 | 最新版本 | npm 最後發布 | GitHub 最後更新 | 授權 | 狀態 |
|---|---|---|---|---|---|---|---|
| [Fancybox](https://fancyapps.com/fancybox/) | 圖片／影片／內容燈箱（lightbox）展示元件，支援畫廊瀏覽與多媒體嵌入 | `@fancyapps/ui` | 6.1.14 | 2026-04-29 | 2026-04-29 | **非開源／需付費授權** | ⚠️ 高風險，見下方說明（維護仍活躍，問題出在授權而非停滯） |

## 跨框架整合套件對照（Nuxt／Vue／CDN via jsDelivr）

公司主要透過 Nuxt、Vue、npm、CDN via jsDelivr 四種方式引入套件，下表整理每個套件在這四種引入方式下的實際狀況。**結論先講**：19 個套件裡，沒有任何一個擁有官方維護的 Nuxt 模組；Vue 官方整合套件也只有 Apache ECharts、FullCalendar 兩個成立，其餘全部是社群第三方維護，依前述嚴格判定標準不列為官方。CDN via jsDelivr 部分，19 個套件全數可透過 jsDelivr 正常取用，但**jsDelivr 本質是 npm 套件的鏡像 CDN，沒有獨立版本號與更新排程**，通常 npm 發布新版後幾分鐘到數小時內會自動同步，因此下表 CDN 欄位不重複列版本號，只註記「跟隨 npm」。

| 套件 | Nuxt 官方模組 | Vue 官方整合套件 | CDN via jsDelivr |
|---|---|---|---|
| SweetAlert2 | 無官方模組 | 無官方整合套件（官方 README 僅列出 React／Angular／Laravel 三個官方整合，`vue-sweetalert2` 屬社群套件） | 可用，跟隨 npm 11.26.25 |
| Bootstrap | 無官方模組 | 無官方整合套件（BootstrapVue／BootstrapVueNext 為獨立社群專案，非 twbs 官方組織維護，且已停止支援 Vue 3） | 可用，跟隨 npm 5.3.8 |
| Vue Quilly | 無官方模組（README 中的「Nuxt Integration」連結僅為 SSR 設定範例專案，未發布成 npm 套件） | 不適用（本身即為 Vue 專屬元件庫） | 可用，跟隨 npm 1.1.6 |
| Swiper | 無官方模組（nuxt.com 上架的 `nuxt-swiper` 官方頁面明確標示為第三方 `@cpreston321` 維護；npm 最新 2.0.2，2026-05-18 發布，GitHub 最後更新 2026-07-27，維護活躍） | 已內建於核心套件（`swiper/vue` entry point 為官方文件指定用法，非獨立套件，版本與核心套件 14.0.6 一致） | 可用，跟隨 npm 14.0.6 |
| Quill | 無官方模組 | 無官方整合套件（官方僅提供 vanilla JS API；團隊使用的 `vue-quilly` 為第三方 `alekswebnet` 維護，非 Quill 官方 org `slab`，另見上方 Vue Quilly 專列） | 可用，跟隨 npm 2.0.3 |
| GSAP | 無官方模組 | 無官方整合套件（官方僅發布 `@gsap/react`，官方文件明確說明「there isn't an official @gsap/vue package」） | 可用，跟隨 npm 3.15.0 |
| Apache ECharts | 無官方模組（`nuxt-echarts` 為個人維護，非 apache／ecomfe 組織） | ✅ 有 —— `vue-echarts` 8.0.1（GitHub `ecomfe/vue-echarts`，`apache/echarts` 官方 README 直接連結背書；GitHub 最後更新 2026-07-24） | 可用，`echarts`、`vue-echarts` 皆跟隨各自 npm 版本 |
| FullCalendar | 無官方模組（官方文件僅提供 Nuxt 設定範例 repo，非正式模組） | ✅ 有 —— `@fullcalendar/vue3`，npm 最新 7.0.2，同屬官方 GitHub org `fullcalendar`（⚠️ 版本落差，見下方說明） | 可用，跟隨各自 npm 版本 |
| GLightbox | 無官方模組 | 無官方整合套件 | 可用，跟隨 npm 3.3.1 |
| Shuffle.js | 無官方模組 | 無官方整合套件（`@dmstr/vue-shufflejs-plugin` 為第三方 `dmstr` 維護，非作者 `glen-cheney` 本人，且宣告 Bootstrap 為 peerDependency） | 可用，跟隨 npm 7.0.0 |
| AOS | 無官方模組（`nuxt-aos` 為第三方維護） | 無官方整合套件（`aos-vue` 為第三方維護） | 可用，跟隨 npm 2.3.4 |
| V-Calendar | 無官方模組（`@samk-dev/nuxt-vcalendar` 為第三方維護，非作者 `nathanreyes` 本人；npm 最新 1.0.4，2024-07-13 發布，近 2 年未更新，GitHub 最後更新同為 2024-07-30，維護狀態與核心套件 V-Calendar 一致停滯） | 不適用（本身即為 Vue 專屬元件庫） | 可用，跟隨 npm 2.4.2 |
| Magnific Popup | 無官方模組 | 無官方整合套件 | 可用，跟隨 npm 1.2.0 |
| EasyZoom | 無官方模組 | 無官方整合套件 | 可用，跟隨 npm 2.6.0 |
| Animate.css | 無官方模組（社群 `nuxt-animate.css` 非官方 org 維護） | 無官方整合套件（`vue-animate-css`、`vue3-animate-css` 皆為個人套件，且分別已 10 年、4 年未更新） | 可用，跟隨 npm 4.1.1 |
| Flatpickr | 無官方模組（`nuxt-flatpickr` 為個人套件，最後發布於 2018 年） | 無官方整合套件（`vue-flatpickr-component` 雖被官方 README「See also」清單收錄推薦，但非官方 org `flatpickr` 發布，依嚴格標準不算官方） | 可用，跟隨 npm 4.6.13 |
| Vue Easy Lightbox | 無官方模組（`nuxt-easy-lightbox` 1.1.0 為第三方 `modbender` 維護，非作者 XiongAmao 本人；MIT 授權，2025-07-30 發布，GitHub 最後更新 2026-06-16，模組本身仍有維護，但其相依為 `vue-easy-lightbox@^1.19.0`，核心套件的停滯狀態會直接繼承下來） | 不適用（本身即為 Vue 專屬元件庫） | 可用，跟隨 npm 1.19.0 |
| Isotope | 無官方模組（僅有社群範例專案示範如何在 Nuxt 中引入，非正式模組） | 無官方整合套件（`vueisotope` 為第三方 `David-Desmaisons` 維護，`vuxtras` 亦為第三方套件合集，皆非 Metafizzy 官方 org） | 可用，跟隨 npm 3.0.6（8 年未更新的舊版本） |
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

### ⚠️ Vue Easy Lightbox —— 維護停滯，但授權與相依皆無疑慮

`vue-easy-lightbox` 最後一次 npm 發版為 2024-03-05（1.19.0），GitHub `main` 分支最後一次 commit 也是同一天，`pushed_at` 為 2024-04-03，屬於「npm 與原始碼一起停滯」的型態。未解決 issue 僅 26 個，數量不高，但 2026 年仍有新 issue 進來（#158 觸控板縮放連帶觸發整頁縮放、#160 pinch zoom 上限），社群針對 #158 送出的修正 PR #159 自 2026-02-26 起未被合併也未獲回覆，判定維護者已停止投入。此套件 npm 月下載量仍有約 27.8 萬次，屬於「使用量高但已無人維護」的類型。

不過此套件風險輪廓與 AOS、Flatpickr 不同：它沒有任何 runtime dependency，僅宣告 peerDependency `vue: ^3.0.0`，停滯不會帶進 transitive 相依的未修補漏洞；授權為標準 MIT，npm 與 GitHub 宣告一致，法遵層面無疑慮。實際暴露點是 Vue 3 後續 minor 版本的相容性未經測試，以及瀏覽器行為變更造成的互動 bug 不會再修。

Vue 2 專案若使用 `vue2` dist-tag 的 0.23.0（2023-02-28 發布），停滯時間更長，加上 Vue 2 官方支援已於 2023-12-31 結束，建議直接視為不可續用。

另註：本套件官網 `https://onycat.com/vue-easy-lightbox/` 是作者自架的 GitHub Pages 自訂網域，原 `xiongamao.github.io/vue-easy-lightbox/` 會以 HTTP 301 導向此網址，兩者為同一份官方文件，npm `package.json` 的 `homepage` 欄位仍停留在舊網址未更新。

### ⚠️ Animate.css —— GitHub 原始碼授權已改為 Hippocratic License 2.1，與目前 npm 發布版本的 MIT 不一致

查證時發現一個授權疑慮，需要提醒：

- 目前 npm 上發布的 `animate.css` 套件（4.1.1 版，2022-11-18 發布）`package.json` 內宣告授權為 **MIT**，屬標準開源授權，可安心使用。
- 但 GitHub 官方 repo 的 `main` 分支（尚未發布到 npm 的最新原始碼）已將授權改為 **Hippocratic License 2.1**，這是一種非 OSI 認可的「倫理來源（ethical source）」授權，附加了使用者需遵守人權相關條款的限制，**不是標準的寬鬆式開源授權**，也是 GitHub API 無法辨識其 SPDX 授權代碼（顯示 `NOASSERTION`）的原因。
- 換句話說：**只要團隊是透過 npm 安裝目前版本，授權仍是 MIT，沒有問題**；但如果未來套件從 GitHub 直接引用原始碼、或 npm 發布新版本沿用 repo 目前的授權條款，屆時的授權條件會改變，需要重新確認是否符合公司法遵要求。
- 建議：安裝時鎖定目前 npm 上的 4.1.1（MIT）版本，並在下次此表格例行更新查核時，特別留意 `animate.css` 的授權欄位是否隨新版發布而變動。

### ⚠️ Isotope（`isotope-layout`）—— 已停滯逾 8 年，且授權為 GPLv3／付費雙軌制

查證官方 [授權頁面](https://isotope.metafizzy.co/license.html) 與 npm registry、GitHub API：

- npm 最新版本 `3.0.6` 於 **2018-04-06** 發布，至今超過 8 年未發版；GitHub `metafizzy/isotope` 最後一次程式碼異動是 **2021-09-24**，也已超過 4 年，屬於「npm 與原始碼一起停滯」的型態，目前待處理 issue 有 76 個。
- 授權採**雙軌制**：npm `package.json` 宣告為 **GPL-3.0**，代表若團隊願意將使用 Isotope 的專案原始碼一併以 GPLv3 公開釋出，理論上可免費使用；但官方授權頁面明確寫明，只要是「領薪水執行的工作、其中一部分是實作 Isotope」，就需要**商業授權**，也就是一般公司內部或商業專案（不打算把自己的程式碼一併開源）必須付費（依開發者人數分級：個人 25 美元／團隊 8 人 110 美元／組織無上限 320 美元，2026-08-19 查證金額）。
- 綜合兩點：這是「已停滯」與「授權疑慮」同時成立的套件，風險層級高於單純授權疑慮但仍活躍維護的 Fancybox，也高於單純停滯但授權單純的 AOS 等套件。
- 查證時另比對常見的同類替代方案 [Muuri](https://github.com/haltu/muuri)（star 數 10,943，遠高於下方建議的 Shuffle.js）：GitHub 顯示最後 push 時間為 2024-05-25，但 npm 最新版本 `0.9.5` 實際發布於 **2021-07-09**，同樣超過 5 年未發版，與 `animate.css` 案例相同屬於「GitHub 時間戳記比 npm 版本新，但核心功能其實已久未更新」的陷阱，因此未列入下方替代方案表格的建議選項。

建議：若團隊目前仍在使用 Isotope 且未購買授權，同樣建議優先跟法務／PM 確認授權狀態；技術替代方案見下方「開源免費替代方案建議」。

### ℹ️ GSAP —— 授權文字非標準 MIT，但確認可商用

GSAP 官方 [授權頁面](https://gsap.com/licensing/) 說明目前所有外掛（含過去付費的 SplitText、MorphSVG）皆已納入免費標準授權，商業用途、SaaS 產品都涵蓋在內。唯一限制是不能用來開發與 Webflow 競爭的視覺化動畫建構工具，與一般前端專案使用情境無關。若原碼掃描工具因授權文字非標準 SPDX 格式而標記為風險，屬於誤報，可備註說明。

### ℹ️ Quill —— npm 發版頻率低，但 GitHub 原始碼持續開發中；授權與 Vue Quilly 不同（皆屬寬鬆開源，無疑慮）

Quill（`quill`，團隊透過 Vue Quilly 間接使用的底層編輯器引擎）npm 最後一次發版是 2024-11-30（近 1 年 8 個月未發版），單看這個數字容易誤判為停滯套件。但查證 GitHub `slab/quill` repo 發現最後一次程式碼異動是 2025-07-25，且 repo 未封存，代表官方仍持續開發，只是尚未把累積的變更打包發布新版，與 AOS、Flatpickr 那種「GitHub 也一起停滯」的情況不同，建議列為正常維護但留意，而非直接歸類已停滯。另外，Quill 本身授權為 **BSD-3-Clause**，與 Vue Quilly 的 **MIT** 不同，但兩者都是標準寬鬆式開源授權，商業使用無限制，授權層面沒有疑慮，僅供掃描工具比對授權欄位時參考。

### 💡 開源免費替代方案建議（供評估，非現況異動）

以下為「已停滯」與「授權疑慮」共 9 個套件的開源免費替代方案，查證時間 2026-07-31（Isotope 一列另於 2026-08-19 查證），方法同上（`npm registry` + GitHub API）。這裡只列建議，不代表團隊已經決定更換，實際導入前建議先評估既有程式碼的相依範圍與改寫成本。

**先合併再新增**：Magnific Popup、EasyZoom、Vue Easy Lightbox、Fancybox 這四個套件的核心需求（燈箱展示、局部放大）高度重疊，建議先評估合併到團隊已在「正常維護中」清單裡的 GLightbox，減少套件數量；只有 Fancybox 那種進階畫廊手勢功能 GLightbox 未涵蓋時，才需要額外引入 PhotoSwipe。AOS 的捲動動畫需求，也可以直接用團隊已導入的 GSAP 內建 ScrollTrigger 外掛達成，不需要新增依賴。

| 原套件 | 問題 | 建議替代方案 | npm 套件名 | 授權 | 最新版本／npm 發布日 | GitHub 最後更新 | 待處理 issue |
|---|---|---|---|---|---|---|---|
| AOS | 已停滯逾 4 年 | [GSAP ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger/)（團隊已導入 GSAP，為其內建 plugin，無需新增依賴） | 隨 `gsap` | 自訂授權，已確認可商用 | 3.15.0／2026-04-13 | 2026-04-13 | — |
| Magnific Popup | 已停滯逾 2 年 | [GLightbox](https://biati-digital.github.io/glightbox/)（團隊已在「正常維護中」清單） | `glightbox` | MIT | 3.3.1 | 2025-12-02 | — |
| Vue Easy Lightbox | 已停滯 | 同上，改用 [GLightbox](https://biati-digital.github.io/glightbox/) | `glightbox` | MIT | 3.3.1 | 2025-12-02 | — |
| Fancybox | 付費授權，不可用於開源專案 | 優先評估改用 GLightbox；若需要 Fancybox 等級的畫廊與縮放手勢，改用 [PhotoSwipe](https://github.com/dimsemenov/Photoswipe) | `photoswipe` | MIT | 5.4.4／2024-05-24 | 2025-12-04 | 169（星數 2.5 萬，用量大屬業界標準，核心功能已穩定，非棄置） |
| EasyZoom | 已停滯逾 3 年 | [medium-zoom](https://github.com/francoischalifour/medium-zoom) | `medium-zoom` | MIT | 1.1.0／2023-11-16 | 2025-12-20 | 49 |
| V-Calendar／Nuxt V-Calendar | 已停滯近 3 年 | [@vuepic/vue-datepicker](https://github.com/Vuepic/vue-datepicker)（Vue 3 專用，維護活躍） | `@vuepic/vue-datepicker` | MIT | 14.0.0／2026-06-02 | 2026-07-08 | 10 |
| Flatpickr | 已停滯逾 4 年 | [vanilla-calendar-pro](https://github.com/uvarov-frontend/vanilla-calendar-pro) 或 [cally](https://github.com/WickyNilliams/cally)（Web Component，框架無關，符合公司 Nuxt／Vue／CDN 多種引入方式） | `vanilla-calendar-pro` 或 `cally` | MIT | 3.1.0／2026-01-09（vanilla-calendar-pro）、0.9.2／2026-02-05（cally） | 2026-07-01、2026-07-10 | 18、15 |
| Animate.css | GitHub 原始碼授權已改 Hippocratic License 2.1（npm 上目前版本仍為 MIT） | 短期無需更換，鎖定現有 npm 4.1.1（MIT）版本即可；中長期若要徹底避開授權疑慮，可評估改用團隊已導入的 [GSAP](https://gsap.com/) 改寫動畫觸發邏輯 | — | — | — | — | — |
| Isotope | 已停滯逾 8 年，且授權為 GPLv3／付費雙軌制 | [Shuffle.js](https://shuffle.js.org)（官方明講「inspired by Isotope and Packery」，定位即為 Isotope 替代品；無 jQuery 或其他 runtime 相依，內建 TypeScript 型別） | `shufflejs` | MIT | 7.0.0／2026-02-13 | 2026-05-12 | 14（星數 2,371，近期仍有 commit，非棄置） |

另外查證時發現一個常見的 EasyZoom 替代方案 **[drift-zoom](https://github.com/strawdynamics/drift)** 已改名搬到 `strawdynamics/drift`，最後一次 GitHub 更新是 2024-06-28，距今超過 2 年，本身也屬於停滯狀態，因此未列入上表推薦選項。

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
