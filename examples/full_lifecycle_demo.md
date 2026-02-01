# 綜合演練：從零打造購物網站後端 (E-commerce API)

## 情境
你正在為一家新創公司開發核心的電商後端系統。這個任務不再是單一功能的實作，而是需要串聯**規劃、架構、開發、資安與文件**的完整 SSDLC 流程。

---

## Agentic Workflow 實戰

### 📅 Phase 1: 專案規劃 (Planning)
與其直接寫 Code，不如先請 Agent 幫你拆解任務。

> **User**: "我們要開發一個購物網站後端 API，使用 Python FastAPI。請幫我列出 MVP (最小可行性產品) 需要的功能模組，並拆解成 User Stories。"

**Agent 產出**:
1.  **使用者模組**: 註冊、登入 (JWT)、個人資料管理。
2.  **商品模組**: 商品列表、搜尋、新增商品 (管理員)。
3.  **訂單模組**: 購物車、建立訂單、訂單狀態更新。

### 🏗️ Phase 2: 架構設計 (Architecture)
在寫第一行程式碼前，先定義資料結構。

> **User**: "基於上述需求，請幫我設計資料庫 Schema (使用 SQLModel)。請包含 User, Product, Order 資料表，並說明它們之間的關聯。"

**Agent 產出**:
- 生成 Mermaid ER Diagram。
- 定義 Pydantic/SQLModel models 程式碼草稿。

### 💻 Phase 3: 分階段實作 (Iterative Development)

**最佳實踐**：不要試圖一句話生成整個專案。請「分模組」進行。

#### 💡 為什麼要分模組？ (Why & How)
-   **降低錯誤率 (Error Isolation)**：
    -   ❌ **One-Shot**: "幫我寫一個電商網站" -> AI 生成了 50 個檔案，發生錯誤時你很難找出是 Database 連線錯了，還是 Router 定義錯了。
    -   ✅ **Iterative**: "先寫 User Model 和 Database 連線" -> 確認連線成功 -> "再寫 User Router" -> 確認 API 能用。每一次只專注解決一個問題。
-   **上下文管理 (Context Management)**：
    -   AI 的記憶體（Context Window）有限。如果一次塞入太多需求，它容易「忘記」前面的細節（例如忘記加密密碼）。
    -   透過分階段，每次對話只聚焦在當前模組，AI 能給出更精確的程式碼。

#### 實戰範例：
1.  **第一步 (Core)**：先建立 `models/user.py` 與 `db.py`。確保資料庫能連線，Table 能建立。
2.  **第二步 (Auth)**：基於 User Model，實作 `auth.py` (登入功能)。這是許多功能的前提。
3.  **第三步 (Features)**：基於 Auth，實作 `models/product.py`。因為只有管理員能新增商品，所以必須先完成 Auth。

---

#### Step 3.1: 建立基礎專案結構
> **User**: "請建立 FastAPI 專案結構，包含 `src/main.py`, `src/models`, `src/routers`。先實作一個 Health Check API 確保環境正常。"

#### Step 3.2: 實作使用者模組
> **User**: "實作 `src/routers/users.py`。包含註冊與登入 API。密碼必須使用 argon2 hash。"

#### Step 3.3: 實作商品與訂單
> **User**: "接續實作 Product CRUD。請確保只有管理員權限可以新增商品。"

### 🔒 Phase 4: 資安檢測 (Security Testing)
在提交程式碼前，讓 Agent 擔任資安稽核員。

> **User**: "請審查 `src/routers/auth.py`。
> 1. 檢查 JWT token 是否有設定過期時間？
> 2. 檢查 Secret Key 是否被寫死在程式碼中？"

**Agent 回饋**:
> ⚠️ **警告**: 發現 `SECRET_KEY = "mysecret"` 在程式碼中。
> ✅ **修正**: 已將其移至 `.env` 檔案，並透過 `os.getenv` 讀取。

### 📄 Phase 5: 文件與部署 (Documentation)
最後，讓 Agent 把文件補齊。

> **User**: "請基於目前的程式碼，生成一份 `README.md`。包含：
> 1. 專案安裝步驟 (使用 poetry)。
> 2. API 文件連結 (Swagger UI)。
> 3. 環境變數設定說明。"

---

## ✅ 總結：為什麼這樣做更快？
1.  **架構清晰**：先規劃再動手，避免寫到一半發現架構不合而重構。
2.  **品質保證**：分階段實作搭配資安檢查，確保每個模組都是穩固的 (Solid)。
3.  **文件同步**：程式碼寫完，文件也同步完成，不再有技術債。
