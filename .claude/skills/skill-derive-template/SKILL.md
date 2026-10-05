---
name: skill-derive-template
description: 給定一個已經寫好的 SOP 的 SKILL，使用者想要針對某個步驟，規範該步驟產出檔案的格式（樣板），此時就必須呼叫此 SKILL。
---

# SOP

## Phase 1 — 定位目標步驟

1. READ 目標 skill 的 SKILL.md，找出使用者指定要抽出樣板的步驟。
2. ASK 指定的步驟無法唯一對應到 SOP 中的一步，或一次指定了多步時，請使用者指定唯一一步，取得答案才往下。
3. READ `rules/樣板萃取判準.md`。
4. THINK 依樣板萃取判準，從使用者口述、目標步驟原文與既有 RuleFile 抽出產出檔案的結構。
   - 若使用者要規範的屬於條列式規則 → ASK 是否改用 `/skill-derive-rule`，取得答案才往下。
5. READ `rules/樣板歸屬判斷.md`。
6. THINK 依樣板歸屬判斷，定出要新開樣板，或改寫哪一份既有樣板。不必詢問使用者。

**產出**：目標步驟的位置、標好出處的產出檔案結構，以及新開或要改寫的樣板。

## Phase 2 — 寫出樣板

1. DELEGATE `/skill-form-template`，交付目標 skill、目標步驟、Phase 1 的產出檔案結構，以及新開或要改寫的樣板。
2. CHECK `/skill-form-template` 交出的骨架與範例兩個檔案都存在；改寫時檔名未被改動。不合就退回步驟 1。

**產出**：通過 `/skill-form-template` 驗收的骨架與範例。

## Phase 3 — 把樣板掛上 SOP

1. READ `../skill-derive-rule/rules/SOP-掛載規則.md` 與 `rules/SOP-樣板掛載規則.md`。
2. WRITE 依 SOP 掛載規則與樣板掛載規則，修改目標 skill 的 SKILL.md，讓目標步驟執行前才 READ 骨架與範例。
3. WRITE 依樣板掛載規則，從目標步驟之前已 READ 的 RuleFile 刪除已搬進樣板的格式描述。
4. READ `../skill-form-sop/rules/sop-格式規範.md` 與 `../skill-form-sop/rules/sop-撰寫原則.md`。
5. CHECK 逐條對照兩份掛載規則、SOP 格式規範與撰寫原則，不合就退回步驟 2 修改。
6. REPORT 列出 SOP 與 RuleFile 修改的 Before／After、骨架與範例路徑、是新開還是改寫，以及共用該樣板的其他步驟，請使用者確認。

**產出**：已掛上樣板的 SOP，以及使用者對 Before／After 的確認。
