# 關於 Learn_Antigravity 專案 (About Learn_Antigravity)

歡迎來到 **Learn_Antigravity**！這不僅是一個學習 Antigravity (Google 的 AI 程式助手) 的專案，更是一個探索 **AI Agentic Workflow (代理人工作流)** 的實驗室。

在這裡，我們不只是寫程式碼，我們在設計「如何讓 AI 幫我們寫程式碼」。

## 1. 學習路徑 (Learning Path)

建議依照以下順序閱讀文件，逐步掌握 Agentic AI 的能力：

### 第一步：觀念建立
-   **[Antigravity 使用指南](Antigravity_Guide.md)**：了解 Agentic AI 的核心概念與三大支柱。
-   **[全域配置與個人化](examples/config_demo.md)**：學會如何設定 `GEMINI.md` 與 `.cursorrules`，讓 Agent 聽懂你的話。

### 第二步：技能與指令
-   **[AI Skills 實戰](examples/skill_demo.md)**：學習如何載入與呼叫「技術寫作」與「筆記」技能。
-   **[Prompt Engineering 指南](examples/prompt_guide.md)**：掌握與 AI 溝通的藝術。

### 第三步：進階應用
-   **[自動化瀏覽器操作](examples/browser_demo.md)**：讓 Agent 幫你上網、測試網頁。
-   **[完整專案演練](examples/full_lifecycle_demo.md)**：從零開始，見證 Agent 如何協助開發一個完整的購物網站後端。

---

## 2. 專案架構 (Project Architecture)

這個專案的結構設計是為了展示 Agent 的不同能力：

-   **`examples/`**：存放各種範例文件與程式碼。
-   **`skills/`**：這是 Agent 的「大腦擴充包」。
    -   `technical_writing/`: 讓 Agent 變成技術寫作專家的設定檔 (Diátaxis 架構)。
    -   `note_taking/`: 讓 Agent 變成筆記高手的設定檔。

---

## 3. 核心技術：AI Skills (技能)

你或許會問：「為什麼我需要 `SKILL.md`？我直接跟 AI 說話不就好了嗎？」

**Skill 就像是員工手冊**。一旦寫好了，Agent 就會自動依照手冊行事，你只需要下達簡單的指令。

本專案已為您準備了兩個強大的 Skill：

#### A. 技術寫作專家 (Technical Writing Expert)
-   **檔案位置**：[skills/technical_writing/SKILL.md](skills/technical_writing/SKILL.md)
-   **用途**：撰寫高品質、結構化的技術文件。
-   **呼叫方式**：`@skills/technical_writing 請幫我寫一份關於 Python async/await 的教學`

#### B. 智慧筆記助理 (Smart Note Taker)
-   **檔案位置**：[skills/note_taking/SKILL.md](skills/note_taking/SKILL.md)
-   **用途**：整理會議記錄、摘要長篇文章。
-   **呼叫方式**：`@skills/note_taking 請幫我總結這段文字`

---

## 4. 為什麼選擇 Markdown？

你會發現這個專案裡充滿了 `.md` 檔案。為什麼不是 Word 或 Google Docs？

1.  **通用性 (Universal)**：Markdown 是純文字，任何編輯器都能開，AI 讀取也最精確。
2.  **版本控制 (Git-friendly)**：我們可以清楚看到每一行文字的變更歷史。
3.  **工程師的共同語言**：在 GitHub 上，Markdown 就是溝通的標準。

---

**開始你的探索吧！** 試著用用看上面的技能，感受一下「有訓練過的 Agent」與「原始 Agent」的差別。
