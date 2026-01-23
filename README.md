# Patient Health Dashboard - <br>SMART on FHIR 病患健康數據整合應用

本專案係為參加 **「臺灣 50」優良 SMART on FHIR 應用程式徵案活動** 所開發之示範應用。透過國際標準 **HL7 FHIR (R4)** 與 **SMART App Launch** 框架，實現以病患為中心的醫療數據跨院整合與視覺化監測。

## 📋 專案概述

本應用程式旨在解決醫療資訊破碎化的問題，讓醫療人員或病患能透過單一介面，快速瀏覽儲存於 FHIR Server 上的完整歷程。系統不僅提供生理數據趨勢，更進一步整合了照護計畫與保險利用情況。

### 核心功能
* **數據趨勢總覽 (Overview)**：自動抓取 `Observation` 資源，針對血壓、BMI、體溫、心跳、疼痛評分等指標進行長期趨勢繪圖。
* **醫療事件時間軸 (Timeline)**：整合 `Encounter`、`Condition`、`Procedure` 與 `DiagnosticReport`，以視覺化時間軸呈現病患完整的就醫脈絡。
* **檢驗與報告追蹤 (Labs & Reports)**：支援檢驗結果與參考範圍（Reference Range）對照，並提供報告內容的快速檢閱。
* **智慧照護計畫 (CarePlan)**：清晰展示醫囑與照護目標，提升病患服從性與醫病溝通效率。
* **資源利用分析 (Utilization)**：整合 `Claim`、`ExplanationOfBenefit` (EOB) 與 `Immunization`，協助追蹤醫療資源使用與疫苗接種狀況。

## 🛠 技術架構

* **標準規範**：HL7 FHIR R4
* **認證協議**：SMART App Launch (OAuth2 + PKCE)
* **前端架構**：Vanilla JavaScript, HTML5, CSS3 (採用模組化頁面設計)
* **數據視覺化**：Chart.js + Luxon (時間序列分析)
* **FHIR 整合庫**：`fhirclient.js`

## 📂 檔案結構說明

- `index.html`: 應用程式入口，執行 SMART Launch 授權引導。
- `patient-select.html`: 病患選擇介面，支援數據豐富度判別（Data Richness）。
- `overview.html`: 生理指標趨勢儀表板。
- `timeline.html`: 臨床事件時間軸。
- `labs.html`: 檢驗數據與診斷報告分析。
- `careplan.html`: 照護計畫追蹤。
- `utilization.html`: 醫療利用率與保險/疫苗資訊。

## 🚀 快速開始

1.  **設定 Client ID**：
    請在 `index.html` 中修改 `clientId` 為您在 FHIR Server (如：MOHW THAS) 註冊的客戶端編號。
    ```javascript
    FHIR.oauth2.authorize({
        clientId: "YOUR_CLIENT_ID",
        scope: "openid fhirUser patient/*.read",
        redirectUri: "patient-select.html",
        iss: "[https://thas.mohw.gov.tw/v/r4/sim/](https://thas.mohw.gov.tw/v/r4/sim/)..." // 測試伺服器網址
    });
    ```
2.  **部署**：
    本專案為純前端應用，可部署於任何支援 HTTPS 的靜態網頁伺服器（如 GitHub Pages 或 Vercel）。
3.  **運行**：
    存取 `index.html` 完成 OIDC 流程後，即可開始瀏覽病患數據。

## 🔐 安全性與隱私

- 符合 SMART on FHIR 安全標準，不儲存任何病患個資於伺服器端。
- 採用 **PKCE** (Proof Key for Code Exchange) 強化授權安全。
- 遵循最小權限原則，僅讀取經授權之 `patient/*.read` 資源。

## 🏆 參賽重點標註 (臺灣 50 徵案)

- **互操作性**：完全相容於臺灣 FHIR 實作指引 (TW Core IG) 精神，經測試已能接軌沙盒 FHIR Server。
- **使用者體驗**：專為臨床情境設計，將複雜的 JSON 數據轉化為易讀的圖表與時間軸。
- **擴展性**：模組化設計方便未來加入 AI 預測模型或更多 TW Core 資源。

---
*本專案係為技術展示用途，相關臨床診斷請以醫療機構正式報告為準。*
*本應用程式所顯示之所有健康數據、檢驗報告及趨勢圖表，僅供一般參考與個人健康管理輔助之用，不構成專業醫療建議、診斷或治療方案。*
*數據之準確性與及時性受限於來源端 FHIR Server 之品質，開發團隊不對原始數據的錯誤、遺漏或傳輸過程中的遺失承擔法律責任。*
*本介面僅對原始醫療數據進行彙整與視覺化呈現，系統本身不具備任何自動診斷或建議功能，請勿將其用於替代醫師之臨床判斷。*
*使用者應妥善保管其醫療機構之登入憑證，開發團隊對因使用者操作不當或裝置安全漏洞導致之資訊洩漏不負損害賠償責任。*
*在未經醫療人員確認前，請勿根據本應用程式之數據自行調整用藥或治療流程。*
