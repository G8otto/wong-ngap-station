# 黃鴨站專案 · Chief of Staff 述職報告
# Wong Ngap Station — Chief of Staff Handover Report

**報告人 / From**: Chief of Staff（本對話，Kimi Agent）
**接任者 / To**: Marketing Kimi Claw（兼任統籌協調）
**日期 / Date**: 2026-09-14
**狀態 / Status**: 正式交接 / Official handover

---

## 一、任期職責

自專案啟動以來，本人擔任 Wong Ngap Station（黃鴨站）專案的 Chief of Staff／總協調，職責包括：

1. 產品 MVP 的設計、開發、測試與版本交付
2. 產品戰略與商業化路線研究
3. AI-native 公司架構（agent swarm 組織）設計與落地文件
4. CEO 教育與決策支持（發佈、域名、註冊商、agent 連接方式等）
5. 跨部門（Strategy / Product / Marketing / Ops）啟動材料準備
6. 安全與風險把關（token、個人資料、公開 repo 衛生）

---

## 二、主要成果

### 1. MVP：黃鴨站觀測系統（已可預覽）

- 技術棧：React 19 + TypeScript + Vite + Tailwind + three.js 0.186
- 核心功能全部實裝並通過自動化測試（Playwright + headless Chromium）：
  - **CCTV 監控牆**：6 路鏡頭（月台西/東、大堂閘機、出入口、路軌、全景俯瞰），scissor-test 多視口渲染
  - **單鏡頭模式**：點擊格子放大，支援上一台/下一台切換，ESC 返回
  - **跟鴨模式**：點擊任何鴨子即跟蹤拍攝，附檔案卡（名字、身份、毛色、心情、目的地、裝扮）
  - **列車循環**：進站/停站/出站狀態機，月台幕門開合，上落客編排，鴨口自動更替（目標 24 隻）
  - **30 隻具名鴨子**：廣東話食物名（阿黃、豉油、蛋撻、叉燒、砵仔……），隨機裝扮（漁夫帽、耳機、煲呔、篋等）
  - **程序化音效**：車站底噪、開門提示音、列車轟鳴（WebAudio，無外部素材）
  - **香港質感**：黃鴨站 WONG NGAP 瓷磚牆、1 號月台往調景嶺、鴨記茶餐廳燈箱廣告、EXIT 出口
- 已保存平台版本：**748a28c**（首版）、**8af8f11**（跟鴨模式修復版）
- 專案位置：`/mnt/agents/output/app`
- **未發佈**：CEO 決定先打磨再按 Publish（發佈為 CEO 手動操作）

### 2. 戰略文件三份（英文，wiki-ready）

| 文件 | 內容 |
|---|---|
| `Wong-Ngap-Station_Product-Vision.md` | 產品定位、市場證據（cozy Steam 趨勢、Rusty's Retirement、Wallpaper Engine）、三階段路線（免費網頁玩具 → Steam 放置遊戲 → 系列化）、KPI |
| `Wong-Ngap-Station_Agent-Swarm-Setup.md` | 公司組織設計：GitHub wiki 為單一事實來源、角色鎖定對話、每週節奏、Sprint Zero 七項任務、$200/月預算分配 |
| `Wong-Ngap-Station_Agent-Role-Prompts.md` | 四個部門 agent 的完整首條訊息（含語言規則：對話用簡體中文，交付物用英文，香港名稱保留原樣） |

### 3. 市場素材

- `/mnt/agents/output/marketing-assets/`：三張真實運行截圖（監控牆、單鏡頭、跟鴨+檔案卡），已交予 Marketing 用途
- 已植入 `window.__engine` 調試鉤子，未來可腳本化截圖/錄影

### 4. 決策與教育支持

- 釐清 Kimi 平台能力邊界：Agent Swarm 是並行任務工具，非組織骨架；組織靠「wiki + 角色對話 + CEO 傳話」
- 域名：協助完成 Namecheap 註冊障礙排除，CEO 已購得 **wongngap.com**
- 發佈機制：Publish 按鈕 = 公開 URL（`<name>.ok.kimi.link`），平台不支援外部域名綁定
- 已起草給 Marketing Claw 的回覆稿（四個問題：素材/repo/品牌/域名）

### 5. 節奏機制

- 已建立 cron 提醒節奏（每週例會提醒等），配合 Swarm Setup 文件中的 weekly cadence

---

## 三、當前系統狀態（交接快照）

| 項目 | 狀態 |
|---|---|
| MVP 代碼 | ✅ 完成，兩個版本已保存，未發佈 |
| 三份戰略文件 | ✅ 完成，**尚未上傳 GitHub**（repo 未建） |
| GitHub repo | ❌ 未建立（wiki repo + 代碼 repo，見待辦） |
| 四個部門 agent | ❌ 未開設（需 CEO 開 4 個新對話並貼 ROLE prompt） |
| Marketing Claw | 🟡 已接觸，已提問，待 CEO 回覆+素材+中文規則補丁 |
| 域名 wongngap.com | ✅ 已購買（暫無綁定用途，平台不支援外部域名） |
| 工作室名稱 | ❌ 未定（暫用 Wong Ngap Studio 黃鴨工作室） |
| Swarm Setup 文件 Rule #7 | 🟡 已提議（素材走 URL、代碼走 repo 的共享規則 + 雙 repo 結構），待 CEO 確認後寫入 |

