# Claude Code 初始化安裝指令

你好，Claude！請扮演專業的開發環境設定助手。使用者目前正在使用 VS Code 與 Claude Code，請協助他完成以下自動化環境配置。

## 任務目標

請自動設定並安裝指定的 MCP (Model Context Protocol) 伺服器與相關工具，讓使用者獲得最強大的開發體驗。

**重要原則**：使用者只需要做兩件事——(1) 按 Allow 同意權限 (2) OAuth 彈出時輸入帳密並按同意。其他全部由你自動完成。

**跨平台原則**：本腳本支援 macOS、Linux 和 Windows。每個步驟執行前，請先判斷使用者的作業系統，自動選擇對應的指令。**不要問使用者用什麼系統，自己偵測。**

---

## Step 0：偵測作業系統 + 帳號確認

### 0.1 偵測作業系統

請先執行以下指令判斷使用者的系統：

```bash
uname -s 2>/dev/null || echo "Windows"
```

根據結果記住使用者的系統類型，後續步驟會用到：
- `Darwin` = macOS
- `Linux` = Linux
- `Windows` 或指令失敗 = Windows

> **Claude 內部備忘**：如果是 Windows，所有 shell 指令要改用 PowerShell 語法。`~` 要換成 `$env:USERPROFILE`，`cp -r` 要換成 `Copy-Item -Recurse`，`rm -rf` 要換成 `Remove-Item -Recurse -Force`，`cat` 要換成 `Get-Content`，`ls` 要換成 `Get-ChildItem`。

### 0.2 帳號確認

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

## Step 1：環境檢查

確認其他相依工具：

**macOS / Linux**：
```bash
docker --version 2>/dev/null || echo "Docker 未安裝（GitHub MCP 將無法使用，其他不受影響）"
git --version
```

**Windows（PowerShell）**：
```powershell
docker --version 2>$null; if (-not $?) { Write-Host "Docker 未安裝（GitHub MCP 將無法使用，其他不受影響）" }
git --version
```

如果 Docker 未安裝，告知使用者：「Docker 未安裝，GitHub MCP 將跳過。如果之後需要，可以到 https://docker.com 安裝 Docker Desktop。」

如果 Git 未安裝：
- **macOS**：`xcode-select --install`
- **Windows**：`winget install Git.Git`，然後重啟 VS Code
- **Linux**：`sudo apt install git` 或 `sudo yum install git`

---

## Step 2：設定 MCP 伺服器

請尋找或建立 MCP 設定檔。

**設定檔位置**：
- **macOS / Linux**：`~/.claude/mcp.json`
- **Windows**：`%USERPROFILE%\.claude\mcp.json`

**重要**：如果檔案已存在，請用 **merge** 的方式加入新的 MCP 設定（保留使用者原有的 MCP），不要覆蓋整個檔案。

需要加入的 MCP 伺服器設定：

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
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<請詢問使用者的 GitHub Personal Access Token>"
      }
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

## Step 3：安裝 Skills 技能包

依序執行以下安裝指令：

### 3.1 Superpowers（核心開發技能）
```bash
npx add-skill obra/superpowers -g -a claude-code -y
```

### 3.2 UI/UX Pro Max（設計技能）
```bash
npx add-skill nextlevelbuilder/ui-ux-pro-max-skill -g -a claude-code -y
```

### 3.3 新手大補帖（速查手冊 + 從錯誤中學習 + 邊做邊學系統）
```bash
npx add-skill lgscvb/claude-code-quickstart -g -a claude-code -y
```

這會安裝三個技能：
- **claude-code-quickstart**：速查手冊，忘記什麼就來翻
- **learn-from-mistakes**：每次遇到 bug 修完後，Claude 會自動把教訓記錄到 CLAUDE.md，下次不會再犯同樣的錯
- **explain-like-im-five**：Claude 每次寫程式碼都會用小學生聽得懂的方式解釋，讓你邊做邊學

### 3.4 Everything Claude Code（全方位強化包）

這是一個超級大禮包，包含多個專業助手與技能。
**⚠️ 注意：為了確保跨平台相容（Windows / Mac / Linux），請不要使用寫死的 Shell 指令。**

