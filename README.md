# 🚀 Claude Code & MCP 麻瓜專用一鍵起飛包（連阿嬤都能裝！）

這份指南專為「完全不懂寫程式」的新手設計。

不需要懂任何專業術語，你只要會**「按滑鼠右鍵、複製、貼上」**，就能把你的 VS Code 變成地表最強的 AI 開發神器！讓 Claude 自動幫你裝好所有進階工具。

---

## 🎯 這包是寫給誰的？

如果你是以下三種人，這份指南就是為你量身打造的：

1. 😩 **已經入坑，但被親朋好友問到快發瘋的人**
   * **症狀**：已經在享受 Claude Code 的強大，但身邊朋友一直吵著要你教，每個人都問一樣的問題：「要裝什麼？」「那個怎麼設定？」「為什麼我的不能用？」
   * **解方**：直接把這個 Repo 的連結丟給他，說：「照著做，不會的問 Claude。」從此解放你的私人時間。

2. 👀 **看社群上大家狂發文，覺得很神想試試看的人**
   * **症狀**：看 Threads 或臉書上大家都在秀用 AI 寫程式、做網站，心癢癢但不知道從何開始。
   * **解方**：這包幫你跳過所有工程師的繁文縟節，直接把環境一次架好。你只要負責「有想法」就好，剩下的交給 Claude。

3. 🐣 **完全不懂程式，但腦袋裡有很多點子的純麻瓜**
   * **症狀**：想做網站、想寫工具，但沒有技術背景。看到「終端機」「npm」就頭痛。
   * **解方**：只要你會用滑鼠和鍵盤，這份指南就能帶你走完全程。所有專業術語都有白話翻譯，所有步驟都有圖文說明。

---

## 🧱 第零關：準備你的「神級編輯器」

在開始魔法之前，你的電腦只需要一個基礎軟體（這輩子只要做一次）：

