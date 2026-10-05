# Rule 1 - 追加到既有 RuleFile 時不另加 READ

- 強度：建議
- 新規則追加到目標步驟前方已經 READ 的 RuleFile 時，SOP 不新增 READ 步驟。
- 該 READ 步驟與被把關步驟的文字都保持原樣，只有 RuleFile 的內容變多。

## Good Example

- `實作一致性核對規則.md` 追加一條新規則，Phase 3 原本就會 READ 它，SOP 一字不改。

```markdown
3. READ `rules/實作一致性核對規則.md`。
4. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
```

## Bad Example

- 同樣是追加，卻又插入一行 READ 讀同一份檔案。多出的步驟沒有作用，CHECK 卻從步驟 4 被推到步驟 5，後面的步驟編號與退回引用也得跟著修。

```markdown
3. READ `rules/實作一致性核對規則.md`。
4. READ `rules/實作一致性核對規則.md`。
5. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
```

# Rule 2 - 新的 READ 緊貼在被把關步驟之前

- 強度：必須
- 新 RuleFile 的 READ 步驟插在被把關步驟的正前方，中間不夾其他步驟。
- 不把 READ 移到 Phase 開頭或 Phase 1 預先讀入。

## Good Example

- 要把關的是 Phase 3 的 CHECK，READ 就插在 CHECK 正前方，排序與實作時都不必載入核對規則。

```markdown
## Phase 3 — 依類別圖實作程式

1. THINK 依類別圖的依賴關係，排出開發順序（被依賴者優先於依賴者）。
2. WRITE 依排定順序逐一將每個類別／模組實作到對應的程式碼檔案。
3. READ `rules/實作一致性核對規則.md`。
4. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
```

## Bad Example

- 同一份核對規則被放到 Phase 3 開頭，排序與實作兩步都還用不到，規則提早載入、離被把關的 CHECK 隔了兩步。

```markdown
## Phase 3 — 依類別圖實作程式

1. READ `rules/實作一致性核對規則.md`。
2. THINK 依類別圖的依賴關係，排出開發順序（被依賴者優先於依賴者）。
3. WRITE 依排定順序逐一將每個類別／模組實作到對應的程式碼檔案。
4. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
```

# Rule 3 - 前一步已是 READ 就併入同一行

- 強度：建議
- 被把關步驟的正前方已經是 READ 時，把新 RuleFile 併進那一行，寫成 `READ A 與 B`。
- 不另開一行 READ，步驟編號維持不變。

## Good Example

- Phase 2 步驟 1 原本就 READ 語法規範，新的關係選用原則併進同一行，後面的步驟編號與退回引用都不用動。

```markdown
1. READ `rules/mermaid-classdiagram-語法.md` 與 `rules/類別關係選用原則.md`。
2. WRITE 依語法規範與關係選用原則，將 Phase 1 得出的類別組成畫成 mermaid classDiagram，存入 `docs/design/<功能名稱>-class-diagram.md`。
```

## Bad Example

- 同樣兩份檔案拆成兩行 READ，WRITE 被推到步驟 3，步驟 4 底下「退回步驟 2」的引用也跟著要改。

```markdown
1. READ `rules/mermaid-classdiagram-語法.md`。
2. READ `rules/類別關係選用原則.md`。
3. WRITE 依語法規範與關係選用原則，將 Phase 1 得出的類別組成畫成 mermaid classDiagram，存入 `docs/design/<功能名稱>-class-diagram.md`。
```

# Rule 4 - 被把關步驟寫明「依 <規則名>」

- 強度：必須
- 被把關步驟的描述裡加上「依 <規則名>」，把動作和剛 READ 的 RuleFile 綁在一起。
- `<規則名>` 用 RuleFile 檔名或其簡稱，只要能明確對應到剛 READ 的檔案；併入多份時用「與」連接。

## Good Example

- CHECK 寫明「依實作一致性核對規則」，執行時知道要拿哪份規則來核對。

```markdown
3. READ `rules/實作一致性核對規則.md`。
4. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
```

## Bad Example

