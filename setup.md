# Claude Code 初始化安裝指令

你好，Claude！請扮演專業的開發環境設定助手。使用者目前正在使用 VS Code 與 Claude Code，請協助他完成以下自動化環境配置。

## 任務目標

請自動設定並安裝指定的 MCP (Model Context Protocol) 伺服器與相關工具，讓使用者獲得最強大的開發體驗。

**重要原則**：使用者只需要做兩件事——(1) 按 Allow 同意權限 (2) OAuth 彈出時輸入帳密並按同意。其他全部由你自動完成。

---

## Step 0：帳號確認

在開始安裝前，先列出以下清單給使用者看，確認他們已經有這些帳號：

| 服務 | 必要？ | 註冊連結 | Google OAuth？ |
|------|--------|---------|:-------------:|
| **GitHub** | 是 | https://github.com/signup | 可用 Google 登入 |
| **Supabase** | 是 | https://supabase.com/dashboard | 可用 GitHub/Google 登入 |
| **Google Cloud** | 是 | https://console.cloud.google.com | 有 Google 帳號就有 |
| **Cloudflare** | 是 | https://dash.cloudflare.com/sign-up | 可用 Google 登入 |
| **Docker Desktop** | 選裝 | https://docker.com/get-started | GitHub MCP 需要 |
| **Pencil** | 選裝 | https://pencil.dev | — |

請問使用者：「你已經有以上帳號了嗎？如果還沒有，請先用 Google 帳號去註冊，只要有 Google 帳號幾乎全部都能一鍵登入。每個服務第一次都需要在瀏覽器跑一次 OAuth 同意授權，之後就不用了。準備好了請告訴我繼續。」

---

## Step 1：Node.js 環境處理（最優先！）

> 大多數的 MCP 底層都高度依賴 Node.js 環境。請確保電腦已經安裝 Node.js，並且安裝完後有重新啟動 VS Code 讓環境變數生效。

請執行以下檢查：

```bash
node --version
npm --version
```

### 情況 A：Node.js 未安裝
執行以下指令安裝 fnm（Fast Node Manager）和 Node.js LTS：

```bash
curl -fsSL https://fnm.vercel.app/install | bash
source ~/.zshrc
fnm install --lts
fnm default lts-latest
```

安裝完成後，**務必提醒使用者**：
> ⚠️ **請完全關閉 VS Code 再重新開啟**（不是只關 Terminal！），讓 PATH 環境變數生效。重新開啟後再回來繼續。

### 情況 B：Node.js 版本 < 18
```bash
fnm install --lts
fnm default lts-latest
```
同樣提醒使用者重啟 VS Code。

### 情況 C：Node.js >= 18
跳過此步驟，繼續下一步。

---

## Step 2：環境檢查

確認作業系統並檢查其他相依工具：

```bash
uname -s
docker --version 2>/dev/null || echo "Docker 未安裝（GitHub MCP 將無法使用，其他不受影響）"
```

如果 Docker 未安裝，告知使用者：「Docker 未安裝，GitHub MCP 將跳過。如果之後需要，可以到 https://docker.com 安裝 Docker Desktop。」

---

## Step 3：設定 MCP 伺服器

請尋找或建立 `~/.claude/mcp.json`。

**重要**：如果檔案已存在，請用 **merge** 的方式加入新的 MCP 設定（保留使用者原有的 MCP），不要覆蓋整個檔案。

需要加入的 MCP 伺服器設定：

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
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<請詢問使用者的 GitHub Personal Access Token>"
      }
    },
    "stitch": {
      "command": "npx",
      "args": ["@_davideast/stitch-mcp", "proxy"]
    }
  }
}
```

### 特殊處理

**GitHub MCP**：需要 Docker 和 GitHub Personal Access Token (PAT)。
- 如果 Docker 未安裝，跳過此 MCP 並告知使用者。
- 如果 Docker 已安裝，請詢問使用者的 GitHub PAT。告訴他們到 https://github.com/settings/tokens 建立，需要 `repo`, `read:org`, `read:user` 權限。

**Pencil MCP**：不需要寫入 mcp.json。告知使用者：「Pencil MCP 不需要額外設定，只要開啟 Pencil App（https://pencil.dev）就會自動連接到 Claude Code。」

---

## Step 4：安裝 Skills 技能包

依序執行以下安裝指令：

### 4.1 Superpowers（核心開發技能）
```bash
npx add-skill obra/superpowers -g -a claude-code -y
```

### 4.2 UI/UX Pro Max（設計技能）
```bash
npx add-skill nextlevelbuilder/ui-ux-pro-max-skill -g -a claude-code -y
```

每個安裝完成後確認成功：
```bash
ls ~/.claude/skills/ | grep -E "superpowers|ui-ux"
```

---

## Step 5：Chrome DevTools 設定與 OAuth 授權

### 5.1 Chrome Debug 模式

告訴使用者需要用特殊模式啟動 Chrome 才能讓 Claude 控制瀏覽器：

**macOS**：
```bash
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222
```

建議使用者建立一個 shell alias：
```bash
echo 'alias chrome-debug="/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222"' >> ~/.zshrc
source ~/.zshrc
```

以後只要輸入 `chrome-debug` 就能用 debug 模式開 Chrome。

### 5.2 OAuth 授權說明

告訴使用者：
> 🎉 **MCP 設定完成！**
>
> 部分 MCP（Supabase、Cloudflare、GCP）在第一次使用時會需要 OAuth 授權。屆時瀏覽器會自動彈出授權頁面。
>
> 👉 **你的唯一動作**：輸入帳號密碼，然後點「我同意」。剩下的 Token 抓取和跳轉都由 Claude 自動處理！

---

## Step 6：建立 CLAUDE.md 模板

在使用者的家目錄建立全域 CLAUDE.md：

```bash
cat > ~/.claude/CLAUDE.md << 'HEREDOC'
# 全域開發守則