請你（Claude）判斷使用者目前的作業系統，並使用適合該系統的方法，完成以下操作：

1. 將 `https://github.com/affaan-m/everything-claude-code.git` clone 到系統的暫存目錄
2. 把 clone 下來的 `/skills` 資料夾內容，完整複製到使用者的 `~/.claude/skills/` 目錄下（Windows 為 `%USERPROFILE%\.claude\skills\`）
3. 清除暫存目錄中的 clone

這會幫使用者裝上一大堆進階技能，包括：
- **程式碼審查**：自動幫你檢查程式碼品質和安全性
- **測試驅動開發**：先寫測試再寫程式，減少 bug
- **多種程式語言支援**：TypeScript、Python、Go、Java 等
- **效能優化**：自動幫你省 token、省錢

每個安裝完成後確認成功：

**macOS / Linux**：
```bash
ls ~/.claude/skills/ | grep -E "superpowers|ui-ux|claude-code-quickstart|learn-from-mistakes|explain-like-im-five|everything-claude-code"
```

**Windows（PowerShell）**：
```powershell
Get-ChildItem "$env:USERPROFILE\.claude\skills" | Where-Object { $_.Name -match "superpowers|ui-ux|claude-code-quickstart|learn-from-mistakes|explain-like-im-five|everything-claude-code" }
```

---

## Step 4：Chrome DevTools 設定與 OAuth 授權

### 4.1 Chrome Debug 模式

告訴使用者需要用特殊模式啟動 Chrome 才能讓 Claude 控制瀏覽器：

**macOS**：
```bash
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222
```

建議建立一個 shell alias：
```bash
echo 'alias chrome-debug="/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222"' >> ~/.zshrc
source ~/.zshrc
```

**Windows（PowerShell）**：
```powershell
Start-Process "C:\Program Files\Google\Chrome\Application\chrome.exe" --ArgumentList "--remote-debugging-port=9222"
```

建議建立一個 PowerShell function（永久生效）：
```powershell
if (-not (Test-Path $PROFILE)) { New-Item -Path $PROFILE -Force }
Add-Content $PROFILE 'function chrome-debug { Start-Process "C:\Program Files\Google\Chrome\Application\chrome.exe" --ArgumentList "--remote-debugging-port=9222" }'
```

**Linux**：
```bash
google-chrome --remote-debugging-port=9222
```

以後只要輸入 `chrome-debug` 就能用 debug 模式開 Chrome。

### 4.2 OAuth 授權說明

告訴使用者：
> 🎉 **MCP 設定完成！**
>
> 部分 MCP（Supabase、Cloudflare、GCP）在第一次使用時會需要 OAuth 授權。屆時瀏覽器會自動彈出授權頁面。
>
> 👉 **你的唯一動作**：輸入帳號密碼，然後點「我同意」。剩下的 Token 抓取和跳轉都由 Claude 自動處理！

---

## Step 5：建立 CLAUDE.md 模板

在使用者的設定目錄建立全域 CLAUDE.md。

**macOS / Linux**：
```bash
cat > ~/.claude/CLAUDE.md << 'HEREDOC'
# 全域開發守則

## 語言與溝通
- 回覆請使用繁體中文（包含思考過程也用繁體中文）
- 每次寫程式碼時，用小學生都能聽懂的白話文解釋：這段程式碼在做什麼、為什麼要這樣寫、目的是什麼
- 解釋時不要用專業術語，如果一定要用，請加上白話文翻譯

## 從錯誤中學習
- 每次遇到錯誤或 bug，修完之後要在這份文件的「踩過的坑」區塊記錄：錯誤原因、怎麼修的、以後怎麼避免
- 不要重複犯同樣的錯誤，修之前先看「踩過的坑」

## 程式碼風格
- 使用 2 空格縮排
- 優先使用 TypeScript
- 函式命名使用 camelCase

## 禁止事項
- 不要在程式碼中留下 console.log（除非是刻意的 debug）
- 不要在 commit 中包含 .env 檔案

## 踩過的坑（Claude 自動記錄區）
<!-- Claude 會在這裡自動記錄每次犯錯的教訓 -->

