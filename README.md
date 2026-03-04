# 🚀 Claude Code & MCP 麻瓜專用一鍵起飛包（連阿嬤都能裝！）

這份指南專為「完全不懂寫程式」的新手設計。

不需要懂任何專業術語，你只要會**「按滑鼠右鍵、複製、貼上」**，就能把你的 VS Code 變成地表最強的 AI 開發神器！讓 Claude 自動幫你裝好所有進階工具。

---

## 🏰 第一關：先辦好你的通行證

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

## 🗂️ 第二關：建立你的第一個「工作資料夾」

> ⚠️ **這是最多新手踩到的坑！** 很多人打開 VS Code 就開始跟 Claude 亂聊，結果它幫你生出來的檔案散落在電腦各處，找都找不到。

**所以請先做這兩步：**

### 第一步：在桌面建一個新資料夾

在桌面空白處按「右鍵」→「新增資料夾」→ 取個**英文名字**，例如 `my-first-app`

### 第二步：把資料夾拖進 VS Code

直接用滑鼠把剛才建的資料夾**拖進 VS Code 視窗**裡面，它就會自動打開了。

> 💡 以後每次要做新的東西，都先建資料夾 → 拖進 VS Code → 再開始跟 Claude 聊。養成這個習慣，你的檔案就永遠不會亂飛！

---

## 🪄 第三關：施放一鍵安裝魔法

在 VS Code 裡面，打開左邊側邊欄的 Claude Code（那個**紫色圖示**），或者從畫面最上方的文字選單點「Terminal（終端機）」→「New Terminal」，然後輸入 `claude` 按 Enter。

當 Claude 醒來後，把下面這整段話**複製起來**，貼在對話框裡，按 Enter：

```
這是一個新專案，請先幫我在現在的資料夾建立一個 CLAUDE.md 檔案，這是我們未來的專案大腦。接著，請幫我讀取這個連結：https://raw.githubusercontent.com/lgscvb/claude-code-quickstart/main/setup.md ，並按照裡面的步驟，全自動幫我裝好所有工具！
```

接下來，**放開你的雙手**，看著 Claude 自動幫你裝好一切！

**你只需要做兩件事**：

1. 每次看到 Claude 問你「可以嗎？」→ 按 **Allow**（允許）
2. 瀏覽器跳出登入頁面時 → 輸入你的**帳號密碼**，然後按**同意**

就這樣。泡杯咖啡等它跑完 ☕

---

