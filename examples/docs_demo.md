# 實戰操作：撰寫文件 (Writing Documentation)

## 情境
專案已經開發了一段時間，新增了許多 API，但 `README.md` 和 API 文件已經過期很久了。

---

## 傳統做法 (Traditional Workflow)
1.  **逐一開啟檔案**：打開 `src/` 下的所有檔案，閱讀程式碼以了解參數變更。
2.  **手動撰寫**：在 `README.md` 中一行一行打字，描述每個函數的功能。
3.  **複製範例**：手動複製程式碼片段作為範例，容易複製錯行或漏掉 import。
4.  **維護困難**：下次更新程式碼時，又忘記更新文件。

---

## Antigravity 做法 (Agentic Workflow)

### 1. 啟動對話 (Start Chat)
在 **Chat 面板** 中輸入指令。因為 Antigravity 具備 **全域感知 (Context Awareness)**，它能「看見」整個專案，所以你不需要貼上任何程式碼。

> "閱讀 `src/` 目錄下的所有 Python 檔案，根據最新的程式碼邏輯，更新 `README.md` 中的 'API Reference' 章節。請為每個函數生成清晰的參數說明與使用範例。"

### 2. 審閱與執行
1.  Agent 會列出它將讀取的檔案清單。
2.  確認無誤後，按下 **Enter** 或 **Run**。

### 3. Agent 執行過程
1.  **掃描程式碼**：Agent 讀取 `src/auth.py`, `src/database.py` 等檔案，解析函數簽章 (Function Signatures) 與 Docstrings。
2.  **生成內容**：
    - 它發現 `login` 函數新增了一個 `timeout` 參數。
    - 它發現 `connect_db` 函數的回傳值變了。
3.  **更新文件**：直接編輯 `README.md`，插入準確的 Markdown 表格與程式碼區塊。

### 4. 結果範例與確認
Agent 完成後，會顯示修改後的 `README.md` 預覽。你可以直接在預覽視窗中檢查格式是否跑掉。

```markdown
### `login(username, password, timeout=30)`

使用者登入函數。

- **參數**:
    - `username` (str): 使用者名稱。
    - `password` (str): 密碼。
    - `timeout` (int, optional): 連線逾時秒數，預設為 30。

- **範例**:
    ```python
    from src.auth import login
    user = login("admin", "secret", timeout=60)
    ```
```

🟢 **優點**：
- **即時同步**：確保文件永遠反映最新的程式碼狀態。
- **減少人為疏失**：參數型別、預設值絕不出錯。
- **節省時間**：文件撰寫通常是工程師最不愛做的事，現在可以完全交給 AI。
