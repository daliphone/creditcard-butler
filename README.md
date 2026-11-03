# 💳 刷卡回饋管家（極簡專屬版）

專為個人自用打造的**極簡無雜訊信用卡封頂額度控管、記帳與銀行登錄額滿監控工具**。

## ✨ 核心改造特色

1. **極簡現代介面（支援深色 / 淺色模式）**
   - 徹底移除原版的跑馬燈公告、戰績分享圖、推銷連結、安裝氣泡與 Apple 裝置強制跳轉限制。
   - **iOS / Android / Windows / Mac 全平台秒開通用**。
2. **多軌加碼池進度條（一眼看穿還可刷多少）**
   - 無需點進卡片深層選單，首頁直接並列顯示每張卡的各個加碼池：
     - **「還可刷 `$X,XXX`」**（已刷 `$Y` / 封頂 `$Z`）
     - 自動連動爬蟲資料，若官方活動已額滿（如聯邦偶數日、UniOpen icash Pay），進度條直接警示 `⛔ 官方活動已額滿`。
3. **銀行登錄與額滿即時監控**
   - 自動過濾出**「我的持卡活動」**，標示 `🟢 尚有名額` / `🔴 已額滿（含額滿時間）` / `📅 遇假日順延提示`。
   - 內建**「行動支付 / 全聯福利點各銀行剩餘名額」**即時監控面板。
   - 支援在本地打勾記錄「✅ 本月已登錄」，避免漏登或重複搶登。
4. **介面與資料 100% 解耦（零維護成本）**
   - 前端介面獨立於 [`index.html`](file:///C:/Users/serap/.gemini/antigravity/scratch/creditcard-butler/index.html)。
   - 透過 GitHub Actions（[`.github/workflows/sync-upstream-data.yml`](file:///C:/Users/serap/.gemini/antigravity/scratch/creditcard-butler/.github/workflows/sync-upstream-data.yml)）每天定時自動從上游同步最新的 `.json` 資料檔（並具備 JSON 合法性驗證防呆機制），**永遠不會覆蓋您的自訂介面**。

---

## 🚀 如何部署到您自己的 GitHub Pages（僅需 3 分鐘）

1. 在您的 GitHub 建立一個新的公開儲存庫（Repository），例如命名為 `my-creditcard`。
2. 在此目錄初始化 Git 並推送上去（依全域規範逐一指定檔案提交）：
   ```powershell
   cd C:\Users\serap\.gemini\antigravity\scratch\creditcard-butler
   git init
   git branch -M main
   git add index.html manifest.json sw.js README.md .nojekyll icon-192.png card_merchants.json registrations.json registration_status.json promo_status.json weekly_promos.json config.json .github/workflows/sync-upstream-data.yml
   git commit -m "feat: 初始化刷卡回饋管家極簡專屬版與自動同步排程"
   git remote add origin https://github.com/<您的GitHub帳號>/my-creditcard.git
   git push -u origin main
   ```
3. 前往 GitHub 儲存庫的 **Settings → Pages**，在 `Build and deployment` 選擇 `Deploy from a branch`（分支選 `main` / `/ (root)`）並儲存。
4. 前往 **Settings → Actions → General**，確認 `Workflow permissions` 勾選為 **Read and write permissions**，如此每天早、中、晚就會自動同步最新銀行活動與額滿狀態！
