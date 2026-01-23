Patient Health Dashboard (SMART on FHIR)
本專案是一款基於 SMART on FHIR 標準開發的個人健康管理儀表板（Patient Health Dashboard）。旨在透過標準化的 FHIR 介面，跨醫療機構整合病患健康數據，並以直觀的視覺化圖表提供臨床檢驗趨勢、就醫行為分析與照護計畫追蹤，提升病患參與健康管理的效能。

核心功能與特色
本應用程式分為五大核心模組，全面覆蓋病患健康管理的需求：

數據趨勢總覽 (Overview)：整合生理量測數據（如血壓、BMI、體溫、心跳等），利用圖表呈現長期趨勢，幫助使用者快速掌握身體狀況。

健康事件時間軸 (Timeline)：彙整門急住診紀錄（Encounter）、疾病診斷（Condition）、處置項目（Procedure）與檢查報告（DiagnosticReport），以時間軸形式呈現完整的病歷發展歷程。

檢驗與報告分析 (Labs & Reports)：提供臨床檢驗數據的深度分析，支援不同檢驗項目的篩選與趨勢圖表顯示，並自動比對參考範圍（Reference Range）提供警示。

個人照護計畫 (CarePlan)：完整呈現醫療團隊制定的照護計畫與活動清單，支援依狀態（進行中、已完成、已取消）進行篩選與排序，強化醫病共同決策。

就醫利用率與覆蓋分析 (Utilization)：分析病患的就醫頻率、醫療機構分佈，並整合保險理賠結果（ExplanationOfBenefit, Claim）與預防接種紀錄（Immunization），掌握醫療資源使用狀況。

技術架構
開發語言/框架：HTML5, CSS3, JavaScript (Vanilla JS)。

FHIR 標準整合：使用 fhirclient.js 進行 OAuth2 認證與 FHIR Server 溝通。

數據視覺化：採用 Chart.js 結合 luxon 適配器，實現高效、精準的時間序列圖表呈現。

認證流程：符合 SMART App Launch 框架，支援引導式病患選擇介面（Patient Selection）。

應用之 FHIR 資源 (FHIR Resources)
本應用程式充分利用 FHIR R4 標準資源，包含但不限於：

基礎資訊：Patient

臨床數據：Observation, Condition, Procedure

檢驗診斷：DiagnosticReport, Laboratory Result (Observation)

流程管理：Encounter, CarePlan

行政與財務：Claim, ExplanationOfBenefit, Coverage

預防醫學：Immunization

快速上手
啟動認證：開啟 index.html，程式將引導至配置的 FHIR Server 進行 OAuth2 授權。

病患選擇：登入後，系統會分析伺服器上的病患列表，並標記數據豐富度（如「豐富資料」標籤），協助測試與展示。

瀏覽健康數據：進入儀表板後，可透過頂部導覽列切換「Overview」、「Timeline」、「Labs」、「CarePlan」及「Utilization」各個模組。

安全性聲明
本專案遵循最小權限原則，僅請求必要的 patient/*.read 權限。所有敏感資料均儲存於 sessionStorage 並在登出或重新啟動時清除，確保資料不留存於用戶端設備中。

關於「臺灣50」徵案
本應用程式致力於落實臺灣推動 FHIR 標準化之願景，透過標準化資料格式（TW Core IG 精神），實現醫療數據的互通與加值應用，提升臺灣智慧醫療之國際競爭力。
