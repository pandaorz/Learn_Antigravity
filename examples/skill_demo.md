# 實戰操作：AI Skills (Skills)

## 什麼是 AI Skill？
Skill 就像是給 Agent 的「操作手冊」或「角色設定卡」。它是一份 Markdown 檔案（通常命名為 `SKILL.md`），裡面詳細定義了 Agent 在處理特定任務時應該遵循的**原則**、**模板**與**檢查清單**。

---

## 為何要使用 Skill？
1.  **標準化品質**：確保每次輸出的風格（如變數命名、文件格式）都一致，不受 AI 隨機性影響。
2.  **減少重複指令**：你不需要每次都打一長串 Prompt（例如：「請用繁體中文，語氣要專業...」），因為 Skill 裡都寫好了。
3.  **專家經驗注入**：你可以將團隊中最資深工程師的 Best Practices 寫入 Skill，讓 Agent 變身為該領域的專家。

---

## 如何使用？

### 1. 建立 Skill 檔案
在專案中建立 `skills/technical_writing/SKILL.md`（以技術寫作 Skill 為例）：

```markdown
---
name: Technical Writing Assistant
description: 協助撰寫高品質技術文件的 Skill。
---

# Technical Writing Assistant

## 角色設定
你是一位資深技術作家。語氣專業、清晰、客觀。

## 核心原則
1. **清晰至上**：避免不必要的術語。
2. **範例驅動**：必須提供程式碼範例。

## 常用指令模版
### 撰寫操作教學 (`draft_howto`)
> 請撰寫關於 [任務] 的教學。
> - 前置作業
> - 步驟
> - 驗證
```

### 2. 呼叫 Skill (Invoking Skills)

當你需要撰寫文件時，有兩種方式使用 Skill：

**方式 A：顯式呼叫 (Explicit)**
在 **Chat 面板** 中輸入：
> "@skills/technical_writing 请帮我重写这段 API 说明。"
（註：透過 `@` 符號可以快速引用專案中的檔案或 Skill）

**方式 B：自然語言觸發 (Implicit)**
如果 Skill 已經載入或設定為全域，你只需說：
> "幫我把這段說明寫得更清楚一點，符合我們平時的風格。"
Antigravity 會自動參考 `SKILL.md` 的原則。

---

## 實際效果

**未使用 Skill**：
Agent 可能會寫出：「這個函數是用來登入的，傳入帳號密碼就好。」（太過隨意，缺乏細節）

**使用 Skill 後**：
回應會立刻套用 Skill 定義的格式。你會在 Chat 面板看到如下輸出：

> **`login` 函數使用教學**
>
> 此函數用於驗證使用者身份。
>
> 1.  **前置作業**：確保資料庫連線已建立。
> 2.  **程式碼範例**：
>     ```python
>     login("user", "pass")
>     ```
> 3.  **注意**：請勿明碼傳輸密碼。

🟢 **效益**：透過 Skill，你瞬間擁有了一位熟讀團隊規範的資深助手。

---

## 🛠️ 如何從零開始建立 Skill？ (How to Create Skills)

當你發現自己**反覆輸入相同的指令**，或者**不斷糾正 Agent 的格式錯誤**時，就是建立 Skill 的最佳時機。

### 步驟 1：分析模式 (Analyze Patterns)
回顧你的對話紀錄，找出重複性高的需求。
- *情境*：每次請 Agent 寫 API 文件，都要提醒它「要包含 Request Body 範例」和「使用 Markdown 表格」。
- *規則*：`Request Body` is MUST, `Markdown Table` is MUST.

### 步驟 2：提取規則 (Extract Rules)
將這些規則轉化為 Skill 的 `核心原則` 與 `模板`。

### 步驟 3：撰寫定義檔 (Write Definitions)
不需要從頭手寫，你可以**請 Agent 幫你寫**！

> **Prompt 範例 (Metaprompting)**：
> "我想建立一個名為 `API Documentation Expert` 的 Skill。
> 請幫我撰寫 `SKILL.md` 檔案。
> 規則如下：
> 1. 所有參數都要有型別說明。
> 2. 必須包含 CURL 範例。
> 3. 失敗的回傳範例也要列出。
> 請參考 Antigravity 的 Skill 格式輸出。"

---

## 🔧 輔助工具與資源 (Tools & Resources)

1.  **Metaprompting (用 AI 寫 AI 設定)**
    如上所述，直接用自然語言告訴 Agent 你想要什麼 Skill，讓它幫你產生 YAML Frontmatter 與 Markdown 結構。

2.  **GitHub 資源 (Awesome Prompts)**
    參考開源社群的 Prompt 集合，將其改寫為 Skill。
    - [Awesome ChatGPT Prompts](https://github.com/f/awesome-chatgpt-prompts)
    - [Awesome AI Skills](https://github.com/topics/ai-skills) (虛構範例，請搜尋真實資源)

3.  **團隊共享**
    將 `skills/` 目錄納入 Git 版本控制。當隊友 `git pull` 下來後，他們也能立即使用你精心調校的 Skill。

---

## ⚙️ 設定與操作
- **位置**：通常存放在專案根目錄的 `skills/<skill_name>/SKILL.md`。
- **生效**：
    - **全域生效**：某些設定可讓 Skill 對所有對話生效（視 IDE 實作而定）。
    - **特定呼叫**：如前述，使用 `@` 或是自然語言觸發。
- **測試**：
    建立完 Skill 後，開一個新的 Chat Session，輸入相關指令測試回應。如果不滿意，隨時修改 `SKILL.md`，效果通常是即時更新的。