- READ 有插進去，CHECK 卻沿用原文，看不出讀進來的規則要用在這一步。

```markdown
3. READ `rules/實作一致性核對規則.md`。
4. CHECK 每完成一個類別，核對其是否符合類別圖定義的職責與介面。
```

# Rule 5 - 插入 READ 後同一 Phase 的步驟重新編號

- 強度：必須
- 新插入的 READ 取得被把關步驟原本的編號，被把關步驟與其後的步驟依序 +1。
- 編號從 1 連續遞增，不跳號、不重複。

## Good Example

- READ 取得 3，CHECK 從 3 變 4，REPORT 從 4 變 5。

```markdown
2. WRITE 依排定順序逐一將每個類別／模組實作到對應的程式碼檔案。
3. READ `rules/實作一致性核對規則.md`。
4. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
5. REPORT 交出實作結果，列出各類別對應的程式碼檔案與開發順序。
```

## Bad Example

- 插入 READ 後沒有重新編號，出現兩個步驟 3，REPORT 仍是 4。

```markdown
2. WRITE 依排定順序逐一將每個類別／模組實作到對應的程式碼檔案。
3. READ `rules/實作一致性核對規則.md`。
3. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
4. REPORT 交出實作結果，列出各類別對應的程式碼檔案與開發順序。
```

# Rule 6 - 退回引用依新編號修正

- 強度：必須
- 重新編號後，逐一檢查整份 SOP 裡「退回步驟 N」「退回 Phase M 步驟 N」的引用。
- 指向插入點之後的步驟，N 跟著 +1；指向插入點之前或其他 Phase 未變動的步驟，保持原樣。

## Good Example

- 插入點在 Phase 3 步驟 3；「退回步驟 2」指向插入點之前的 WRITE，「退回 Phase 2 步驟 2」指向其他 Phase，兩者都保持原樣。

```markdown
3. READ `rules/實作一致性核對規則.md`。
4. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
   - 若是實作有誤 → 退回步驟 2 修正該類別，完成後再次 CHECK。
   - 若是類別圖本身需要變更 → 退回 Phase 2 步驟 2 修圖，重新取得核准後再繼續。
```

## Bad Example

- 把所有退回引用一律 +1，「退回步驟 3」現在指向 READ 而不是 WRITE，實作有誤時會退回去重讀規則而不是修程式。

```markdown
3. READ `rules/實作一致性核對規則.md`。
4. CHECK 每完成一個類別，依實作一致性核對規則核對其是否符合類別圖定義的職責與介面。
   - 若是實作有誤 → 退回步驟 3 修正該類別，完成後再次 CHECK。
   - 若是類別圖本身需要變更 → 退回 Phase 2 步驟 3 修圖，重新取得核准後再繼續。
```

# Rule 7 - 被把關步驟只留動作、依據與產出

- 強度：必須
- 掛上 RuleFile 後，被把關步驟只寫「動詞 + 依 <規則名> + 產出什麼」。
- 已經萃取進 RuleFile 的判準子句，要從被把關步驟刪除；決定流程走向的子句（退回步驟 N、ASK）保留。

## Good Example

- 主題比對與兩個路徑分支已寫進 `RuleFile-歸屬判斷.md`，被把關步驟只剩動作、依據與產出。

```markdown
5. READ `rules/RuleFile-歸屬判斷.md`。
6. THINK 依 RuleFile 歸屬判斷，定出要追加或新開的 RuleFile 路徑。不必詢問使用者。
```

## Bad Example

- 同一步掛上 RuleFile 後，判準子句仍留在 SOP 上，同一套判準在 SOP 與 RuleFile 各寫一次，或只寫在 SOP 上。

```markdown
5. READ `rules/RuleFile-歸屬判斷.md`。
6. THINK 依 RuleFile 歸屬判斷，比對使用者口述的規則主題與目標步驟已 READ 的 RuleFile 主題，定出 RuleFile 路徑。不必詢問使用者。
   - 若主題相同 → 追加到該 RuleFile。
   - 若主題不同或沒有既有 RuleFile → 新開 `<目標 skill>/rules/<主題>.md`。
```
