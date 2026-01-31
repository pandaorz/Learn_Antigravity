# 實戰操作：專案規劃 (Project Planning)

## 情境
你只有一個模糊的想法（例如：「我想做一個 AI 驅動的記帳 App」），但不知道該從何開始，需要一位專案經理 (PM) 幫你梳理需求、規劃流程與預估資源。

---

## Antigravity 做法 (Agentic Workflow)

### 1. 下達指令
在 Chat 面板中，扮演 PM 的角色下達指令：

> "我想開發一個『AI 語音記帳 App』。請幫我規劃專案開發流程。
> 1. 列出核心功能 (MVP)。
> 2. 建議需要的技術堆疊 (Tech Stack)。
> 3. 建立一份詳細的 `task.md` 任務清單，將開發工作拆解為可執行的步驟。"

### 2. Agent 執行過程
1.  **需求分析**：Agent 會列出 App 應該具備的功能，如「語音轉文字」、「分類辨識」、「統計圖表」。
2.  **資源建議**：根據你的需求，建議適合的技術（例如：React Native 用於跨平台、Whisper API 用於語音辨識、Firebase 用於後端）。
3.  **產出文件**：自動在專案根目錄建立 `task.md` 或 `plan.md`。

---

## 結果範例
Agent 自動生成的 `task.md`：

```markdown
# AI 語音記帳 App - 開發計畫

## 階段一：核心基礎 (MVP)
- [ ] **專案初始化**
    - [ ] 使用 Expo 初始化 React Native 專案
    - [ ] 設定 Firebase Auth 與 Firestore
- [ ] **語音功能實作**
    - [ ] 整合手機麥克風權限
    - [ ] 串接 OpenAI Whisper API 進行轉錄
- [ ] **記帳邏輯**
    - [ ] 設計資料庫 Schema (Transaction Model)
    - [ ] 實作 CRUD 介面
```

🟢 **效益**：
- **從 0 到 1**：將抽象的想法具象化為可執行的清單。
- **全觀視野**：在寫下一行程式碼之前，先看清楚全貌，避免走冤枉路。
