# 測試版使用指南

## 安裝

macOS 下載包適用於 Apple Silicon。解壓縮 ZIP，將 `CreAilo.app` 拖入「應用程式」後開啟。此版本未經 Apple Developer 簽章及公證；若 macOS 阻止執行，請確認來源後查看「系統設定 → 隱私權與安全性」。不需安裝 Python 或 Node.js 才能啟動 CreAilo。

Windows v0.1.0-alpha.3 適用 Windows 10/11 x64。完整解壓縮後先執行 `Start-CreAilo.cmd`，保留 `_internal` 資料夾。需安裝 [Microsoft Edge WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/)。此測試包尚未簽章。

## 建立本機專案

從 Dashboard 建立專案，選擇你有寫入權限的資料夾。專案包含版面資料與素材，請備份整個資料夾。AI 功能可以稍後連接。

## 連接 AI

### Codex

依 [Codex CLI 官方文件](https://developers.openai.com/codex/cli/) 安裝 CLI，完成官方帳號登入後重新開啟 CreAilo。可在 AI 帳號選單查看連接狀態。帳號選單出現在 Dashboard 右上角，以及編輯頁右側工具列。

本測試版的圖片生成使用本機 Codex CLI。需要具有圖片生成能力的相容 CLI 版本與帳號；成功登入並不保證可生成圖片。圖片能力或額度不支援時，請回報錯誤訊息與 CLI 版本。

若軟體找不到 CLI，請確認其安裝位置。進階使用者可在啟動程式時設定 `AI_COMIC_CODEX_BIN` 指向可執行檔；目前尚無介面化路徑設定。

### Claude Code（選用）

依 [Claude Code 官方文件](https://code.claude.com/docs/en/quickstart) 安裝 CLI，使用自己的帳號登入，再於「創作夥伴」選擇 Claude。此連接用於協作規劃；生圖可另選 Codex 或 ComfyUI（Windows alpha.2）。

Claude 連接尚待更多實機測試。找不到 CLI 時，進階使用者可設定 `AI_COMIC_CLAUDE_BIN`。

## 第一個 Prompt 工作流

1. 匯入圖片作為參考素材。
2. 在工具列選擇 Prompt，點擊畫布放置並輸入描述。
3. 用選取工具 V，從元素邊界的節點拖曳連線：藍色連接參考素材，紫色連接生成目標。
4. 將 Prompt 連到 Frame 或 Panel。Panel 可以獨立放在 Frame 外。
5. 按下「生成圖片」。已有生成工作執行時，可加入佇列；生成完成後結果加入目標與 Assets。
6. 需要可編輯對白時，開啟「自動建立對白」。生成與對白配置可能需要不同的處理步驟。

節點在滑鼠靠近或拖曳連線時出現；已有連線的節點會保留。拖動已連接節點到空白處可拆除連線。

## 用聊天協作

打開「創作夥伴」，輸入簡短劇本，或使用 `@` 指定畫布元素。可以要求建立角色、安排 Frame 與 Panel、建立 Prompt 或修改對白。先用小規模指令測試，查看結果後再調整。

若只想排版，關閉「自動排程生圖」。AI 建立的內容仍可手動修改，模型也可能誤解指令。

## 編輯 Panel 內容

單擊選取 Panel，雙擊進入內容編輯。進入後，Panel 外框淡化，可選取內部圖片或對白。點擊外部或按 Esc 離開。

## 輸出與備份

使用輸出功能產生 PNG。若文字位置與畫布不同，請附上畫布與輸出結果回報。備份完整專案資料夾，不要只複製 `project.json`。

## ComfyUI（Windows v0.1.0-alpha.2）

另行啟動 ComfyUI 並安裝所需模型。在「生圖引擎」填入服務 API 位址，測試連接，再匯入 **API 格式**工作流 JSON。分別設定純文字與參考圖工作流，指定 Prompt、尺寸、種子和參考圖欄位；選擇 SaveImage 輸出。參考圖槽數必須符合實際連接的圖片數。程式不會自動下載模型。

使用 ComfyUI 生圖不需要 Codex 帳號；「自動建立對白」目前仍透過 Codex 配置。此版本已以模擬 ComfyUI 服務驗證串接，尚未完成真實 Qwen 模型推論測試。

### Windows 下載封鎖

若出現 `Failed to resolve Python.Runtime.Loader.Initialize`，可能是網路下載標記阻止 .NET 載入 DLL。alpha.3 的 `Start-CreAilo.cmd` 會解除本包 EXE、DLL、PYD 的下載封鎖，再啟動軟體，不會修改全域安全設定。請確認檔案來自官方 Release 後使用。舊版可先在 ZIP 右鍵「內容」勾選「解除封鎖」，套用後解壓縮到新資料夾；已解壓的舊資料夾仍可能保留封鎖。

### Windows alpha.4 自動準備 Codex

在 AI 帳號選單按「準備 Codex 元件並登入 ChatGPT」。程式會下載官方固定版本、驗證 SHA-256，完成後啟動官方瀏覽器登入，不需要手動安裝 Node.js 或 Codex CLI。下載需要網路；既有本機 Codex 仍可使用。元件獨立儲存在 `%LOCALAPPDATA%/CreAilo/runtimes`，帳號仍由 Codex 管理，未加入自動升級最新版功能。
