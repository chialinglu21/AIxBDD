# Rule 1 - SOP 不重述 rules/ 已定義的內容

- 強度：必須
- rules/ 已經定義的內容（強度、格式細節、檢查項目），SOP 步驟只寫「依 `<檔名>`」，不在步驟裡重新說明一次。
- 同一個概念只在一個地方定義，SOP 只負責寫出做什麼、依據哪份文件。

## Good Example

- 驗收步驟只寫「對照格式規範」，強度怎麼判斷交給格式規範自己定義，SOP 保持一行一件事。

```markdown
## Phase 3 — 驗收並交付

1. CHECK 逐條對照格式規範，不合就退回 Phase 2 步驟 2 修改。
2. CHECK 拿每條規則去套它的 Good 與 Bad：Good 符合、Bad 違反才算通過，否則退回 Phase 2 步驟 2 重寫範例。
3. REPORT 交出 RuleFile，列出規則清單、每條的強度與出處，請使用者確認。
```

## Bad Example

- 同一個驗收階段，把格式規範裡 `必須`、`建議` 的定義又拆成兩個步驟重寫一次；格式規範一改，SOP 就跟著過時。

```markdown
## Phase 4 — 驗收並交付

1. CHECK 逐條對照格式規範中強度為 `必須` 的規則，不合就退回 Phase 3 步驟 1（標題與描述）或步驟 2（範例）修改。
2. CHECK 逐條對照強度為 `建議` 的規則，不符合的必須有記下的理由；沒有理由就退回 Phase 3 步驟 2 修改。
3. REPORT 交出 RuleFile，列出規則清單與強度、歸納模式下每條的出處、未遵守的 `建議` 規則與理由，請使用者拍板規則清單與強度。
```

# Rule 2 - 文件在第一次用到的那一步才 READ

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
