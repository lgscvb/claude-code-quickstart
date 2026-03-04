# 🚀 Claude Code 新手大補帖：一鍵起飛懶人包

這是一份專為剛接觸 VS Code 與 Claude Code 的新手準備的**自動化設定指南**。透過這份指南，Claude Code 會自動幫你安裝並設定好最強大的擴充工具（MCP 與 Skills），讓你直接體驗「新世界」的開發效率！

---

## 🎯 第一步：如何一鍵安裝？

> **前置條件**：已安裝 VS Code + Claude Code 擴充套件

打開 VS Code，啟動 Claude Code（終端機輸入 `claude` 或用側邊欄），然後**直接把下面這段貼到對話框**：

```
請讀取這個連結並幫我自動完成所有 MCP 與 Skill 的安裝及環境設定：https://raw.githubusercontent.com/lgscvb/claude-code-quickstart/main/setup.md
```

接下來你只需要：
- ✅ 看到權限詢問時按 **Allow**
- ✅ 瀏覽器彈出時輸入**帳號密碼**並按**同意**
- ☕ 然後泡杯咖啡等它跑完

---

## 📋 安裝前：帳號申請清單

大部分服務都能用 **Google 帳號 OAuth 一鍵登入**，但第一次都需要在瀏覽器跑一次授權流程。