## 暫停開發的功能
<!-- 做到一半暫時不想做的功能，記錄在這裡。程式碼已註解掉，等之後有空再打開。 -->
<!-- 格式：📦 **功能名稱**：暫停原因。程式碼在哪個檔案的第幾行。 -->

## 提醒
- 每次啟動 Claude Code 都會讀取這份文件
- 可以隨時修改這裡的規則，Claude 會遵守
- 這份文件也是 Claude 的「成長日記」，錯誤記錄會越來越豐富
- 如果程式碼裡有被「註解掉」的功能，先來這裡查「暫停開發的功能」，不要隨便打開或刪除
HEREDOC
```

**Windows（PowerShell）**：

請使用 Claude Code 的 Write tool 直接建立 `%USERPROFILE%\.claude\CLAUDE.md`，內容與上方 macOS/Linux 版本相同。

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

## Step 6：最終驗證與恭喜

執行環境總檢查：

**macOS / Linux**：
```bash
echo "=== 🔍 環境總檢查 ==="
echo ""
echo "1. MCP 設定檔："
cat ~/.claude/mcp.json 2>/dev/null | python3 -m json.tool > /dev/null 2>&1 && echo "   ✅ JSON 格式正確" || echo "   ❌ JSON 格式有誤，請檢查"
echo ""
echo "2. 已安裝的 MCP："
cat ~/.claude/mcp.json 2>/dev/null | python3 -c "import json,sys; d=json.load(sys.stdin); [print(f'   ✅ {k}') for k in d.get('mcpServers',{})]" 2>/dev/null
echo ""
echo "3. 已安裝的 Skills："
ls ~/.claude/skills/ 2>/dev/null | while read skill; do echo "   ✅ $skill"; done
echo ""
echo "4. CLAUDE.md："
test -f ~/.claude/CLAUDE.md && echo "   ✅ 全域 CLAUDE.md 已建立" || echo "   ❌ 未找到"
echo ""
echo "=== ✅ 檢查完畢 ==="
```

**Windows（PowerShell）**：
```powershell
Write-Host "=== 🔍 環境總檢查 ===" -ForegroundColor Cyan
Write-Host ""
Write-Host "1. MCP 設定檔："
$mcpPath = "$env:USERPROFILE\.claude\mcp.json"
if (Test-Path $mcpPath) {
    try { Get-Content $mcpPath | ConvertFrom-Json | Out-Null; Write-Host "   ✅ JSON 格式正確" } catch { Write-Host "   ❌ JSON 格式有誤，請檢查" }
} else { Write-Host "   ❌ 找不到 mcp.json" }
Write-Host ""
Write-Host "2. 已安裝的 MCP："
if (Test-Path $mcpPath) { (Get-Content $mcpPath | ConvertFrom-Json).mcpServers.PSObject.Properties | ForEach-Object { Write-Host "   ✅ $($_.Name)" } }
Write-Host ""
Write-Host "3. 已安裝的 Skills："
Get-ChildItem "$env:USERPROFILE\.claude\skills" -ErrorAction SilentlyContinue | ForEach-Object { Write-Host "   ✅ $($_.Name)" }
Write-Host ""
Write-Host "4. CLAUDE.md："
if (Test-Path "$env:USERPROFILE\.claude\CLAUDE.md") { Write-Host "   ✅ 全域 CLAUDE.md 已建立" } else { Write-Host "   ❌ 未找到" }
Write-Host ""
Write-Host "=== ✅ 檢查完畢 ===" -ForegroundColor Cyan
```

最後，用輕鬆幽默的語氣恭喜使用者：

> 🎉🎉🎉 **恭喜你！開發環境已經全副武裝！**
>
> 你現在擁有了：
> - 🌐 5 個 MCP 伺服器（瀏覽器操控、資料庫、雲端、版控…）
> - 🛠️ 4 組頂級技能包（全自動工程 + 頂級設計 + 學習系統 + 全方位強化）
> - 📜 專屬的 CLAUDE.md 大腦守則
>
> **快速上手小秘訣：**
> - 按 `Shift+TAB` 可以切換自動接受模式 / 規劃模式
> - 輸入 `claude -c` 可以回到上次的對話
> - 輸入 `claude -r` 可以看所有對話歷史
>
> 歡迎來到新世界！🚀 開始你的第一個 AI 輔助開發專案吧！
