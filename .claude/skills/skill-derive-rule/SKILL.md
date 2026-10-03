---
name: skill-derive-rule
description:  給定一個已經寫好的 SOP 的 SKILL，使用者想要針對某個步驟，去展開該步驟需要遵守的規則，此時就必須呼叫此 SKILL。
---

# SOP

## Phase 1 — 定位目標步驟

1. READ 目標 skill 的 SKILL.md，找出使用者指定要展開規則的步驟。
2. ASK 指定的步驟無法唯一對應到 SOP 中的一步，或一次指定了多步時，請使用者指定唯一一步，取得答案才往下。
3. READ `rules/規則萃取判準.md`。
4. THINK 依規則萃取判準，從使用者口述與目標步驟抽出需要新增或改寫的規則。
   - 若與既有規則衝突 → ASK 使用者採用哪一方，附上衝突分析，取得答案才往下。
5. READ `rules/RuleFile-歸屬判斷.md`。
6. THINK 依 RuleFile 歸屬判斷，定出要追加或新開的 RuleFile 路徑。不必詢問使用者。

**產出**：目標步驟的位置、要新增或改寫的規則清單，以及要追加或新開的 RuleFile 路徑。

## Phase 2 — 寫出 RuleFile

1. DELEGATE `/skill-form-rule`，交付目標 skill、目標步驟、Phase 1 的規則清單與 RuleFile 路徑。
   - 若是追加 → 新規則接在既有規則之後，編號續接。
2. CHECK RuleFile 寫在 Phase 1 定出的路徑；追加時既有規則的內容與編號未被改動。不合就退回步驟 1。

**產出**：通過 `/skill-form-rule` 驗收的 RuleFile。

## Phase 3 — 把規則掛上 SOP

1. READ `rules/SOP-掛載規則.md`。
2. WRITE 依掛載規則，修改目標 skill 的 SKILL.md，讓目標步驟執行前才 READ 該 RuleFile。
3. READ `../skill-form-sop/rules/sop-格式規範.md` 與 `../skill-form-sop/rules/sop-撰寫原則.md`。
4. CHECK 逐條對照掛載規則、SOP 格式規範與撰寫原則，不合就退回步驟 2 修改。
5. REPORT 列出 SOP 修改的 Before／After、RuleFile 路徑，以及是追加還是新開，請使用者確認。

**產出**：已掛上 RuleFile 的 SOP，以及使用者對 Before／After 的確認。
