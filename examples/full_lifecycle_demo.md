# 綜合演練：從零打造購物網站後端 (E-commerce API)

這份文件將展示如何運用 Antigravity Agent，從無到有打造一個完整的電商後端系統。我們將遵循 SSDLC (Secure SDLC) 流程，並採用 **分階段 (Iterative)** 的開發策略。

## 情境目標
- **專案類型**: 購物網站後端 API
- **技術堆疊**: Python (FastAPI), SQLModel, PostgreSQL
- **核心功能**: 使用者管理 (Auth), 商品管理 (Product), 訂單處理 (Order)

---

## 策略核心：為什麼要分模組？ (Why & How)

在進入實作前，建立正確的心態至關重要。許多人使用 Agent 失敗，是因為試圖「一句話生成整個專案」。

### ❌ 錯誤做法：One-Shot Generation
> "幫我寫一個電商網站，要有會員、商品、購物車功能，用 FastAPI 寫。"

**後果**：
- Agent 生成了 50 個檔案，程式碼長度超過 Context Window 上限。
- 發生 Bug 時，你不知道是資料庫連線錯了，還是邏輯錯了（Error Isolation 困難）。
- 需求細節（如密碼加密方式）容易被忽略。

### ✅ 正確做法：Iterative Development (分階段協作)
> "我們先建立 User Model 和資料庫連線。" -> (確認成功) -> "接著實作註冊 API。"

**優勢**：
- **精確控制**：每次對話只聚焦一個主題，AI 準確度極高。
- **穩固基礎**：確保基礎建設 (Core) 沒問題後，再蓋上層建築 (Features)。

---

## Agentic Workflow 實戰流程

### 📅 Phase 1: 專案規劃 (Planning)
**目標**：明確定義 MVP (最小可行性產品) 範圍。

> **User**: "我們要開發一個購物網站後端 API。請幫我拆解 User Stories，並列出 MVP 必須包含的功能模組。"

**Agent 產出**:
1.  **使用者模組**: 註冊、登入 (JWT)、個人資料管理。
2.  **商品模組**: 商品列表、搜尋、新增商品 (管理員)。
3.  **訂單模組**: 購物車、建立訂單 (交易一致性)。

### 🏗️ Phase 2: 架構設計 (Architecture)
**目標**：定義資料結構與關聯。

> **User**: "請設計資料庫 Schema (使用 SQLModel)。包含 User, Product, Order，並說明它們之間的關聯 (1-to-many, many-to-many)。"

**Agent 產出**:
- 生成 Mermaid ER Diagram。
- 定義 Python Models 草稿 (確保關聯欄位正確)。

### 💻 Phase 3: 分階段開發 (Iterative Implementation)
**目標**：逐步實作程式碼。

#### Step 3.1: 核心基礎 (Core Infrastructure)
> **User**: "請建立 FastAPI 專案結構，包含 `src/main.py`, `src/database.py`。實作一個 Health Check API，並確保能連線到 PostgreSQL。"

#### Step 3.2: 身份驗證模組 (Auth Module)
> **User**: "實作 User CRUD 與 `auth.py`。
> 1. 密碼需使用 Argon2 hash。
> 2. 登入回傳 JWT Token。
> 3. 實作 `get_current_user` dependency。"

#### Step 3.3: 業務邏輯模組 (Business Logic)
> **User**: "接著實作 Product CRUD。請加入權限控制：只有 `is_admin=True` 的使用者可以新增/修改商品，一般使用者只能查詢。"

### 🔒 Phase 4: 資安檢測 (Security Testing)
**目標**：在部署前找出漏洞。

> **User**: "請仔細審查 `src/routers/auth.py` 與 `src/config.py`。
> 1. 檢查 JWT Secret Key 是否寫死在程式碼中？(應讀取環境變數)
> 2. 檢查是否有 SQL Injection 風險？"

**Agent 回饋**:
> ⚠️ **發現風險**: `ALGORITHM = "HS256"` 被寫死。
> ✅ **修正建議**: 建議也將演算法配置移至 `.env` 檔。

### 📄 Phase 5: 文件與部署 (Documentation)
**目標**：留下好維護的資產。

> **User**: "請基於目前的程式碼庫：
> 1. 生成 `README.md`，說明如何使用 Poetry 安裝與啟動。
> 2. 生成 `API.md`，列出所有 Endpoints 與參數範例。"

---

## ✅ 總結
透過這個案例，我們展示了 Antigravity 不是一個「取代者」，而是一個強大的「倍增器」。你不需要親自寫每一行 boilerplate code，但你必須是那個**懂得拆解任務、並審核結果的架構師**。
