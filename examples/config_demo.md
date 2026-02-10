# 全域配置與個人化 (Configuration Guide)

Antigravity 允許你透過設定檔來定義 Agent 的行為。你可以「馴服」你的 AI，讓它更符合你的開發習慣、語言偏好或資安要求。

---

## 設定檔階層 (Configuration Hierarchy)

Antigravity 的設定分為兩個層級，**專案級設定會覆蓋 (Override) 全域設定**（如果發生衝突）。

| 層級 | 設定檔位置 | 用途 | 適用範圍 |
| :--- | :--- | :--- | :--- |
| **1. 全域設定 (Global)** | `~/.gemini/GEMINI.md` | 定義通用的「人格」、「原則」與「禁令」。 | **所有的專案** |
| **2. 專案設定 (Project)** | `.cursorrules` (或 `.antigravity/rules`) | 定義該專案特定的技術堆疊、架構規範。 | **僅當前專案** |

---

## 🌎 1. 全域設定：GEMINI.md
這是 Agent 的「大腦」基底。建議將**不隨專案改變的習慣**放在這裡。

### 推薦設定範例
位置：`~/.gemini/GEMINI.md`

```markdown
# Antigravity Global Context

## 1. 語言與溝通 (Language & Communication)
- **Always respond in Traditional Chinese (繁體中文).**
- 使用台灣工程師常用的術語（如：資料庫、演算法、視窗、檔案）。
- 解釋技術概念時，請使用淺顯易懂的比喻。

## 2. 程式碼風格 (Coding Style Principles)
- **Python**: 總是使用 Type Hinting (PEP 484)。
- **Comments**: 註解必須說明「為什麼 (Why)」而非「做什麼 (What)」。
- **Error Handling**: 禁止使用空的 try-except block (pass)。

## 3. 安全限制 (Security Hard Constraints)
- ❌ **絕對禁止**：將 API Key、Password 硬編碼 (Hardcode) 在程式碼中。
- ❌ **絕對禁止**：未經確認直接刪除資料庫 (DROP TABLE)。
```

> **💡 小技巧**：
> 如果你希望 Agent 扮演特定角色（例如：「你是一位嚴格的資深架構師」），也可以寫在這裡。

---

## 📂 2. 專案設定：.cursorrules
這是針對特定專案的「任務簡報」。每個專案的需求不同（有的用 React，有的用 Vue），應在此定義。

### 推薦設定範例
位置：專案根目錄 `/path/to/project/.cursorrules`

```markdown
# Project Rules: E-commerce API

## Tech Stack
- **Framework**: FastAPI (Python 3.10+)
- **Database**: PostgreSQL + SQLModel
- **Package Manager**: Poetry

## 架構規範
- 所有的 API Routers 必須放在 `src/routers/` 目錄下。
- 資料庫操作均需透過 `src/crud/` 中的函式，禁止在 Router 直接寫 SQL。

## 特殊需求
- 本專案使用 **Soft Delete** (軟刪除)，所有 Table 都有 `is_deleted` 欄位。
- 刪除資料時，請將 `is_deleted` 設為 `True`，而非執行 `DELETE` 指令。
```

---

## ✅ 最佳實踐
1.  **由簡入繁**：先把通用的規則（如繁體中文）放進 Global `GEMINI.md`。
2.  **專案特化**：當你發現某個規則只對這個專案有效（如 Soft Delete），請放進 Project `.cursorrules`。
3.  **定期檢視**：如果發現某個 Project Rule 在每個專案都用到，就將它升級為 Global Rule。

---

### 📚 下一步
- 回到 **[LEARN.md](../LEARN.md)** 查看完整學習路徑。
- 閱讀 **[Antigravity 使用指南](../Antigravity_Guide.md)** 了解更多核心概念。
