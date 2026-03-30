# ForgeView

macOS 桌面應用，為使用 Claude Code 的開發者打造。統一管理 OpenSpec 和 Crew 規格檔案，內嵌終端機直接執行 AI 輔助開發。

## 下載安裝

前往 [Releases](https://github.com/mark22013333/ForgeView/releases/latest) 下載最新版本。

| 平台 | 檔案 |
|------|------|
| macOS (Apple Silicon) | `forgeview-x.x.x-arm64.dmg` |
| macOS (Apple Silicon) | `forgeview-x.x.x-arm64.zip` |

### 系統需求

- **macOS 12+**（Monterey 以上）
- Apple Silicon (arm64)

### 安裝步驟

1. 下載 `.dmg` 檔案
2. 開啟後將 ForgeView 拖入 Applications 資料夾
3. **首次開啟前，請先執行以下指令**（每次更新後需重新執行一次）

> **⚠️ macOS 會阻擋未簽名的應用程式**
>
> 由於 ForgeView 尚未取得 Apple 開發者簽名，macOS 會顯示「已損毀，無法打開」的錯誤訊息。
> 這不是檔案損壞，而是 macOS Gatekeeper 安全機制的限制。
>
> **開啟終端機，貼上以下指令即可解決：**
>
> ```bash
> xattr -cr /Applications/forgeview.app
> ```
>
> 執行後即可正常開啟 ForgeView。**每次更新版本後需要重新執行一次。**

## 功能特色

### 跨專案規格管理
- 在一個介面中瀏覽所有專案的 OpenSpec 和 Crew 規格
- 合併顯示兩套系統的規格，統一狀態篩選
- 三種顯示模式：卡片網格 / 列表 / 迷你卡片
- Markdown 文件即時預覽（proposal、design、spec、tasks 等）

### 規格狀態自動推斷
- **Crew**：7 階段工作流（spec → db → arch → files → review → verify → log），根據 artifact 檔案自動判定進度
- **OpenSpec**：根據 tasks.md checkbox 完成百分比推斷狀態
- 支援手動覆蓋狀態（右鍵選單）

### 內嵌 Claude Code 終端機
- node-pty + xterm.js，開啟時自動 cd 到專案目錄
- 技能按鈕（Skill Bar）：點擊即送出 Claude Code slash command
- 支援多 session 持久化，切換專案時保留終端機狀態
- 可自訂 CLI 指令（claude / cc / 自訂 alias）

### 外部終端機整合
- 支援 iTerm2 和 Warp 一鍵啟動
- 自動帶入專案路徑和指令

### 佈局模式
- **預設佈局**：側邊欄 + 規格瀏覽器 + 可收合終端機
- **IDE 佈局**：三欄 IDE 風格，可調整面板寬度

### 外觀個人化
- 10+ 款內建主題（Catppuccin、Dracula、Nord、Solarized 等）
- 支援跟隨系統深色 / 淺色模式
- 匯入自訂主題（JSON）/ 自訂強調色、背景色
- 背景圖片 + 毛玻璃模糊效果
- UI 字體與終端機字體分別自訂

## 技術棧

| 層級 | 技術 |
|------|------|
| 框架 | Electron 33 |
| 前端 | React 19 + TypeScript 5 |
| 樣式 | TailwindCSS v4 |
| 終端機 | node-pty + xterm.js |
| 規格讀取 | crew-openspec-bridge |
| 打包 | electron-builder → DMG |

## 回報問題

如果遇到 bug 或有功能建議，請在 [Issues](https://github.com/mark22013333/ForgeView/issues) 中回報。

## 授權

MIT
