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

### Hot Reload 系統（v0.8.0 新增）
- JDK 管理：掃描本機 JDK、登錄 JetBrains Runtime，標示 DCEVM 支援
- HotswapAgent 下載與路徑設定，進度回報
- 依 JDK 類型自動組合 JVM 參數（DCEVM allow-unresolved、agent JAR、OPTS env key）
- 專案 Java target 偵測：解析 pom.xml/build.gradle 推測 compiler release / toolchain
- 自動挑選最佳 JDK：根據專案 target major 版本對應最相容的 JDK
- 服務啟動時注入 CATALINA_OPTS / JAVA_TOOL_OPTIONS，偵測 HOTSWAP AGENT 訊息並顯示 reload 次數
- 設定頁新增 JDK 管理分頁（掃描、新增、移除、驗證、HotswapAgent 下載）
- ServiceConfigModal 新增 Hot Reload 區段與 JDK 下拉選擇

### 多模組掃描強化（v0.8.0 新增）
- Maven 多模組專案自動解析 build.finalName 與 exploded WAR 路徑

### 每服務獨立 log buffer（v0.8.0 新增）
- renderer 端環形緩衝，切換服務不再遺失歷史 log

### 服務重新編譯（v0.8.0 新增）
- 不停服務直接重跑 compile 指令，配合 Hot Reload 即時生效

### 建置網路診斷（v0.8.0 新增）
- 識別 Connect timed out / Connection refused / UnknownHostException
- 識別 Could not HEAD/GET、Unable to load Maven meta-data
- 識別 SSLHandshakeException / PKIX path / certificate 問題
- 自動萃取問題 host，Toast 顯示並提供「改用離線模式重試」

### 離線建置勾選（v0.8.0 新增）
- 服務設定可啟用離線建置（Gradle `--offline` / Maven `-o`）

### 服務啟動器（v0.7.0 新增）
- 全新 Services tab，管理 Spring Boot / Maven WAR (Tomcat) / Node.js 等開發伺服器
- 範本快速建立服務設定、Maven 模組自動掃描
- 一鍵全啟 / 全停所有服務
- 即時日誌串流（LogViewer），支援自動捲動與手動鎖定
- Tomcat 隔離啟動：自動複製 conf 目錄、部署 WAR、獨立 CATALINA_BASE
- 結構化日誌檔寫入（含 ANSI 清除）

### 設定面板分頁式重構（v0.7.0 新增）
- 左側分類導覽 + 右側內容區，搜尋功能快速跳轉
- ⌘, 快捷鍵開啟/關閉設定面板
- 系統字體搜尋選擇器（macOS NSFontManager 原生列舉 + 即時預覽）
- 字體大小 +/- 微調按鈕
- Toast 通知強化：支援 warning 類型、自訂內容、複製/關閉按鈕

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
- UI 字體與終端機字體分別自訂（系統字體搜尋選擇器 + 即時預覽）

## 更新日誌

### v0.8.0（2026-04-19）
- Hot Reload 系統：JDK 管理 + HotswapAgent + DCEVM，即時反映程式碼變更無需重啟服務
- JDK 管理分頁：掃描本機 JDK、登錄 JetBrains Runtime、標示 DCEVM 支援
- 自動挑選最佳 JDK：依專案 Java target（pom.xml / build.gradle）對應最相容版本
- ServiceConfigModal 新增 Hot Reload 區段與 JDK 下拉選擇
- 多模組掃描強化：Maven 專案自動解析 build.finalName 與 exploded WAR 路徑
- 每服務獨立 log buffer：切換服務不再遺失歷史 log
- 服務重新編譯：不停服務直接重跑 compile 指令，配合 Hot Reload 即時生效
- 建置網路診斷：偵測 Maven/Gradle 連線錯誤並 Toast 提示改用離線模式
- 離線建置勾選：Gradle 自動加 --offline、Maven 自動加 -o
- vitest 單元測試框架：test 流程改為「單元測試 → build → e2e」

### v0.7.0（2026-04-10）
- 服務啟動器：全新 Services tab，管理 Spring Boot / Maven WAR (Tomcat) / Node.js 等開發伺服器
- 範本快速建立服務設定、Maven 模組掃描、一鍵全啟/全停
- 即時日誌串流（LogViewer）+ 結構化日誌檔寫入
- Tomcat 隔離啟動：自動複製 conf 目錄、部署 WAR、獨立 CATALINA_BASE
- 設定面板分頁式重構：左側分類導覽 + 搜尋 + ⌘, 快捷鍵開關
- 系統字體選擇器：macOS NSFontManager 原生列舉 + 搜尋即時預覽
- 字體大小 +/- 微調按鈕（介面字體與終端機字體皆適用）
- Toast 通知強化：支援 warning 類型、自訂內容、複製/關閉按鈕

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
