---
name: skill-form-rule
description: 撰寫 skill 之 rules/ 底下 RuleFile 類型的檔案時，必須使用此 skill。
---

# SOP

## Phase 1 — 定出規則來源

1. READ `rules/RuleFile-格式規範.md` 與 `rules/RuleFile-撰寫守則.md`。
2. READ 目標 skill 的 SKILL.md，找出哪一步會 READ 這份 RuleFile、拿它來做什麼。
3. THINK 判斷輸入模式：使用者口述規則、從既有程式碼／文件歸納，或兩者並用。
   - 若兩者並用 → 口述為主，歸納結果只補充、不覆蓋口述。
4. ASK 目標 skill 或歸納來源無法從對話判斷時，問清楚「寫給哪個 skill」與「從哪些檔案歸納」才往下；其餘不必詢問使用者。

**產出**：目標 RuleFile 路徑、輸入模式、規則來源清單。

## Phase 2 — 收斂規則清單

1. READ 規則來源：口述內容，或 Phase 1 列出的程式碼／文件。
2. THINK 抽出候選規則，一條只規範一件事，標題寫成祈使句。
   - 若來源為程式碼／文件 → 只收錄重複出現的慣例，並記下出處路徑，留作 Example 素材。
3. THINK 為每條候選規則寫出判準。
   - 若寫不出 pass／fail 判準 → 該條不是規則，刪除或併入其他規則。
4. THINK 依讀者使用順序排列規則，決定編號。不必詢問使用者。

**產出**：規則清單，每條含標題、判準，歸納模式另含出處。

## Phase 3 — 寫出 RuleFile

1. WRITE 依格式規範，將每條規則的標題與描述條列寫入 `<目標 skill>/rules/<主題>-<類型>.md`。
2. WRITE 為每條規則補上 Good Example 與 Bad Example，寫入同一檔案。
   - 若為歸納模式 → 優先使用 Phase 2 記下的真實片段，不自行編造。

**產出**：RuleFile 草稿。

## Phase 4 — 驗收並交付

1. CHECK 逐條對照格式規範與撰寫守則，不合就退回 Phase 3 步驟 1 修改。
2. CHECK 拿每條規則的判準去套 Good 與 Bad：Good 必須 pass、Bad 必須 fail，不成立就退回 Phase 3 步驟 2 重寫範例。
3. REPORT 交出 RuleFile，列出規則清單與判準、歸納模式下每條的出處，並點名把握不足、需要使用者拍板的規則。

**產出**：可被目標 skill READ 的 RuleFile，以及待使用者確認的規則清單。