## 語言偏好
- 回覆請使用繁體中文

## 程式碼風格
- 使用 2 空格縮排
- 優先使用 TypeScript
- 函式命名使用 camelCase

## 禁止事項
- 不要在程式碼中留下 console.log（除非是刻意的 debug）
- 不要在 commit 中包含 .env 檔案

## 提醒
- 每次啟動 Claude Code 都會讀取這份文件
- 可以隨時修改這裡的規則，Claude 會遵守
HEREDOC
```

告訴使用者：
> 📜 已在 `~/.claude/CLAUDE.md` 建立全域開發守則。這就像 Claude 的「永久記憶」，每次啟動都會讀取。你可以隨時修改裡面的規則！
>
> 另外，你也可以在每個專案的根目錄建立 `CLAUDE.md`，寫上該專案專屬的規範。

接著，**非常重要地**告訴使用者以下觀念（麻瓜防呆起手式）：

> 📂 **以後每次你想做新東西的時候，請先做這三步：**
>
> 1. **桌面新增資料夾** → 用英文命名（例如 `my-first-app`）
> 2. **複製路徑** → 右鍵資料夾 →「複製路徑」
> 3. **貼給 Claude** →「我要開始新專案了，請幫我把工作目錄切換到這裡：[貼上路徑]」
>
> 或者更簡單：**直接把資料夾拖進 VS Code 視窗！**
>
> 進入資料夾後，貼這句：「請在這個資料夾幫我建立一份 CLAUDE.md，並根據我們剛剛聊的想法，總結專案目標與開發注意事項。」
>
> ⚠️ **鐵律**：就算只是在聊天聊一個 prototype 想法，只要準備從聊天切換到 Plan Mode 開始認真做，就一定要先建立專案根目錄 + CLAUDE.md。不會寫沒關係，叫 Claude 幫你寫！

---

## Step 7：最終驗證與恭喜

執行環境總檢查：

```bash
echo "=== 🔍 環境總檢查 ==="
echo ""
echo "1. Node.js:" && node --version
echo "2. npm:" && npm --version
echo "3. Claude Code:" && claude --version 2>/dev/null || echo "   (在 VS Code 中使用，CLI 版本可能未安裝)"
echo ""
echo "4. MCP 設定檔："
cat ~/.claude/mcp.json 2>/dev/null | python3 -m json.tool > /dev/null 2>&1 && echo "   ✅ JSON 格式正確" || echo "   ❌ JSON 格式有誤，請檢查"
echo ""
echo "5. 已安裝的 MCP："
cat ~/.claude/mcp.json 2>/dev/null | python3 -c "import json,sys; d=json.load(sys.stdin); [print(f'   ✅ {k}') for k in d.get('mcpServers',{})]" 2>/dev/null
echo ""
echo "6. 已安裝的 Skills："
ls ~/.claude/skills/ 2>/dev/null | while read skill; do echo "   ✅ $skill"; done
echo ""
echo "7. CLAUDE.md："
test -f ~/.claude/CLAUDE.md && echo "   ✅ 全域 CLAUDE.md 已建立" || echo "   ❌ 未找到"
echo ""
echo "=== ✅ 檢查完畢 ==="
```

最後，用輕鬆幽默的語氣恭喜使用者：

> 🎉🎉🎉 **恭喜你！開發環境已經全副武裝！**
>
> 你現在擁有了：
> - 🌐 8 個 MCP 伺服器（瀏覽器操控、資料庫、雲端、版控…）
> - 🛠️ 2 組頂級技能包（全自動工程 + 頂級設計）
> - 📜 專屬的 CLAUDE.md 大腦守則
>
> **快速上手小秘訣：**
> - 按 `Shift+TAB` 可以切換自動接受模式 / 規劃模式
> - 輸入 `claude -c` 可以回到上次的對話
> - 輸入 `claude -r` 可以看所有對話歷史
>
> 歡迎來到新世界！🚀 開始你的第一個 AI 輔助開發專案吧！
