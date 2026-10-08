# CreAilo v0.1.0-alpha.7 — Windows 圖示與視窗修正

- 新增藍色素描 C 字 Logo，以前傾字形、速度線與多重筆觸呈現科技感，套用到程式 EXE、原生視窗、工作列與首頁。
- Windows 改用原生標題列與視窗邊框，最大化依系統工作區保留工作列空間。
- 移除重複的網頁視窗按鈕與自製拖曳、縮放處理，交由 Windows 處理視窗移動、縮放與 Snap Layouts。
- 新增安裝程式，後續安裝版可覆蓋升級；設定、專案與 Codex 元件儲存在程式目錄外，卸載也保留資料。
- 介面偏好改用固定 WebView 資料目錄，避免重啟或升級後遺失。
- 延續 alpha.6 的畫布、文字與創作夥伴更新。

## 使用

下載並執行 `CreAilo-v0.1.0-alpha.7-Windows-x64-Setup.exe`，完成安裝後從開始功能表或桌面開啟 CreAilo。適用 Windows 10/11 x64，需 Microsoft Edge WebView2 Runtime。

Windows 11 可使用原生最大化按鈕的 Snap Layouts、Win+Z 或 Win+方向鍵。是否顯示排列選單也取決於 Windows 的多工設定。Windows 10 不提供 Windows 11 的排列選單。

請先備份專案並使用副本測試；本版仍未簽章。CI 已驗證原生視窗、應用程式圖示與最大化工作區；Snap 排列選單仍需 Windows 11 實機確認。

既有 ZIP 版本可直接改用安裝版，不需要把專案複製進安裝資料夾；若專案未自動列出，使用「開啟資料夾」選擇原專案。首次安裝後，未曾持久保存的舊版介面偏好可能需要重新設定。
