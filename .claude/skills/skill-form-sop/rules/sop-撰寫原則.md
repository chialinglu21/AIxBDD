# Rule 1 - 判準、檢查清單、schema 放 rules/ 或 references/，樣板放 templates/

- 強度：必須
- SOP 只留骨幹：做什麼、依據哪份文件、產出什麼。
- 判準、檢查清單、schema 寫進 `rules/` 或 `references/`；產出檔案的樣板寫進 `templates/`，骨架與範例各一份。
- SOP 步驟只寫 READ 該文件、再「依 <文件名>」執行。

## Good Example

- 主題比對與路徑分支都寫在 `RuleFile-歸屬判斷.md`，SOP 只讀進文件、再依它定出路徑。

```markdown
5. READ `rules/RuleFile-歸屬判斷.md`。
6. THINK 依 RuleFile 歸屬判斷，定出要追加或新開的 RuleFile 路徑。不必詢問使用者。
```

## Bad Example

- 同一步把判準直接寫在 SOP 的子句裡，沒有 RuleFile 可以 READ；判準要補充時只能一直往 SOP 裡加子句。

```markdown
5. THINK 比對使用者口述的規則主題與目標步驟已 READ 的 RuleFile 主題，定出 RuleFile 路徑。不必詢問使用者。
   - 若主題相同 → 追加到該 RuleFile。
   - 若主題不同或沒有既有 RuleFile → 新開 `<目標 skill>/rules/<主題>.md`。
```

# Rule 2 - SOP 不重述 rules/ 已定義的內容

- 強度：必須
- rules/ 已經定義的內容（強度、格式細節、檢查項目），SOP 步驟只寫「依 `<檔名>`」，不在步驟裡重新說明一次。
- 同一個概念只在一個地方定義，SOP 只負責寫出做什麼、依據哪份文件。

## Good Example

- 驗收步驟只寫「對照格式規範」，強度怎麼判斷交給格式規範自己定義，SOP 保持一行一件事。

```markdown
## Phase 3 — 驗收並交付

1. CHECK 逐條對照格式規範，不合就退回 Phase 2 步驟 2 修改。
2. CHECK 拿每條規則去套它的 Good 與 Bad：Good 符合、Bad 違反才算通過，否則退回 Phase 2 步驟 2 重寫範例。
3. REPORT 交出 RuleFile，列出規則清單、每條的強度、違反時的結果與出處，請使用者確認。
```

## Bad Example

- 同一個驗收階段，把格式規範裡 `必須`、`建議` 的定義又拆成兩個步驟重寫一次；格式規範一改，SOP 就跟著過時。

```markdown
## Phase 3 — 驗收並交付

1. CHECK 逐條對照格式規範中強度為 `必須` 的規則，不合就退回 Phase 2 步驟 2 修改。
2. CHECK 逐條對照強度為 `建議` 的規則，不符合的必須有記下的理由；沒有理由就退回 Phase 2 步驟 2 修改。
3. REPORT 交出 RuleFile，列出規則清單、每條的強度、違反時的結果與出處，請使用者確認。
```

# Rule 3 - 已有 script、subagent 或 skill 能完成的步驟用 DELEGATE

- 強度：必須
- 已經有 script、subagent 或其他 skill 能完成的步驟，用 DELEGATE 寫出對象名稱與交付內容。
- 不在 SOP 裡展開被委派對象的實作步驟。

## Good Example

- 寫 RuleFile 交給 `/skill-form-rule`，SOP 只寫交付什麼，寫法與驗收都由該 skill 負責。

```markdown
1. DELEGATE `/skill-form-rule`，交付目標 skill、目標步驟、Phase 1 的規則清單與 RuleFile 路徑。
```

## Bad Example

- 同一件事把 `/skill-form-rule` 的步驟抄進來，同一套流程在兩個 skill 各寫一次；`/skill-form-rule` 一改，這裡就過時。

```markdown
1. READ `../skill-form-rule/rules/RuleFile-格式規範.md`。
2. WRITE 依格式規範，將規則清單寫入 Phase 1 定出的 RuleFile 路徑。
3. CHECK 逐條對照格式規範，不合就退回步驟 2 修改。
```

# Rule 4 - 文件在第一次用到的那一步才 READ

- 強度：必須
- READ 步驟放在第一次用到該文件的 Phase，不在 Phase 1 預先讀入所有文件。
- 同一份文件在多個 Phase 都會用到時，只在第一次用到的地方 READ 一次。

## Good Example

- Phase 1 只讀收斂規則需要的目標 skill 檔案；格式規範到 Phase 2 準備動筆時才讀，兩類資訊不會在同一個階段混在一起。

```markdown
## Phase 1 — 收斂規則清單

1. READ 目標 skill 的 SKILL.md 與相關檔案，找出哪一步會 READ 這份 RuleFile、要它規範什麼。
2. THINK 從使用者口述與上一步讀到的檔案抽出規則，一條只規範一件事，記下每條的出處。

## Phase 2 — 寫出 RuleFile

1. READ `rules/RuleFile-格式規範.md`，這是 RuleFile 唯一的格式規範，不參照其他文件的格式。
2. WRITE 依格式規範，將規則清單寫入 Phase 1 定出的 RuleFile 路徑。
```

## Bad Example

- 格式規範在 Phase 1 第一步就讀進來，但收斂規則時根本用不到，格式細節和目標 skill 的內容混在一起，干擾規則的判斷。

```markdown
## Phase 1 — 收斂規則清單

1. READ `rules/RuleFile-格式規範.md`。
2. READ 目標 skill 的 SKILL.md 與相關檔案，找出哪一步會 READ 這份 RuleFile、要它規範什麼。
3. THINK 從使用者口述與上一步讀到的檔案抽出規則，一條只規範一件事，記下每條的出處。

## Phase 2 — 寫出 RuleFile

1. WRITE 依格式規範，將規則清單寫入 Phase 1 定出的 RuleFile 路徑。
```

# Rule 5 - 兩個人照做會做出不同東西的步驟要寫死

- 強度：必須
- 逐步驟自問：兩個沒有上下文的人照做，會不會做出不同的東西。
- 會的話，把那一步的位置、格式或判斷依據寫明，直到只有一種做法。

## Good Example

- 路徑格式寫死成 `<目標 skill>/rules/<檔名>.md`，誰來做都會放在同一個位置。

```markdown
6. THINK 定出 RuleFile 路徑 `<目標 skill>/rules/<檔名>.md`。不必詢問使用者。
```

## Bad Example

- 同一步只說「決定放哪裡」，有人放進目標 skill 的 `rules/`，有人放進執行中的 skill 底下，SOP 照 `rules/<檔名>.md` READ 時可能找不到。

```markdown
6. THINK 決定 RuleFile 要放在哪裡。不必詢問使用者。
```
