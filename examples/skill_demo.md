# 實戰操作：AI Skills (技能)

## 1. 什麼是 AI Skill？
Skill 就像是給 Agent 的「員工手冊」或「SOP」。它是一份 Markdown 檔案（通常命名為 `SKILL.md`），裡面詳細定義了 Agent 在處理特定任務時應該遵循的**原則**、**模板**與**檢查清單**。

---

## 2. 為什麼需要 Skill？
1.  **標準化品質**：確保每次輸出的風格（如變數命名、文件格式）一致。
2.  **減少重複指令**：不需要每次都打一長串 Prompt。
3.  **注入專家經驗**：將資深工程師的 Best Practices 寫入 Skill，讓 Agent 變身為該領域的專家。

---

## 3. 專案中的 Skills
本專案已經為您準備了兩個強大的 Skill：

### A. 技術寫作專家 (Technical Writing Expert)
-   **檔案位置**：`skills/technical_writing/SKILL.md`
-   **用途**：撰寫高品質、結構化的技術文件。
-   **核心架構**：採用 **Diátaxis** 原則（教學、指南、參考、解釋）。
-   **使用範例**：
    > "@skills/technical_writing 請幫我寫一份關於 Python async/await 的教學 (Tutorial)。"

### B. 智慧筆記助理 (Smart Note Taker)
-   **檔案位置**：`skills/note_taking/SKILL.md`
-   **用途**：整理會議記錄、摘要長篇文章。
-   **核心功能**：提取 TL;DR、關鍵決策與待辦事項。
-   **使用範例**：
    > "@skills/note_taking 請幫我總結這段會議記錄，並列出 Action Items。"

---

## 4. 如何建立自己的 Skill？

### 步驟 1：建立目錄與檔案
在專案根目錄建立 `skills/<你的技能名稱>/SKILL.md`。
例如：`skills/code_reviewer/SKILL.md`

### 步驟 2：撰寫定義檔
參考以下模板：

```markdown
---
name: Code Reviewer
description: 協助進行程式碼審查的專家。
---

# Code Reviewer

## 角色設定
你是一位嚴格但公正的資深工程師。

## 檢查清單
- [ ] 是否有潛在的安全性漏洞？
- [ ] 變數命名是否清晰？
- [ ] 是否有過度設計 (Over-engineering)？

## 常用指令
### 審查 (`review`)
> 請審查這段程式碼。
```

### 步驟 3：開始使用
回到對話視窗，輸入 `@skills/code_reviewer` 即可呼叫。

---

## 5. 進階技巧：Metaprompting

懶得自己寫 `SKILL.md`？**叫 Agent 幫你寫！**

> **Prompt 範例**：
> "我想建立一個名為 `Python Optimization Expert` 的 Skill。
> 請幫我撰寫 `SKILL.md` 檔案。
> 規則如下：
> 1. 專注於效能優化。
> 2. 提供 `profile` 指令來分析程式碼。
> 3. 必須提供 Before/After 的比較數據。"
