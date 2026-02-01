# 實戰操作：資安檢測 (Security Testing)

## 情境
在 SSDLC (Secure Software Development Life Cycle) 中，安全性不能等到上線前才檢查，而應該「左移 (Shift Left)」至開發階段。你需要 Agent 協助進行早期的弱點掃描與依賴檢查。

---

## Antigravity 做法 (Agentic Workflow)

### 1. 靜態應用程式安全測試 (SAST)
在寫完程式碼後，立即請 Agent 進行安全審查：

> "請審查 `src/auth.py` 的程式碼安全性。
> 特別注意：
> 1. 是否有 SQL Injection 風險？
> 2. 密碼是否經過正確雜湊 (Hashing)？
> 3. 是否有寫死的 API Key？"

**Agent 回饋範例**：
> ⚠️ **發現高風險項目**：
> 在第 45 行發現直接字串串接 SQL 指令：
> `query = f"SELECT * FROM users WHERE name = '{username}'"`
>
> ✅ **修正建議**：
> 請改用參數化查詢 (Parameterized Query)：
> `cursor.execute("SELECT * FROM users WHERE name = ?", (username,))`

### 2. 軟體組成分析 (SCA)
檢查第三方套件是否有已知漏洞：

> "請掃描 `requirements.txt` 中的依賴套件，並比對已知漏洞資料庫 (如 OSV 或 PyPI Advisory)。如果有高風險漏洞，請建議升級版本。"

**Agent 回饋範例**：
> ⚠️ **發現漏洞**：
> `requests==2.10.0` 含有 CVE-2023-xxxx 漏洞。
>
> ✅ **行動**：
> 已自動將 `requirements.txt` 中的版本更新為 `2.31.0`，並執行測試確保相容性。

### 3. 機敏資料防護 (Secret Management)
在 commit 之前，確保沒有將私鑰上傳：

> "檢查專案中所有檔案，確認是否有類似 AWS Key、Private Key 或 Database Password 的字串被硬編碼 (Hardcoded)。如果發現，請將其移至 `.env` 檔案並更新程式碼。"

---

## 🟢 效益
- **早期發現**：修復漏洞的成本最低。
- **自動化合規**：確保每次提交都符合基本的資安規範。
- **教育訓練**：Agent 在修正漏洞時，也會解釋原因，提升開發者的資安意識。
