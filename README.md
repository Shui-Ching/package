# 第三方套件總覽

追蹤團隊專案中實際使用的第三方套件，包含版本、官方維護狀態與授權條款，作為原碼掃描與授權合規檢查的依據。

## 查看套件清單

完整、可搜尋篩選的套件清單請看發布出去的儀表板頁面：

**https://claude.ai/code/artifact/a54ef023-0cc1-47c1-b32a-d5dd7015d146**

## 資料如何維護

這份專案的套件資料**只維護在 [`.claude/skills/package-dashboard/output/dashboard.html`](.claude/skills/package-dashboard/output/dashboard.html) 一份**，不再另外寫在這份 README 裡（避免兩邊分岔、沒人知道哪份才是對的）。

要新增、更新、移除套件，或重新查核維護狀態，跟 Claude Code 說套件名稱即可（例如「加入 xxx 套件」「xxx 更新一下版本」），會自動查證 npm／GitHub 資料、寫入頁面、發布到上面同一個連結、並 commit 到這個 repo。詳細流程與查證方法見 [`.claude/skills/package-dashboard/SKILL.md`](.claude/skills/package-dashboard/SKILL.md)。
