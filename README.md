# 🚀 Claude Code 新手大補帖：一鍵起飛懶人包

你剛裝好 VS Code 和 Claude Code？恭喜你踏入新世界！

這份懶人包會讓 Claude **自動幫你裝好一堆超強外掛**，裝完之後 Claude 就不只是會聊天而已 — 它可以幫你操作瀏覽器、管資料庫、管網站、甚至幫你做設計。

**你不需要懂任何技術，照做就好。**

---

## 🎯 怎麼用？三個動作搞定

### 動作一：先去辦帳號

下面這些服務等等會用到。好消息是，**你只要有 Google 帳號，幾乎全部都可以用「使用 Google 登入」一鍵搞定**。

每個網站第一次登入時，會跳出一個「是否同意授權」的頁面，按同意就好，之後就不會再問了。

| 去這裡辦 | 一定要？ | 用 Google 帳號就能辦？ |
|---------|:-------:|:-------------------:|
| [GitHub](https://github.com/signup)（程式碼託管平台） | ✅ 要 | ✅ 可以 |
| [Supabase](https://supabase.com/dashboard)（資料庫服務） | ✅ 要 | ✅ 可以 |
| [Google Cloud](https://console.cloud.google.com)（雲端服務） | ✅ 要 | 你有 Google 帳號就已經有了 |
| [Cloudflare](https://dash.cloudflare.com/sign-up)（網站管理） | ✅ 要 | ✅ 可以 |
| [Docker Desktop](https://docker.com/get-started)（容器工具） | 可以之後再裝 | — |
| [Pencil](https://pencil.dev)（設計工具） | 可以之後再裝 | — |

### 動作二：打開 Claude Code

在 VS Code 裡面，打開左邊側邊欄的 Claude Code（那個紫色圖示），或是打開終端機輸入 `claude`。

### 動作三：把下面這段話複製貼上

直接貼到 Claude Code 的對話框裡：

```
請讀取這個連結並幫我自動完成所有環境設定：https://raw.githubusercontent.com/lgscvb/claude-code-quickstart/main/setup.md
```

接下來 Claude 會自己跑一大堆安裝步驟。**你只需要做兩件事**：

1. 每次看到 Claude 問你「可以嗎？」→ 按 **Allow**（允許）
2. 瀏覽器跳出登入頁面時 → 輸入你的**帳號密碼**，然後按**同意**

就這樣。泡杯咖啡等它跑完 ☕

---

## 📂 超級重要！每次開新專案前一定要做的事

> 這是最多新手踩到的坑：打開 VS Code 就開始亂聊，結果 Claude 幫你生出來的檔案散落在電腦各處，找都找不到。

**請養成這個好習慣：**

### 第一步：在桌面建一個新資料夾

在桌面空白處按「**右鍵**」→「**新增資料夾**」→ 取個英文名字，例如 `my-app`

### 第二步：把資料夾丟進 VS Code

最簡單的方式：直接用滑鼠把資料夾**拖進 VS Code 視窗**裡面，它就會自動打開了。

### 第三步：叫 Claude 幫你建「大腦守則」

在 Claude Code 對話框貼這句：

```
請在這個資料夾幫我建立一份 CLAUDE.md，並根據我們剛剛聊的想法，總結專案目標與開發注意事項。
```

**為什麼要做這步？** 因為 Claude 每次開新對話都會失憶。但如果資料夾裡有一份 `CLAUDE.md`，Claude 每次啟動都會先讀這份文件，就像給它灌入記憶一樣。**它就不會忘記你的專案在幹嘛了。**

> ⚠️ **鐵律**：就算你只是隨便聊一個想法，只要聊到覺得「欸可以認真來做」的時候，就一定要先建資料夾 + 叫 Claude 建 `CLAUDE.md`。不會寫沒關係，叫 Claude 幫你寫就好！

---

## 📦 裝完之後你多了什麼超能力？

裝完之後，Claude 從一個「只會聊天的 AI」進化成「什麼都能幫你做的 AI」：

| 超能力 | 白話說明 |
|--------|---------|
| 🌐 **操控瀏覽器** | Claude 可以幫你開網頁、點按鈕、填表單。需要登入什麼服務時，它會自動開瀏覽器，你只要輸入帳密就好。 |
| 📚 **查最新文件** | 你問 Claude「React 的 useEffect 怎麼用」，它會去網路上撈最新的官方文件來回答你，不會給你過時的答案。 |
| 🗄️ **管理資料庫** | 你可以直接跟 Claude 說「幫我看一下資料庫裡有哪些使用者」，不用自己開後台操作。 |
| ☁️ **管理雲端** | Google Cloud 那些複雜的設定，直接用中文跟 Claude 說就好，不用記任何指令。 |
| 🌍 **管理網站** | 網域設定、DNS、網站部署，直接跟 Claude 說，不用登入 Cloudflare 後台。 |
| 🐙 **管理程式碼** | 幫你建立 PR（程式碼審查請求）、處理 Issue（問題回報），不用一直切換到 GitHub 網頁。 |
| 🎨 **設計能力** | 把設計稿直接變成程式碼，或是讓 Claude 幫你選配色、字型、UI 風格。 |
| 🛠️ **工程能力** | 自動幫你寫測試、除錯、做程式碼審查，像有一個資深工程師坐在旁邊。 |

---

## 💡 一定要知道的小秘訣

### 三種打開 Claude 的方式

| 你打的字 | 會發生什麼 |
|---------|-----------|
| `claude` | 開始一段全新的對話 |
| `claude -c` | 回到你上次聊到一半的地方（超實用！） |
| `claude -r` | 列出所有歷史對話，讓你挑一個繼續 |

### 切換工作模式

在對話中按 `Shift + TAB` 可以切換模式：

| 模式 | 什麼時候用 |
|------|-----------|
| 🤖 **自動接受模式** | Claude 做的每個修改都自動通過，不會一直問你「可以嗎」。適合你很信任它的時候。 |
| 📋 **規劃模式** | Claude 只跟你討論架構和計畫，**不會動任何檔案**。適合你還在想「到底要怎麼做」的時候。 |

> 💡 **建議工作流程**：先用「規劃模式」跟 Claude 討論你要做什麼 → 討論完覺得 OK → 切回普通模式讓 Claude 開始動手做。

### ⚠️ 危險模式（通常不要用）

```bash
claude --dangerously-skip-permissions
```

這會讓 Claude 不再問你「可以嗎」就直接做所有事情。**非常不建議用**，除非你非常清楚接下來會發生什麼。

---

## 📜 什麼是 CLAUDE.md？為什麼它超重要？

`CLAUDE.md` 就是一個純文字檔案，你可以在裡面寫下任何「規則」，Claude 每次啟動都會先讀它。

**你可以這樣想**：如果你請了一個新助理，你會希望他第一天上班先看一份「公司手冊」對吧？`CLAUDE.md` 就是那份手冊。

### 可以放在哪裡？

| 放的位置 | 效果 |
|---------|------|
| 你的個人設定資料夾裡 | 不管開哪個專案，Claude 都會遵守這些規則（例如「回覆都用繁體中文」） |
| 專案資料夾裡 | 只有在這個專案裡 Claude 才會遵守（例如「這個專案用 React」） |

### 裡面可以寫什麼？

隨便你寫！例如：
- 「回覆請用繁體中文」
- 「這個專案是用 React 做的購物網站」
- 「不要在程式碼裡留 console.log」
- 「每次改完程式都要跑一次測試」

**不會寫？沒關係，直接跟 Claude 說：「幫我建一份 CLAUDE.md」，它會幫你寫。**

---

## ❓ 出問題了怎麼辦？

### 跑安裝的時候卡住了

| 你看到的狀況 | 怎麼辦 |
|-------------|--------|
| Claude 說找不到某個指令 | 把 VS Code **整個關掉再重開**（不是只關下面的終端機！） |
| Mac 跳出「無法驗證開發者」 | 去「系統設定」→「隱私與安全性」→ 往下滑找到「仍要允許」 |
| 安裝跑超久都沒反應 | 第一次裝會比較慢，正常要等 2-3 分鐘。如果超過 5 分鐘，檢查你的網路。 |

### 安裝完之後遇到的問題

| 你看到的狀況 | 怎麼辦 |
|-------------|--------|
| 某個外掛顯示「disconnected」 | 跟 Claude 說：「幫我檢查一下 mcp.json 的設定是不是格式有錯」 |
| 瀏覽器操控功能不能用 | Chrome 需要用特殊方式開啟。跟 Claude 說：「幫我用 debug 模式開 Chrome」 |
| Claude 好像忘記你跟它說的事 | 檢查專案資料夾裡是不是有 `CLAUDE.md`。注意檔名要**全大寫**，`claude.md` 是不行的！ |
| Claude 整個打不開 | 跟 Claude 說：「幫我重新安裝 claude code」 |

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