1. **下載 VS Code（寫程式用的軟體）**
   * 請去官網：[Visual Studio Code](https://code.visualstudio.com/)
   * 點擊畫面上大大的 `Download` 按鈕。
   * 下載後打開它，**一路無腦按「Next / 下一步」到底**直到安裝完成。

---

## 🔌 第一關：安裝 Claude 插件與登入授權

現在你已經有了 VS Code，我們要幫它裝上 Claude 的大腦：

### 1. 安裝 Claude 插件

1. 打開 VS Code，看螢幕**最左邊**那一排圖示，點擊由四個小方塊組成的圖示（這叫「延伸模組 / Extensions」）。
2. 在左上方的搜尋框輸入 `Claude Code`。
3. 找到官方出的 Claude Code（認明 Anthropic 官方的橘底白色放射圖示），大力點下 **Install（安裝）**。

### 2. 登入授權

1. 安裝好之後，你螢幕**上方**就會多出一個 Claude 的**橘底白色放射狀圖案**，點擊它！
2. 畫面會提示你需要登入。點擊登入按鈕後，**瀏覽器會自動彈出一個 Anthropic 的登入網頁！**
   * 👉 **你的動作**：在網頁上登入你的帳號（用 Google 登入最快）。
   * 登入後，畫面會出現一個綠色的 **「Approve（同意）」** 按鈕，大力點下去！
   * 當網頁顯示「Success」時，就可以把網頁關掉，回到 VS Code 了。

恭喜！你的 Claude 已經正式進駐你的電腦，準備好為你工作了！

---

## 🏰 第二關：辦好你的通行證

等等安裝過程中，Claude 會需要幫你登入一些服務。好消息是，**你只要有 Google 帳號，幾乎全部都可以用「使用 Google 登入」一鍵搞定**。

請先去以下網站，點「使用 Google 登入」完成註冊（每個大概 30 秒）：

| 去這裡辦 | 一定要？ | 用 Google 帳號就能辦？ |
|---------|:-------:|:-------------------:|
| [GitHub](https://github.com/signup)（你的程式碼會放在這裡） | ✅ 要 | ✅ 可以 |
| [Supabase](https://supabase.com/dashboard)（幫你管資料的倉庫） | ✅ 要 | ✅ 可以 |
| [Google Cloud](https://console.cloud.google.com)（Google 的雲端服務） | ✅ 要 | 你有 Google 帳號就已經有了 |
| [Cloudflare](https://dash.cloudflare.com/sign-up)（幫你管網站的地方） | ✅ 要 | ✅ 可以 |
| [Docker Desktop](https://docker.com/get-started)（一種程式的打包工具） | 之後再說 | — |
| [Pencil](https://pencil.dev)（畫設計稿用的） | 之後再說 | — |

每個網站第一次登入時，會跳出一個「是否同意授權」的頁面，按同意就好，之後就不會再問了。

---

## 🗂️ 第三關：建立你的第一個「工作資料夾」

> ⚠️ **這是最多新手踩到的坑！** 很多人打開 VS Code 就開始跟 Claude 亂聊，結果它幫你生出來的檔案散落在電腦各處，找都找不到。

**所以請先做這兩步：**

### 第一步：在桌面建一個新資料夾

在桌面空白處按「右鍵」→「新增資料夾」→ 取個**英文名字**，例如 `my-first-app`

### 第二步：把資料夾拖進 VS Code

直接用滑鼠把剛才建的資料夾**拖進 VS Code 視窗**裡面，它就會自動打開了。

> 💡 以後每次要做新的東西，都先建資料夾 → 拖進 VS Code → 再開始跟 Claude 聊。養成這個習慣，你的檔案就永遠不會亂飛！

---

## 🪄 第四關：施放一鍵安裝魔法

在 VS Code 畫面上方，找到一個**橘底白色放射狀的圖案**，點一下打開它。

點下去之後會出現一個對話框（就像聊天視窗一樣）。把下面這整段話**複製起來**，貼進去，按 Enter：

```
這是一個新專案，請先幫我在現在的資料夾建立一個 CLAUDE.md 檔案，這是我們未來的專案大腦。接著，請幫我讀取這個連結：https://raw.githubusercontent.com/lgscvb/claude-code-quickstart/main/setup.md ，並按照裡面的步驟，全自動幫我裝好所有工具！
```

接下來，**放開你的雙手**，看著 Claude 自動幫你裝好一切！

**你只需要做兩件事**：

1. 每次看到 Claude 問你「可以嗎？」→ 按 **Allow**（允許）
2. 瀏覽器跳出登入頁面時 → 輸入你的**帳號密碼**，然後按**同意**

就這樣。泡杯咖啡等它跑完 ☕

---

## 🎁 第五關：它剛剛幫你裝了什麼神兵利器？

安裝完成後，你的 Claude 已經進化成完全體，擁有了以下超能力：

| 超能力 | 白話說明 |
|--------|---------|
| 🌐 **網頁幫手** | 遇到需要登入的網頁（例如 Google 授權），它會自己打開瀏覽器。你只要負責打帳號密碼並按「同意」，剩下的它搞定。 |
| ⚡ **電腦總管** | 它可以幫你新增、修改、刪除任何檔案，你只要出一張嘴。 |
| 📚 **知識百科** | 你問它程式怎麼寫，它會去網路上撈最新的官方文件來回答你，不會給你過時的答案。 |
| 🎨 **設計大師** | 幫你把網頁畫面排得漂漂亮亮，擁有頂級的設計美感。 |
| ☁️ **雲端管家** | 直接在對話裡幫你管理 Cloudflare 或是 Google Cloud 的伺服器，不用再傻傻登入網頁後台找設定。 |
| 🗄️ **資料庫管家** | 直接跟 Claude 說「幫我看一下資料庫裡有哪些使用者」，不用自己開後台操作。 |
| 🐙 **程式碼管家** | 幫你把程式碼存到 GitHub、處理問題回報，不用一直切網頁。 |
| 📝 **從錯誤中學習** | 每次遇到問題，Claude 修完後會自動把「踩過的坑」記錄下來。下次不會再犯同樣的錯，越用越聰明。 |
| 🎓 **邊做邊學** | Claude 每次寫程式碼都會用小學生聽得懂的白話文解釋：這段在做什麼、為什麼要這樣寫。讓你不知不覺就學會。 |
| 🔧 **全方位強化** | 自動幫你檢查程式碼品質、安全漏洞、寫測試，支援多種程式語言。像請了一整個工程團隊。 |

### 工具來源清單（全部都是官方的）

**MCP 伺服器（讓 Claude 擁有超能力的外掛）：**

| 工具 | 官方來源 | 說明 |
|------|---------|------|
| Chrome DevTools | [ChromeDevTools/chrome-devtools-mcp](https://github.com/nicholascpark/chrome-devtools-mcp) | 操控瀏覽器 |
| Supabase | [supabase/supabase](https://github.com/supabase/supabase) | 資料庫管理 |
| Google Cloud | [google-cloud/gcloud-mcp](https://github.com/nichochar/gcloud-mcp) | 雲端管理 |
| Cloudflare | [cloudflare/mcp-server-cloudflare](https://github.com/cloudflare/mcp-server-cloudflare) | 網站管理 |
| GitHub | [github/github-mcp-server](https://github.com/github/github-mcp-server) | 程式碼管理 |
| Pencil | [pencil.dev](https://pencil.dev) | 設計工具（開 App 自動連接） |

**Skills 技能包：**

| 技能包 | 官方來源 | 說明 |
|-------|---------|------|
| Superpowers | [obra/superpowers](https://github.com/obra/superpowers) | 核心開發技能 |
| UI/UX Pro Max | [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | 頂級設計技能 |
| Everything Claude Code | [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code) | 全方位強化包（13 助手 + 56 技能） |
| 新手大補帖 | [lgscvb/claude-code-quickstart](https://github.com/lgscvb/claude-code-quickstart) | 速查手冊 + 學習系統 |

---

## 🕹️ 新手必學：工作模式與解開限制

### 1. 兩種基本工作模式（快捷鍵 `Shift + TAB`）

在對話框裡，按下鍵盤的 `Shift + TAB` 鍵可以切換：

| 模式 | 白話說明 |
|------|---------|
| 🤖 **自動接受模式** | Claude 改檔案時「不用再問你」，直接幫你存檔。適合你完全信任它的時候。 |
| 📋 **規劃模式** | Claude **不會幫你改任何檔案**。它會單純跟你「討論想法、規劃怎麼做」。腦袋很亂的時候切到這個模式聊聊就對了！ |

> 💡 **建議流程**：先切到「規劃模式」跟 Claude 討論你想做什麼 → 討論完覺得 OK → 切回普通模式讓 Claude 開始動手做。

### 2. ⚠️ 隱藏秘技：啟用 Bypass Permission 模式（完全自動駕駛）

如果你覺得每次 Claude 執行指令都要點「Allow」很煩，你可以透過以下設定解開它的所有封印。

> **注意**：請確保你信任正在執行的專案，並已做好檔案備份！

**方法：通過 VS Code 設置啟用（最簡單直觀）**

1. 打開 VS Code 設置（快捷鍵：`Ctrl + ,` 或 Mac 的 `Cmd + ,`）
2. 在上方搜索框輸入 `Claude Code`
3. 找到 **"Allow Dangerously Skip Permissions"** 選項
4. 勾選啟用 ✅

勾選後，Claude 就會像脫韁的野馬一樣，自動幫你把所有事情幹完，不再中斷徵求你的同意！

---

## 📜 什麼是 CLAUDE.md？為什麼它超重要？

`CLAUDE.md` 就是一份「Claude 的大腦守則」。你可以把它當作 Claude 的記憶體，因為它每次開新對話都會失憶，但只要資料夾裡有這份文件，它醒來第一件事就是讀它，**它就不會忘記你的專案在幹嘛了。**

**不會寫？沒關係，直接跟 Claude 說：「幫我建一份 CLAUDE.md」，它會幫你寫好。**

---

## 💣 出問題了怎麼辦？

| 你看到什麼 | 怎麼辦 |
|-----------|--------|
| Claude 幫你改了一大堆檔案，結果畫面全壞了 | 用 VS Code 的「復原」功能（`Ctrl+Z` 或 `Cmd+Z`）。建議在 Claude 大改之前，先手動把資料夾複製一份備份。 |
| 某個外掛顯示「disconnected」 | 跟 Claude 說：「幫我檢查一下外掛設定是不是有問題」 |
| Claude 好像忘記你跟它說的事 | 檢查資料夾裡是不是有 `CLAUDE.md`。注意檔名要**全大寫**，`claude.md` 是不行的！ |

---

## ⚙️ 我想自己動手裝（進階玩家）

> 以下內容是給想手動設定的人看的。如果你用上面的一鍵安裝已經搞定了，這段可以跳過。

<details>
<summary>點這裡展開手動安裝步驟</summary>

### 外掛設定

編輯 `~/.claude/mcp.json`：

```json
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": ["chrome-devtools-mcp@latest"]
    },
    "supabase": {
      "url": "https://mcp.supabase.com/mcp"
    },
    "gcloud": {
      "command": "npx",
      "args": ["-y", "@google-cloud/gcloud-mcp"]
    },
    "cloudflare": {
      "command": "npx",
      "args": ["mcp-remote", "https://docs.mcp.cloudflare.com/mcp"]
    },
    "github": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "-e", "GITHUB_PERSONAL_ACCESS_TOKEN", "ghcr.io/github/github-mcp-server"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<你的 GitHub PAT>"
      }
    }
  }
}
```

### 技能包安裝

```bash
npx add-skill obra/superpowers -g -a claude-code -y
npx add-skill nextlevelbuilder/ui-ux-pro-max-skill -g -a claude-code -y
npx add-skill lgscvb/claude-code-quickstart -g -a claude-code -y
git clone https://github.com/affaan-m/everything-claude-code.git /tmp/everything-claude-code
cp -r /tmp/everything-claude-code/skills/* ~/.claude/skills/
rm -rf /tmp/everything-claude-code
```

### 用 debug 模式開 Chrome（macOS）

```bash
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222
```

</details>

---

## 🤝 貢獻

歡迎 PR 新增更多好用的外掛和技能包！

## 📄 License

MIT