## 🎁 第四關：它剛剛幫你裝了什麼神兵利器？

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
| Context7 | [upstash/context7](https://github.com/upstash/context7) | 查最新文件 |
| Supabase | [supabase/supabase](https://github.com/supabase/supabase) | 資料庫管理 |
| Google Cloud | [google-cloud/gcloud-mcp](https://github.com/nichochar/gcloud-mcp) | 雲端管理 |
| Cloudflare | [cloudflare/mcp-server-cloudflare](https://github.com/cloudflare/mcp-server-cloudflare) | 網站管理 |
| GitHub | [github/github-mcp-server](https://github.com/github/github-mcp-server) | 程式碼管理 |
| Stitch | [_davideast/stitch-mcp](https://github.com/nichochar/stitch-mcp) | Firebase 整合 |
| Pencil | [pencil.dev](https://pencil.dev) | 設計工具（開 App 自動連接） |

**Skills 技能包：**

| 技能包 | 官方來源 | 說明 |
|-------|---------|------|
| Superpowers | [obra/superpowers](https://github.com/obra/superpowers) | 核心開發技能 |
| UI/UX Pro Max | [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | 頂級設計技能 |
| Everything Claude Code | [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code) | 全方位強化包（13 助手 + 56 技能） |
| 新手大補帖 | [lgscvb/claude-code-quickstart](https://github.com/lgscvb/claude-code-quickstart) | 速查手冊 + 學習系統 |

---

## 🕹️ 新手必學：兩個最重要的快捷鍵

在跟 Claude 聊天的對話框裡，按下鍵盤的 `Shift + TAB` 鍵，可以切換模式：

| 模式 | 白話說明 |
|------|---------|
| 🤖 **自動接受模式** | Claude 改檔案時「不用再問你」，直接幫你存檔。適合你完全信任它的時候。 |
| 📋 **規劃模式** | Claude **不會幫你改任何檔案**。它會單純跟你「討論想法、規劃怎麼做」。當你腦袋很亂的時候，切到這個模式跟它聊聊就對了！ |

> 💡 **建議流程**：先切到「規劃模式」跟 Claude 討論你想做什麼 → 討論完覺得 OK → 切回普通模式讓 Claude 開始動手做。

### 三種打開 Claude 的方式

| 你打的字 | 會發生什麼 |
|---------|-----------|
| `claude` | 開始一段全新的對話 |
| `claude -c` | 回到你上次聊到一半的地方（超實用！） |
| `claude -r` | 列出所有歷史對話，讓你挑一個繼續 |

---

## 📜 什麼是 CLAUDE.md？為什麼它超重要？

`CLAUDE.md` 就是一份「Claude 的大腦守則」。你在裡面寫什麼規則，Claude 每次開新對話都會先讀它。

**你可以這樣想**：Claude 每次開新對話都會失憶。但如果資料夾裡有一份 `CLAUDE.md`，它每次醒來都會先讀這份文件，就像給它灌入記憶一樣。**它就不會忘記你的專案在幹嘛了。**

### 裡面可以寫什麼？

隨便你寫！例如：
- 「回覆請用繁體中文（包含思考過程也要用繁體中文）」
- 「這個專案是一個幫人記帳的手機 App」
- 「每次寫程式碼都要用白話文解釋給我聽」
- 「不要在程式碼裡留 console.log」

**不會寫？沒關係，直接跟 Claude 說：「幫我建一份 CLAUDE.md」，它會幫你寫。**

### 進階技巧：用 CLAUDE.md 管理「做到一半的功能」

開發到一半，發現某個功能太難了、效益不高、或者暫時不想做？

**不要刪掉！** 請叫 Claude 把那段程式碼「註解掉」（就是讓電腦暫時跳過它，但程式碼還在），然後在 CLAUDE.md 裡面記錄一筆：

```
## 暫停開發的功能
- 📦 **購物車折扣功能**：太複雜了，等之後有空再做。程式碼已註解，在 cart.js 的第 50-80 行。
- 📦 **深色模式**：目前不急，先做核心功能。程式碼已註解，在 theme.js。
```

**為什麼要這樣做？** 因為如果你只是把程式碼註解掉但不記錄原因，下次 Claude 讀到一堆被註解的程式碼，它會很困惑：「這是要用的？還是不要的？要不要幫你打開？」寫在 CLAUDE.md 裡面，它一看就懂，不會亂動。

> 💡 刪掉了就浪費了，但留著不說明原因，Claude 就會被搞混。**CLAUDE.md 就是你和 Claude 之間的溝通橋樑。**

---

## 💣 出問題了怎麼辦？

### 安裝的時候

| 你看到什麼 | 怎麼辦 |
|-----------|--------|
| 黑框框一直跳紅字，說什麼 `npm command not found` | 這代表你沒裝 Node.js！安裝好之後，一定要把 VS Code **整個關掉再重開**（不是只關黑框框！） |
| Mac 跳出「無法驗證開發者」 | 去「系統設定」→「隱私與安全性」→ 往下滑找到「仍要允許」 |
| 安裝跑超久都沒反應 | 第一次裝會比較慢，正常要等 2-3 分鐘。超過 5 分鐘就檢查網路。 |

### 安裝完之後

| 你看到什麼 | 怎麼辦 |
|-----------|--------|
| Claude 幫你改了一大堆檔案，結果畫面全壞了 | 用 VS Code 的「復原」功能（`Ctrl+Z` 或 `Cmd+Z`）。建議在 Claude 大改之前，先手動把資料夾複製一份備份。 |
| 某個外掛顯示「disconnected」 | 跟 Claude 說：「幫我檢查一下外掛設定是不是有問題」 |
| 瀏覽器操控功能不能用 | 跟 Claude 說：「幫我用 debug 模式開 Chrome」 |
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
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
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
    },
    "stitch": {
      "command": "npx",
      "args": ["@_davideast/stitch-mcp", "proxy"]
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
