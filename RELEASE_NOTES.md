# CreAilo v0.1.0-alpha.7 — Windows 圖示與視窗修正

- 新增藍色素描 C 字 Logo，以前傾字形、速度線與多重筆觸呈現科技感，套用到程式 EXE、原生視窗、工作列與首頁。
- Windows 改用原生標題列與視窗邊框，最大化依系統工作區保留工作列空間。
- 移除重複的網頁視窗按鈕與自製拖曳、縮放處理，交由 Windows 處理視窗移動、縮放與 Snap Layouts。
- 延續 alpha.6 的畫布、文字與創作夥伴更新。

## 使用

下載 `CreAilo-v0.1.0-alpha.7-Windows-x64.zip`，完整解壓縮到新的資料夾後執行 `Start-CreAilo.cmd`，保留 `_internal`。適用 Windows 10/11 x64，需 Microsoft Edge WebView2 Runtime。

Windows 11 可使用原生最大化按鈕的 Snap Layouts、Win+Z 或 Win+方向鍵。是否顯示排列選單也取決於 Windows 的多工設定。Windows 10 不提供 Windows 11 的排列選單。

請先備份專案並使用副本測試；本版仍未簽章。CI 已驗證原生視窗、應用程式圖示與最大化工作區；Snap 排列選單仍需 Windows 11 實機確認。
