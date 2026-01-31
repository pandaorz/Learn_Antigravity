# 實戰操作：協助工作 (Work Assistance)

## 情境
除了寫 Code，工程師的日常還包含了大量的「雜事」：
1.  **創意發想**：專案需要一個響亮的名字，或是一句吸引人的 Slogan。
2.  **環境除錯**：新買的電腦跑不動舊專案，Python 版本衝突，Global 套件一團亂。

---

## Antigravity 做法 (Agentic Workflow)

### 案例 1：腦力激盪 (Brainstorming)

你不需要自己盯著天花板發呆，讓 Agent 陪你 Brainstorming。

#### 指令
> "我們正在開發一個『專為全職媽媽設計的時間管理 App』。
> 請幫我想 10 個英文專案名稱 (Project Name) 與對應的 Slogan。
> 風格要求：溫馨、強大、易記。
> 請用表格呈現，並附上每個名稱的命名理念。"

#### 結果
Agent 會生成如下的創意清單：

| 名稱 | Slogan | 命名理念 |
| :--- | :--- | :--- |
| **Moments** | Capture the chaos, cherish the calm. | 結合 Mom 與 Moment，強調把握當下。 |
| **SuperNest** | Running the home like a HQ. | 將家庭比喻為巢穴 (Nest)，媽媽是超人 (Super)。 |
| **FlowMama** | Find your rhythm. | 強調像水一樣的適應力 (Flow)。 |

---

### 案例 2：環境設定 (Environment Setup)

這是每位開發者最頭痛的噩夢：接手別人的專案，結果 `pip install` 失敗。

#### 指令
> "我試圖執行這個專案，但出現了 `ModuleNotFoundError: No module named 'tensorflow'` 錯誤。
> 我目前的 Python 版本是 3.11。請幫我檢查 `requirements.txt`，並修復環境問題。
> 如果需要建立虛擬環境，請直接執行相關指令。"

#### Agent 執行過程
1.  **診斷**：Agent 檢查 `requirements.txt`，發現指定了 TensorFlow 2.10，該版本可能不支援 Python 3.11。
2.  **規劃**：建議降級 Python 或升級套件。
3.  **執行**：
    - 建立虛擬環境：`python3 -m venv .venv`
    - 嘗試安裝相容版本：`pip install tensorflow-macos` (如果是 Mac)
    - 更新文件：修改 `requirements.txt` 鎖定正確版本。
4.  **驗證**：試跑 `main.py` 確認錯誤消失。

🟢 **效益**：
- **節省心神**：不用再去 Stack Overflow 翻找五年前的解答。
- **創意加值**：AI 往往能提出你沒想過的切入點。
