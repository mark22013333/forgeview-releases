# ForgeView

macOS 桌面應用，為使用 Claude Code 的開發者打造。統一管理 OpenSpec 和 Crew 規格檔案，內嵌終端機直接執行 AI 輔助開發。

**ForgeView 是 [CREW plugin](https://github.com/mark22013333/crew) 的 GUI 前端** — 所有 Notion 操作透過 CREW skill + Claude Code terminal 完成。

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

### 應用程式更新檢查（v0.6.0 新增）
- 透過 GitHub Release 自動比對版號，提示下載新版
- 設定頁「關於」區塊顯示動態版號，支援手動檢查更新按鈕
- 自動背景檢查（24 小時節流），可在設定中開關
- 更新可用時顯示 Release Notes 與一鍵下載 DMG

### Ribbon 技能列（v0.5.0 新增）
- Office 風格 Ribbon Bar，按功能分區：**規劃 / 開發 / 審查 / 輔助**
- Feature / Bug / OpenSpec 三組 tab 切換
- 每個按鈕有圖示 + 文字標籤 + 豐富 Tooltip（功能說明 + 產出檔案）
- 非線性 workflow — 可從任何階段啟動 skill，不限固定順序
- 涵蓋 CREW 全部 19 個 skill

### 建立任務精靈（v0.5.0 新增）
- 3 步驟引導：基本資訊 → 屬性設定 → 確認
- 自動建立 `.spec/` 規劃目錄 + Git 分支
- 支援 Feature 和 Bug 兩種任務類型
- 中文別名（displayName）讓 Spec 瀏覽器更易讀

### 跨專案規格管理
- 在一個介面中瀏覽所有專案的 OpenSpec 和 Crew 規格
- 合併顯示兩套系統的規格，統一狀態篩選
- 三種顯示模式：卡片網格 / 列表 / 迷你卡片
- Markdown 文件即時預覽（proposal、design、spec、tasks 等）
- 規格卡片一鍵「同步」「結案」— 直接送出 CREW skill 指令

### 規格狀態自動推斷
- **Crew**：7 階段工作流（spec → db → arch → files → review → verify → log），根據 artifact 檔案自動判定進度
- **OpenSpec**：根據 tasks.md checkbox 完成百分比推斷狀態
- 支援手動覆蓋狀態（右鍵選單）

### 內嵌 Claude Code 終端機
- node-pty + xterm.js，開啟時自動 cd 到專案目錄
- Ribbon 技能列：點擊即送出 Claude Code slash command
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
- 背景圖片 + 毛玻璃模糊效果 + 自動文字對比增強
- UI 字體與終端機字體分別自訂（最小 12px 確保可讀性）

## 更新日誌

### v0.6.0（2026-04-01）
- 應用程式更新檢查：透過 GitHub Release 自動比對版號，提示下載新版
- 設定頁「關於」區塊顯示動態版號，支援手動檢查更新按鈕
- 自動背景檢查（24 小時節流），可在設定中開關
- 更新可用時顯示 Release Notes 與一鍵下載 DMG

### v0.5.0（2026-03-31）
- 全新 Ribbon 技能列：按功能分區，圖示 + 文字 + 分隔線
- Hover 顯示豐富說明：功能名稱、指令、用途描述、產出檔案
- Feature / Bug / OpenSpec 三組技能 Tab 切換
- 建立任務精靈：3 步驟引導建立 .spec/ 規劃目錄 + Git 分支
- 規格卡片新增「同步」「結案」快捷按鈕
- 規格卡片支援中文別名（displayName）顯示
- Toast 通知系統升級：支援 info / error / success 三種類型
- 字體可讀性提升：最小字體 12px，透明模式自動增強對比
- 修正中文輸入法選字時意外送出的問題
- 設定頁面與主程式架構重構

### v0.4.0（2026-03-28）
- 規格歸檔功能
- 主題個人化（自訂顏色、毛玻璃、背景圖）
- 介面字體選擇器
- 移除專案確認對話框

### v0.2.0（2026-03-25）
- 外部終端機支援（iTerm2 / Warp）
- Toast 通知系統

### v0.1.0（2026-03-24）
- 初始版本

## 技術棧

| 層級 | 技術 |
|------|------|
| 框架 | Electron 33 |
| 前端 | React 19 + TypeScript 5 |
| 樣式 | TailwindCSS v4 |
| 終端機 | node-pty + xterm.js |
| 規格讀取 | crew-openspec-bridge |
| 打包 | electron-builder → DMG |

## 搭配使用

- **[CREW plugin](https://github.com/mark22013333/crew)** — Claude Code 的功能開發 + Bug 修復工作流 plugin
- **Claude Code** — Anthropic 的 CLI AI 助手

## 回報問題

如果遇到 bug 或有功能建議，請在 [Issues](https://github.com/mark22013333/ForgeView/issues) 中回報。

## 授權

MIT