| 服務 | 必要？ | 註冊連結 | Google 登入？ |
|------|--------|---------|:------------:|
| **GitHub** | ✅ 必要 | [github.com/signup](https://github.com/signup) | ✅ |
| **Supabase** | ✅ 必要 | [supabase.com](https://supabase.com/dashboard) | ✅ |
| **Google Cloud** | ✅ 必要 | [console.cloud.google.com](https://console.cloud.google.com) | 有 Google 就有 |
| **Cloudflare** | ✅ 必要 | [dash.cloudflare.com](https://dash.cloudflare.com/sign-up) | ✅ |
| **Anthropic** | 已有 | 裝 Claude Code 時已完成 | — |
| **Docker Desktop** | 選裝 | [docker.com](https://docker.com/get-started) | GitHub MCP 需要 |
| **Pencil** | 選裝 | [pencil.dev](https://pencil.dev) | — |

> 💡 **只要有 Google 帳號，幾乎全部都能一鍵登入。**

---

## 📦 這個大禮包幫你裝了什麼？

### MCP 伺服器（讓 Claude 連接外部工具）

| MCP | 亮點 |
|-----|------|
| **Chrome DevTools** | 讓 Claude 擁有控制瀏覽器的能力！遇到 OAuth 授權時，Claude 幫你開網頁並操作流程。你只需輸入帳密並點「我同意」。 |
| **Context7** | 即時查詢任何程式庫的最新文件。問 Claude「React useEffect 怎麼用」，它會去撈最新官方文件回來回答你。 |
| **Supabase** | 直接在對話中管理你的 PostgreSQL 資料庫，無需切換到 Supabase 後台。 |
| **GCP** | 用自然語言管理 Google Cloud 資源，再也不用背 `gcloud` 指令。 |
| **Cloudflare** | 網管與部署神器！讓 Claude 直接幫你查詢 DNS 紀錄、管理網域設定，或是快速配置及重啟 Tunnel，甚至檢查 R2 儲存桶的狀態。再也不用登入 Cloudflare 後台找設定在哪裡。 |
| **GitHub** | 管理 PR、Issue、Repo，直接在對話中操作你的 GitHub 專案。需要 Docker。 |
| **Stitch** | Google 的 AI 設計工具，把設計稿轉成程式碼。 |
| **Pencil** | 設計工具，操作 `.pen` 檔。開啟 Pencil App 就自動連接，不需額外設定。 |

### Skills 技能包

| Skill | 亮點 |
|-------|------|
| **Superpowers** | TDD 測試驅動開發、系統化除錯、Git Worktree、Code Review、平行 Agent 派遣 — 讓 Claude 成為全自動工程師的核心引擎。 |
| **UI/UX Pro Max** | 前端救星。67 種 UI 風格、96 種配色、57 種字型配對、設計系統生成器。讓 Claude 具備頂級設計直覺。 |

---

## 📂 階段零：麻瓜專用的防呆起手式（開發前必讀）

很多新手打開 VS Code 就急著跟 Claude 聊天，結果最後做出來的檔案散落一地，連存在電腦哪裡都找不到。為了避免這種悲劇，**每次你想做點什麼**，請嚴格執行以下「防呆三步驟」：

### 第一步：去桌面新增資料夾

回到你的電腦桌面，在空白處點擊「**滑鼠右鍵**」 → 選擇「**新增資料夾**」 → 幫它取個名字（強烈建議用英文，例如 `my-first-app`）。

### 第二步：複製這個資料夾的路徑

對著你剛建好的資料夾點擊「**滑鼠右鍵**」 → 選擇「**複製路徑**」（Copy as path）。

### 第三步：貼給 Claude Code

回到 VS Code 的終端機啟動 `claude`，然後直接霸氣地對它說：

```
我要開始新專案了，請幫我把工作目錄切換到這裡：[按右鍵貼上你剛剛複製的路徑]
```

> 💡 **更暴力的做法**：直接把那個資料夾「拖曳」丟進 VS Code 的視窗裡，它就會自動打開了！

完成這三步，你所有的對話與檔案就會被安全地鎖在這個桌面資料夾裡，再也不怕弄丟！

### 後續銜接：建立 CLAUDE.md

順利進入資料夾後，如果你準備讓 Claude 開始寫程式，請直接貼這句話給它：

```
請在這個資料夾幫我建立一份 CLAUDE.md，並根據我們剛剛聊的想法，總結專案目標與開發注意事項。
```

以後每次開啟這個資料夾，Claude 就會自動讀取這份大腦守則，**不會失憶**！

> ⚠️ **鐵律**：就算只是在聊天聊一個 prototype 的想法，只要準備從「聊天模式」切換到「規劃模式（Plan Mode）」開始認真做，就一定要**先建立專案根目錄 + CLAUDE.md**。不會寫沒關係，叫 Claude 幫你寫就好！

---

## 💡 Claude Code 必學實用 Tips

### 1. 啟動指令

| 指令 | 功能 |
|------|------|
| `claude` | 標準啟動，開始一次全新的對話 |
| `claude -c` | 快速回到最近一次的對話，接續開發進度 |
| `claude -r` | 顯示過往對話歷史列表（含摘要），方便選擇繼續 |

### 2. 對話模式切換（快捷鍵：`Shift + TAB`）

| 模式 | 狀態 | 功能 | 適用場景 |
|------|------|------|---------|
| 🤖 自動接受編輯 | ⏵⏵ auto-accept edits on | 自動接受已允許的編輯指令 | 大量重複性編輯、信任度高的操作 |
| 📋 規劃模式 | ⏸ plan mode on | 只規劃不編輯，Claude 跟你討論架構 | 專案設計、流程規劃、需求分析 |

### 3. 危險權限模式（⚠️ 警語）

```bash
claude --dangerously-skip-permissions
```

允許所有權限，跳過安全檢查。**極不建議常態使用！** 僅在完全了解風險時才開啟。

---

## 📜 CLAUDE.md 的重要性

在專案根目錄建立 `CLAUDE.md`，是最高效的開發秘訣。

這個檔案就像專案的**「大腦守則」**。每次啟動 Claude Code 時，它都會優先讀取這份文件。

### 三層結構

| 位置 | 作用 | 共享 |
|------|------|------|
| `~/.claude/CLAUDE.md` | 全域個人偏好（語言、風格） | 僅自己 |
| `./CLAUDE.md` | 專案規範（技術棧、命名慣例） | Git tracked，團隊共享 |
| `./src/CLAUDE.md` | 子模組指示 | 模組級 |

### 你可以寫什麼

- 專案的技術棧版本
- 命名慣例
- 不允許使用的寫法
- 整體商業邏輯的簡介

### 效益

免去每次開新對話都要重新跟 Claude 解釋背景的麻煩，確保它寫出的程式碼**永遠符合你的規範**。

---

## ❓ 新手常見問題 FAQ

### 環境類

| 問題 | 解法 |
|------|------|
| `npx: command not found` | Node.js 沒裝，或裝完沒重啟 VS Code |
| 裝完 Node 但 VS Code 還是找不到 | **完全關閉 VS Code 再重開**（只關 terminal 不夠！） |
| `EACCES: permission denied` | 用 fnm 安裝 Node（不需 sudo）：`curl -fsSL https://fnm.vercel.app/install \| bash` |
| macOS 跳出「無法驗證開發者」 | 系統設定 → 隱私與安全性 → 仍要允許 |
| Node.js 版本太舊 | `fnm install --lts && fnm default lts-latest` |

### MCP 類

| 問題 | 解法 |
|------|------|
| MCP 顯示 disconnected | 檢查 `~/.claude/mcp.json` 格式：`cat ~/.claude/mcp.json \| python3 -m json.tool` |
| MCP 一直 connecting | npx 首次下載較慢，等 2-3 分鐘 / 檢查網路 |
| Chrome DevTools 連不上 | Chrome 要用 debug 模式啟動（見下方手動安裝說明） |
| Supabase OAuth 彈不出 | 允許瀏覽器彈出視窗 |

### Claude Code 類

| 問題 | 解法 |
|------|------|
| `claude: command not found` | `npm install -g @anthropic-ai/claude-code` |
| Skill 安裝了但叫不出來 | `ls ~/.claude/skills/` 確認有裝到 |
| Claude 不讀 CLAUDE.md | 檔名必須大寫 `CLAUDE.md`（不是 claude.md） |
| 認證失敗 | 到 [console.anthropic.com](https://console.anthropic.com) 確認 API Key / 訂閱狀態 |

---

## ⚙️ 手動安裝（進階）

如果你想自己動手，以下是完整的設定內容。

### MCP 設定

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

### Skills 安裝

```bash
npx add-skill obra/superpowers -g -a claude-code -y
npx add-skill nextlevelbuilder/ui-ux-pro-max-skill -g -a claude-code -y
```

### Chrome DevTools 啟動方式

macOS：
```bash
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222
```

---

## 🤝 貢獻

歡迎 PR 新增更多好用的 MCP 和 Skills！

---

## 📄 License

MIT
