---
name: claude-code-quickstart
description: "Claude Code 新手大補帖。查看 Tips、模式切換、MCP 速查、CLAUDE.md 說明、常見問題。觸發詞：新手、tips、quickstart、懶人包、setup、環境設定、MCP 怎麼用。"
metadata:
  author: kevin
  version: "1.0.0"
---

# Claude Code 新手大補帖

安裝完成後的快速參考指南。包含 Tips、MCP 速查表、CLAUDE.md 說明、權限設定、常見問題。

---

## 💡 Claude Code Tips

### 啟動指令

| 指令 | 功能 |
|------|------|
| `claude` | 標準啟動，開始新對話 |
| `claude -c` | 快速回到最近一次的對話 |
| `claude -r` | 顯示對話歷史列表（含摘要），選擇要繼續的對話 |

### 對話模式切換（`Shift + TAB`）

在對話中按 `Shift+TAB` 切換模式：

| 模式 | 狀態顯示 | 功能 | 適用場景 |
|------|---------|------|---------|
| 🤖 自動接受編輯 | ⏵⏵ auto-accept edits on | 自動接受已允許的編輯指令 | 重複性編輯、信任度高的操作 |
| 📋 規劃模式 | ⏸ plan mode on | 只規劃不編輯，專注討論架構 | 架構設計、流程規劃、需求分析 |

### ⚠️ 危險權限模式

```bash
claude --dangerously-skip-permissions
```

允許所有權限，跳過安全檢查。**極不建議常態使用！** 僅在完全了解風險時才開啟。

---

## 📜 CLAUDE.md 的重要性

`CLAUDE.md` 就像專案的「大腦守則」。每次啟動 Claude Code 都會優先讀取。

### 三層結構

| 位置 | 作用 | 共享範圍 |
|------|------|---------|
| `~/.claude/CLAUDE.md` | 全域個人偏好（語言、風格） | 僅自己 |
| `./CLAUDE.md` | 專案規範（技術棧、命名慣例） | Git tracked，團隊共享 |
| `./src/CLAUDE.md` | 子模組指示 | 模組級 |

### 可以寫什麼

- 專案的技術棧與版本
- 命名慣例（camelCase / snake_case）
- 不允許使用的寫法
- 整體商業邏輯簡介
- 語言偏好（繁體中文 / English）

### 範例模板

```markdown
# 專案開發守則

## 技術棧
- React 19 + TypeScript + Vite
- Tailwind CSS v4
- Supabase (PostgreSQL)

## 命名慣例
- 元件：PascalCase（UserProfile.tsx）
- 函式：camelCase（getUserData）
- CSS：kebab-case（user-profile）

## 禁止事項
- 不使用 any 型別
- 不留 console.log
- 不 commit .env 檔案
```

---

## 📦 MCP 速查表

| MCP | 用途 | 一句話說明 |
|-----|------|-----------|
| **Chrome DevTools** | 瀏覽器操控 | 讓 Claude 控制 Chrome，幫你完成 OAuth 授權、測試網頁 |
| **Context7** | 文件查詢 | 即時查任何程式庫的最新文件（React、Next.js、Vue…） |
| **Supabase** | 資料庫 | 在對話中直接管理 PostgreSQL，不用開 Supabase 後台 |
| **GCP** | 雲端 | 用自然語言管理 Google Cloud 資源 |
| **Cloudflare** | 網管/部署 | 管理 DNS、Tunnel、R2、Workers，不用開 Cloudflare 後台 |
| **GitHub** | 版控 | 管理 PR、Issue、Repo（需 Docker） |
| **Stitch** | 設計→程式碼 | Google AI 設計工具，把設計稿轉成前端程式碼 |
| **Pencil** | 設計工具 | 操作 .pen 檔（開 Pencil App 自動連接，無需設定） |

### Chrome DevTools OAuth 流程

當 Claude 需要幫你做 OAuth 授權時：
1. Claude 用 Chrome DevTools 開啟授權頁面
2. **你**：輸入帳號密碼 + 點「我同意」
3. Claude：自動抓取 Token 並完成設定

> 前提：Chrome 需用 debug 模式啟動。終端機輸入 `chrome-debug`（如果有設 alias）或：
> ```bash
> /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222
> ```

---

## 🔐 權限設定

### settings.json 結構

`~/.claude/settings.json` 控制 Claude Code 的權限：

```json
{
  "permissions": {
    "allow": [
      "Bash(npm install:*)",
      "Bash(git *)",
      "Read",
      "Write",
      "Edit",
      "mcp__chrome-devtools__*",
      "mcp__context7__*",
      "mcp__supabase__*",
      "mcp__gcloud__*",
      "mcp__cloudflare__*",
      "mcp__github__*",
      "mcp__stitch__*"
    ]
  }
}
```

### 權限模式

| 模式 | 說明 |
|------|------|
| **Allow once** | 僅本次允許（下次還會再問） |
| **Allow always** | 永久允許（自動寫入 settings.json） |
| **互動模式（預設）** | 每次都詢問，最安全 |

### 安全提醒

- ❌ **永遠不要**把 API Key / Token 放在 git tracked 的檔案中
- ❌ **永遠不要**允許 `Bash(rm -rf *)` 這類危險指令
- ✅ 定期檢查 `~/.claude/settings.json` 中的 allow 列表

---

## ❓ 常見問題 FAQ

### 環境類

| 問題 | 解法 |
|------|------|
| `npx: command not found` | Node.js 沒裝 / 裝完沒重啟 VS Code |
| 裝完 Node 但 VS Code 還是找不到 | **完全關閉 VS Code 再重開**（關 terminal 不夠！） |
| `EACCES: permission denied` | 用 fnm 裝 Node（不需 sudo）：`curl -fsSL https://fnm.vercel.app/install \| bash` |
| macOS「無法驗證開發者」 | 系統設定 → 隱私與安全性 → 仍要允許 |
| Node.js 版本太舊 | `fnm install --lts && fnm default lts-latest` |

### MCP 類

| 問題 | 解法 |
|------|------|
| MCP 顯示 disconnected | 檢查 mcp.json 格式：`cat ~/.claude/mcp.json \| python3 -m json.tool` |
| MCP 一直 connecting | npx 首次下載較慢，等 2-3 分鐘 |
| Chrome DevTools 連不上 | Chrome 要用 debug 模式啟動（見上方說明） |
| Supabase OAuth 彈不出 | 允許瀏覽器彈出視窗 |
| GitHub MCP 無法啟動 | 確認 Docker Desktop 已啟動 + PAT 已設定 |

### Claude Code 類

| 問題 | 解法 |
|------|------|
| `claude: command not found` | `npm install -g @anthropic-ai/claude-code` |
| Skill 叫不出來 | `ls ~/.claude/skills/` 確認有裝到 |
| Claude 不讀 CLAUDE.md | 檔名必須大寫 `CLAUDE.md`（不是 claude.md） |
| 認證失敗 | 到 console.anthropic.com 確認 API Key / 訂閱狀態 |

---

## 🚀 下一步

環境就緒後，推薦的學習路徑：

1. 在任意專案資料夾啟動 `claude`，開始你的第一個 AI 輔助開發
2. 試試 `Shift+TAB` 切換到規劃模式，讓 Claude 先幫你設計架構
3. 用 Chrome DevTools 讓 Claude 幫你測試網頁
4. 在專案根目錄建立 `CLAUDE.md`，寫下專案規範
