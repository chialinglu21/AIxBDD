# Rule 1 - 比對範圍是同一 Phase 中目標步驟之前已 READ 的 RuleFile

- 強度：必須
- 候選的既有 RuleFile，是目標步驟所在 Phase 裡、目標步驟之前所有 READ 步驟列出的 RuleFile，不只看正前方那一步。
- 其他 Phase READ 的 RuleFile 不列入比對。

## Good Example

- 要為 Phase 3 步驟 4 的 CHECK 展開「核對退回引用」的規則。往前看到步驟 3 READ 的 SOP 規範，也看到步驟 1 READ 的 `SOP-掛載規則.md`；後者和新規則同一個主題，所以決定追加。

```markdown
## Phase 3 — 把規則掛上 SOP

1. READ `rules/SOP-掛載規則.md`。
2. WRITE 依掛載規則，修改目標 skill 的 SKILL.md，讓目標步驟執行前才 READ 該 RuleFile。
3. READ `../skill-form-sop/rules/sop-格式規範.md` 與 `../skill-form-sop/rules/sop-撰寫原則.md`。
4. CHECK 逐條對照掛載規則、SOP 格式規範與撰寫原則，不合就退回步驟 2 修改。
```

## Bad Example

- 同一個情境只看步驟 3，兩份 SOP 規範都和「核對退回引用」不同主題，於是新開 `SOP-引用核對.md`，和 `SOP-掛載規則.md` 的 Rule 6 重複規範同一件事。

```markdown
3. READ `../skill-form-sop/rules/sop-格式規範.md`、`../skill-form-sop/rules/sop-撰寫原則.md` 與 `rules/SOP-引用核對.md`。
4. CHECK 逐條對照掛載規則、SOP 格式規範與撰寫原則，不合就退回步驟 2 修改。
```

# Rule 2 - 規範的對象相同就追加到該 RuleFile

- 強度：必須
- 新規則與比對範圍內某份 RuleFile 規範同一個對象的同一個面向，才算主題相同。
- 只是把關同一個步驟、或同一行 READ 進來，不代表主題相同。
- 主題相同時追加到該檔案，不另開新檔；同一個主題的規則只放在一份 RuleFile 裡。

## Good Example

- 為 Phase 2 步驟 2 展開「只有 is-a 關係才畫繼承」，步驟 1 同一行 READ 了語法規範與關係選用原則。新規則規範的是選用哪種關係，和 `類別關係選用原則.md` 同主題，所以追加到這份檔案，SOP 的 READ 不用改。

```markdown
1. READ `rules/mermaid-classdiagram-語法.md` 與 `rules/類別關係選用原則.md`。
2. WRITE 依語法規範與關係選用原則，將 Phase 1 得出的類別組成畫成 mermaid classDiagram，存入 `docs/design/<功能名稱>-class-diagram.md`。
```

```markdown
plan-with-class-diagram/rules/
├── mermaid-classdiagram-語法.md
├── 實作一致性核對規則.md
├── 類別設計原則.md
└── 類別關係選用原則.md      ← 追加 Rule N+1
```

## Bad Example

- 同一條規則因為 `mermaid-classdiagram-語法.md` 排在同一行 READ 的第一個，就追加進去，語法規範裡混入了關係選用的判斷。另開 `繼承使用原則.md` 也一樣錯：關係選用的判斷會分散在兩份檔案裡。

```markdown
plan-with-class-diagram/rules/
├── mermaid-classdiagram-語法.md  ← 追加 Rule N+1
├── 實作一致性核對規則.md
├── 類別設計原則.md
└── 類別關係選用原則.md
```

# Rule 3 - 新開的 RuleFile 放在目標 skill 的 rules/ 底下

- 強度：必須
- 新開 RuleFile 的路徑固定為 `<目標 skill>/rules/<檔名>.md`。
- 不放在本 skill、其他 skill 或 repo 的其他目錄，否則目標 SOP 用 `rules/<檔名>.md` READ 時會找不到檔案。

## Good Example

- 為 `plan-with-class-diagram` Phase 3 的 CHECK 新開的檔案，放在該 skill 自己的 `rules/` 底下，SOP 的 `READ rules/實作一致性核對規則.md` 可以直接讀到。

```markdown
.claude/skills/plan-with-class-diagram/rules/實作一致性核對規則.md
```

## Bad Example

- 同一份檔案被放在執行展開的 `skill-derive-rule/rules/` 底下，`plan-with-class-diagram` 的 SOP 照 `rules/實作一致性核對規則.md` 去讀時找不到檔案。

```markdown
.claude/skills/skill-derive-rule/rules/實作一致性核對規則.md
```

# Rule 4 - 新檔名以規範的對象命名

- 強度：建議
- 新開 RuleFile 的檔名用繁中名詞短語寫出規範的對象，例如 `類別設計原則`、`實作一致性核對規則`。
- 不用 Phase、步驟編號命名，因為之後插入 READ 會讓編號推移，檔名就對不上。

## Good Example

- 為 Phase 3 的 CHECK 新開的檔案叫 `實作一致性核對規則.md`，步驟從 3 變成 4 之後檔名依然正確。

```markdown
3. READ `rules/實作一致性核對規則.md`。
4. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
```

## Bad Example

- 同一份檔案依當時的位置命名為 `phase3-step3.md`。插入 READ 之後被把關的 CHECK 變成步驟 4，檔名指向的步驟 3 已經是 READ 本身。

```markdown
3. READ `rules/phase3-step3.md`。
4. CHECK 每完成一個類別，依 phase3-step3 核對其是否符合類別圖定義的職責與介面。
```

# Rule 5 - 新檔名與既有 RuleFile 重名時改為追加

- 強度：必須
- 定出新檔名後，檢查目標 skill 的 `rules/` 是否已有同名檔案。
- 同名代表主題相同，改為追加到該檔案，不加 `-2`、`-new` 之類的後綴另開新檔。

## Good Example

- 為 Phase 1 步驟 4 的 THINK 展開「一個類別只負責一件事」的規則，依主題命名為 `類別設計原則.md`，發現 `rules/` 裡已有同名檔案，改為追加。

```markdown
plan-with-class-diagram/rules/
├── mermaid-classdiagram-語法.md
├── 實作一致性核對規則.md
├── 類別設計原則.md          ← 追加 Rule N+1
└── 類別關係選用原則.md
```

## Bad Example

- 同一條規則撞名後另開 `類別設計原則-2.md`，同一個主題分散在兩個檔案裡，SOP 也得多 READ 一份。

```markdown
plan-with-class-diagram/rules/
├── mermaid-classdiagram-語法.md
├── 實作一致性核對規則.md
├── 類別設計原則.md
├── 類別設計原則-2.md
└── 類別關係選用原則.md
```
