# Forgeview

macOS 桌面 App，為使用 Claude Code 的開發者打造。統一管理 OpenSpec 和 Crew 規格檔案，內嵌終端機直接執行 AI 輔助開發。

## 下載安裝

前往 [Releases](https://github.com/mark22013333/forgeview-releases/releases/latest) 下載最新版本。

### 系統需求

- **macOS 12+**（Monterey 以上）
- Apple Silicon (arm64) 或 Intel (x64)

### 安裝方式

1. 下載 `.dmg` 檔案
2. 開啟後將 Forgeview 拖入 Applications 資料夾
3. **首次開啟前，請先執行以下指令**（只需要一次）：

> **⚠️ 重要：macOS 會阻擋未簽名的 App**
>
> 由於 Forgeview 尚未取得 Apple 開發者簽名，macOS 會顯示「已損毀，無法打開」。
> 這不是檔案損壞，而是 macOS 的安全機制（Gatekeeper）。
>
> **打開終端機，貼上這行指令即可解決：**
>
> ```bash
> xattr -cr /Applications/Forgeview.app
> ```
>
> 執行後就能正常開啟 Forgeview。此指令只需執行一次。

## 功能

- **跨專案規格管理** — 在一個介面中瀏覽所有專案的 OpenSpec 和 Crew 規格
- **內嵌 Claude Code 終端機** — 點擊技能按鈕直接執行 AI 指令，支援多 session 持久化
- **自動狀態推斷** — 根據檔案和任務完成度自動判斷規格進度
- **10+ 主題** — Catppuccin、Dracula、Nord、Solarized 等，支援自訂主題和毛玻璃效果
- **IDE 佈局** — 三欄 IDE 風格佈局，可調整面板寬度
- **外部終端機整合** — 支援 iTerm2 和 Warp

## 螢幕截圖

<!-- TODO: 加入產品截圖 -->

## 回報問題

如果遇到 bug 或有功能建議，請在 [Issues](https://github.com/mark22013333/forgeview-releases/issues) 中回報。

## 更新日誌

詳見 [CHANGELOG.md](./CHANGELOG.md)

## 授權

Forgeview 是閉源商業軟體。