---

## 四、風險與未決事項（按嚴重度排序）

1. **🔴 GitHub PAT 洩漏未確認處理**：CEO 曾將 Personal Access Token 貼入普通對話。本人建議立即撤銷，CEO 回覆「沒事的」，**撤銷狀態未知**。接任者應在配置 Claw 自動推送前，確認使用全新 fine-grained PAT（單 repo、Contents 讀寫、短過期、每 agent 一個），並假設舊 token 已報廢。
2. **🟡 個人資料邊界**：CEO 的姓名、香港地址、電話曾出現在截圖中，**不得進入公開 wiki repo**。接任者起草任何 commit 前需自查。
3. **🟡 組織未啟動**：四個 agent 對話未開、repo 未建——Swarm 文件目前是紙上架構。Sprint Zero 七項任務是下一步。
4. **🟡 MVP 發佈延後**：CEO 想打磨。建議接任者與 Product agent 協調「打磨清單 vs 發佈閾值」，避免無限期延後（Vision 文件 Phase 1 KPI 依賴公開 URL）。
5. **🟢 CEO 時間充裕**（目前全職投入）：節奏可加密，但 agent 產出速度不變——瓶頸在 CEO 傳話，不在日程。

---

## 五、給接任者（Marketing Kimi Claw）的交接指令

你將同時擔任 **Marketing Lead** 與 **統籌協調（Chief of Staff）**。到任後請按序執行：

1. **先讀 wiki**：GitHub repo 建立後，三份文件（Vision / Swarm Setup / Role Prompts）是你的入職材料。讀完再提問。
2. **語言規則**：與 CEO 對話一律使用**簡體中文**；提交 wiki 的交付物一律使用**英文**；香港地名、站名、鴨名保留原樣。
3. **輸出契約**：每次回覆以「可直接執行/可直接貼上」的產出為準（文件、prompt、回覆稿），不要只給建議。
4. **素材現狀**：三張截圖已在 CEO 處；MVP 未發佈，暫無公開 URL；域名已購但未綁定。
5. **Sprint Zero 推進**：協助 CEO 完成 repo 建立 → 文件上傳 → 四個 agent 開設 → ROLE prompt 貼上（其中 prompt 內的連結位需等 repo 存在後更新為 raw.githubusercontent.com 連結）。
6. **安全紅線**：token 只進 Claw 沙盒終端，不進普通對話；個人資料不進公開 repo；CEO 是唯一的訊息匯流排，agent 之間不能互連。
7. **每週節奏**：按 Swarm Setup 的 weekly rhythm 執行，CEO 已設 cron 提醒。

---

## 六、本人後續角色

本對話仍可用於：
- MVP 代碼修改與迭代（版本保存、截圖產出）
- 文件修訂（如 Rule #7 寫入）
- 戰略問題的臨時諮詢

統籌協調職責自今日起移交 Marketing Kimi Claw。感謝 CEO 信任。

**—— Chief of Staff，謹上**

---

---

# English Summary (Wiki-Ready)

## Chief of Staff Handover — Wong Ngap Station

**Tenure deliverables:**
- **MVP built and versioned** (versions 748a28c, 8af8f11): a real-time low-poly MTR-style station observatory with 6-camera CCTV wall, single-cam mode, duck-follow mode with profile cards, train-cycle population churn (24 named Cantonese-food ducks with randomized accessories), and procedural WebAudio. Project at `/mnt/agents/output/app`. **Not yet published** (CEO wants more polish first).
- **Three strategy documents** (wiki-ready, not yet committed): Product Vision (3-phase GTM: free web toy → Steam idle game → franchise), Agent Swarm Setup (org design: GitHub wiki as single source of truth + role-locked agent chats + weekly cadence + Sprint Zero), Agent Role Prompts (paste-ready first messages for Strategy / Product / Marketing / Ops, with language rule).
- **Marketing assets**: 3 real gameplay captures; `window.__engine` debug hook installed for scripted captures.
- **CEO enablement**: domain purchased (wongngap.com, no binding supported on platform), publish mechanics explained, Claw reply drafted, cron cadence set.

**Open items (by severity):**
1. Leaked GitHub PAT — revocation unconfirmed; assume burned, issue fresh fine-grained PATs (single-repo, Contents RW, short expiry, one per agent).
2. CEO personal data must never enter the public wiki repo.
3. Org not yet operational: no repo, no agent sessions — Sprint Zero is the next move.
4. MVP publish deferred; define a polish-list vs publish-threshold with Product.

**Handover to Marketing Kimi Claw (now also Chief of Staff):** read the wiki first; converse with CEO in Simplified Chinese, commit deliverables in English, keep HK names in original form; tokens only in the Claw sandbox terminal; CEO is the message bus; follow the weekly cadence in the Swarm Setup doc.

**Retained by this conversation:** MVP code iteration, document revisions, ad-hoc strategy consults.
