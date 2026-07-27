# 第三方套件總覽

本文件用於追蹤團隊專案中實際使用的第三方套件，包含目前版本、最新版本、官方維護狀態與授權條款，作為原碼掃描與授權合規檢查的依據。

- **最後查詢時間**：2026-07-27
- **資料來源**：npm registry（`npm view`）、GitHub 官方 API、各套件官方授權頁面
- **「目前用版本」欄位**：需要團隊成員依實際專案回填，本文件建立時尚未取得，先標記為「待補」

## 套件清單

| 套件（官網） | npm 套件名 | 目前用版本 | 最新版本 | npm 最後發布 | GitHub 最後更新 | 授權 | 狀態 |
|---|---|---|---|---|---|---|---|
| [SweetAlert2](https://sweetalert2.github.io/) | `sweetalert2` | 待補 | 11.26.25 | 2026-05-23 | 2026-07-20 | MIT | ✅ 正常，活躍維護 |
| [Bootstrap](https://getbootstrap.com/) | `bootstrap` | 待補 | 5.3.8 | 2026-06-05 | 2026-07-26 | MIT | ✅ 正常，活躍維護 |
| [Vue Quilly](https://vue-quilly.vercel.app/) | `vue-quilly` | 待補 | 1.1.6 | 2025-12-07 | 2026-03-23 | MIT | ✅ 正常，但專案規模小、更新頻率較低，建議留意 |
| [Fancybox](https://fancyapps.com/fancybox/) | `@fancyapps/ui` | 待補 | 6.1.14 | 2026-04-29 | 2026-04-29 | **非開源／需付費授權** | ⚠️ 高風險，見下方說明 |
| [AOS](https://michalsnik.github.io/aos/) | `aos` | 待補 | 2.3.4 | 2022-06-13（超過 4 年未發版） | 2024-03-26 | MIT | ⚠️ 已停滯，373 個未解決 issue |
| [Swiper](https://swiperjs.com/) | `swiper` | 待補 | 14.0.6 | 2026-07-22 | 2026-07-24 | MIT | ✅ 正常，非常活躍 |
| [V-Calendar](https://vcalendar.io/) | `v-calendar` | 待補 | 2.4.2 | 2023-10-13（近 3 年未發版） | 2024-08-07 | MIT | ⚠️ 已停滯，786 個未解決 issue |
| [GSAP](https://gsap.com/) | `gsap` | 待補 | 3.15.0 | 2026-04-13 | 2026-04-13 | 自訂「Standard No Charge License」 | ✅ 授權特殊但確認可商用，見下方說明 |
| [Apache ECharts](https://echarts.apache.org/) | `echarts` | 待補 | 6.1.0 | 2026-05-19 | 2026-07-26 | Apache-2.0 | ✅ 正常，Apache 基金會專案，非常活躍 |
| [Magnific Popup](https://dimsemenov.com/plugins/magnific-popup/) | `magnific-popup` | 待補 | 1.2.0 | 2024-06-08（超過 2 年未發版） | 2024-06-08 | MIT | ⚠️ 已停滯，678 個未解決 issue |
| [EasyZoom](https://i-like-robots.github.io/EasyZoom/) | `easyzoom` | 待補 | 2.6.0 | 2022-12-30（超過 3 年未發版） | 2024-06-19 | MIT | ⚠️ 已停滯，超過 3 年未發版 |
| [Animate.css](https://animate.style/) | `animate.css` | 待補 | 4.1.1 | 2022-11-18（超過 3 年未發版） | 2024-07-29 | ⚠️ 見下方說明 | ⚠️ 已停滯 + 授權疑慮，見下方說明 |

## 風險與注意事項

### ⚠️ Fancybox（`@fancyapps/ui`）—— 授權風險，需優先確認

官方 [授權頁面](https://fancyapps.com/license/) 明確寫明：

- 每個專案無論類型、位置或法律形式，都需要**有效的付費授權**
- **不可在開源專案中使用**
- 商業用途、公司內網、SaaS 產品皆需購買「商業授權」或「商業擴展授權」

若團隊目前是直接引用但尚未購買授權，屬於實際法遵風險，建議優先跟法務／PM 確認授權狀態。如需替換，MIT 授權的同類型 lightbox 套件（例如 GLightbox、PhotoSwipe）可列入評估。

### ⚠️ AOS、V-Calendar、Magnific Popup、EasyZoom、Animate.css —— 維護停滯風險

這五個套件最後一次 npm 發版都超過一年（AOS 已逾 4 年、V-Calendar 近 3 年、Magnific Popup 超過 2 年、EasyZoom 與 Animate.css 皆超過 3 年），代表官方維護能量可能不足，長期使用有安全性更新跟不上的風險。其中 AOS、V-Calendar、Magnific Popup 三者 GitHub 上待處理 issue 數量偏高（分別為 373、786、678 個）；EasyZoom 待處理 issue 僅 8 個，數量不高，但也已超過 3 年沒有新版發布，同樣建議列入觀察。建議團隊評估是否需要尋找替代方案（例如 Magnific Popup、EasyZoom 可考慮 PhotoSwipe 等仍活躍的同類套件），或接受此風險並列管觀察。

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
