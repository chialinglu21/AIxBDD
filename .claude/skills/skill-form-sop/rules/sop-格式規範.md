# Rule 1 - `# SOP` 之下只放 `## Phase N — <標題>`

- 強度：必須
- `# SOP` 的下一層只有 Phase 標題，格式固定為 `## Phase N — <標題>`，連接符號用 `—`。
- `N` 從 1 開始連續編號，不跳號、不重複。

## Good Example

- 三個 Phase 都用同一個格式，編號從 1 連續遞增，「退回 Phase 2 步驟 2」可以直接對應到位置。

```markdown
# SOP

## Phase 1 — 收斂規則清單

## Phase 2 — 寫出 RuleFile

## Phase 3 — 驗收並交付
```

## Bad Example

- 同樣三段，第二段少了 Phase 編號，第三段跳到 4 還降成 `###`。「退回 Phase 2 步驟 2」找不到對象。

```markdown
# SOP

## Phase 1 — 收斂規則清單

## 寫出 RuleFile

### Phase 4：驗收並交付
```

# Rule 2 - Phase 標題用 5–10 字的動賓短語寫出這段做完的事

- 強度：建議
- `<標題>` 寫成「動詞 + 受詞」，說出這個 Phase 做完時完成了什麼。
- 長度 5–10 字，不寫成名詞或整句說明。

## Good Example

- 每個標題都是動賓短語，只看標題就知道這段要完成什麼。

```markdown
## Phase 1 — 收斂規則清單

## Phase 2 — 寫出 RuleFile

## Phase 3 — 驗收並交付
```

## Bad Example

- 同樣三段，第一段只有名詞，看不出要做什麼；第二段把步驟內容整句寫進標題；第三段沒有受詞，不知道驗收什麼。

```markdown
## Phase 1 — 規則

## Phase 2 — 讀取格式規範之後依照格式規範把規則清單寫進 RuleFile 檔案

## Phase 3 — 驗收
```

# Rule 3 - 全流程 2–5 個 Phase，每個 Phase 2–7 個步驟

- 強度：建議
- 整份 SOP 切成 2–5 個 Phase。
- 每個 Phase 有 2–7 個編號步驟。

## Good Example

- `skill-derive-rule` 切成 3 個 Phase，每段的步驟數都在 2–7 之間，一眼就能看出流程分幾段。

```markdown
## Phase 1 — 定位目標步驟        （6 步）
## Phase 2 — 寫出 RuleFile       （2 步）
## Phase 3 — 把規則掛上 SOP      （5 步）
```

## Bad Example

- 同樣的 13 個步驟全塞進一個 Phase，看不出哪裡是里程碑，退回時也只能說「退回步驟 9」。

```markdown
## Phase 1 — 展開步驟規則        （13 步）
```

# Rule 4 - 每個 Phase 以一行 `**產出**：` 收尾

- 強度：必須
- 每個 Phase 的最後一行固定是 `**產出**：<一句話>`，寫出這段做完後手上多了什麼。
- 答不出產出的 Phase，併入相鄰 Phase，這是切 Phase 的唯一判準。

## Good Example

- 讀規範與寫 SOP 在同一個 Phase，做完時手上多了 SOP 草稿，產出行寫得出來。

```markdown
## Phase 2 — 寫出 SOP

1. READ `rules/sop-格式規範.md` 與 `rules/sop-撰寫原則.md`。
2. THINK 從產出回推里程碑，一個里程碑一個 Phase。
3. WRITE 依格式規範與撰寫原則，寫出 Phase 標題、產出行與步驟。

**產出**：SOP 草稿。
```

## Bad Example

- 同樣的步驟把 READ 獨立成一個 Phase。讀完規範手上沒有新東西，答不出產出，所以沒有產出行；這段應該併入下一個 Phase。

```markdown
## Phase 2 — 讀取規範

1. READ `rules/sop-格式規範.md` 與 `rules/sop-撰寫原則.md`。

## Phase 3 — 寫出 SOP

1. THINK 從產出回推里程碑，一個里程碑一個 Phase。
2. WRITE 依格式規範與撰寫原則，寫出 Phase 標題、產出行與步驟。

**產出**：SOP 草稿。
```

# Rule 5 - 步驟一步一行，開頭一個動詞 token

- 強度：必須
- 每個編號步驟只佔一行，子句另外縮排在下方。
- 一行的開頭是一個動詞 token（見 Rule 6），token 之後接繁中祈使描述。

## Good Example

- 每一步都是一行、一個動詞 token 開頭，後面直接寫要做的事。

```markdown
1. CHECK 逐條對照格式規範，不合就退回 Phase 2 步驟 2 修改。
2. CHECK 拿每條規則去套它的 Good 與 Bad：Good 符合、Bad 違反才算通過，否則退回 Phase 2 步驟 2 重寫範例。
3. REPORT 交出 RuleFile，列出規則清單、每條的強度、違反時的結果與出處，請使用者確認。
```

## Bad Example

- 同樣的驗收，第一步沒有動詞 token；第二步塞了兩個 token；第三步換行接著寫，變成兩行。

```markdown
1. 逐條對照格式規範，不合就退回 Phase 2 步驟 2 修改。
2. CHECK／REPORT 拿每條規則去套它的 Good 與 Bad，通過後交給使用者。
3. REPORT 交出 RuleFile。
   列出規則清單、每條的強度、違反時的結果與出處，請使用者確認。
```

# Rule 6 - 動詞只用動詞表的七個，並符合判準

- 強度：必須
- 動詞是封閉集，只有下表七個，不得自創。
- 每一步都要符合該動詞的判準；對不上就換動詞，或把該步拆成兩步。

| 動詞 | 這一步在做什麼 | 判準 |
|---|---|---|
| READ | 讀取既有資料：檔案、issue、指令輸出 | 不改變任何狀態 |
| THINK | 推理、判斷、擴展思考 | 不碰檔案、不呼叫工具；產出是判斷不是檔案 |
| ASK | 停下來問使用者 | 會阻塞；必須寫明需要什麼答案才能往下 |
| DELEGATE | 交給 script、subagent 或其他 skill | 必須寫出被委派對象的名字 |
| WRITE | 產生或修改檔案、留言、commit | 必須寫出寫到哪裡 |
| CHECK | 驗收前面的產出 | 有明確 pass／fail；fail 要寫明退回哪一步 |
| REPORT | 對使用者總結產出與待確認事項 | 不改變任何狀態 |

## Good Example

- DELEGATE 寫出被委派的 skill 名稱；CHECK 寫出通過條件，也寫出不合時退回哪一步。

```markdown
1. DELEGATE `/skill-form-rule`，交付目標 skill、目標步驟、Phase 1 的規則清單與 RuleFile 路徑。
2. CHECK RuleFile 寫在 Phase 1 定出的路徑；追加時既有規則的內容與編號未被改動。不合就退回步驟 1。
```

## Bad Example

- 同樣兩步，第一步用了表外的 `RUN`，也沒寫交給誰；第二步的 CHECK 沒有 pass／fail 條件，不合時也不知道退回哪裡。

```markdown
1. RUN 交給別的 skill 把 RuleFile 寫出來。
2. CHECK 看看 RuleFile 有沒有問題。
```

# Rule 7 - 一個步驟只做一件事

- 強度：必須
- 一個步驟只有一個動作；同一步要做兩件事，就拆成兩步。

## Good Example

- 讀強度判準與定出強度拆成兩步，各自的動詞都符合判準，之後也能單獨退回其中一步。

```markdown
3. READ `rules/強度判準.md`。
4. THINK 依強度判準，為每條規則定出強度。
```

## Bad Example

- 同樣兩件事擠在一個 READ 裡，READ 卻做了 THINK 的判斷；退回時也分不出要重讀還是重判。

```markdown
3. READ `rules/強度判準.md`，並依強度判準為每條規則定出強度。
```

# Rule 8 - 例外與分支寫成縮排子句

- 強度：建議
- 例外與分支寫在該步驟下方，格式為 `- 若 <條件> → <動作>`。
- 不為了分支另開 Phase。

## Good Example

- 規則衝突是萃取時才會遇到的例外，寫成步驟 4 底下的子句，沒有衝突時直接往下走。

```markdown
4. THINK 依規則萃取判準，從使用者口述與目標步驟抽出需要新增或改寫的規則。
   - 若與既有規則衝突 → ASK 使用者採用哪一方，附上衝突分析，取得答案才往下。
```

## Bad Example

- 同一個衝突分支另開一個 Phase，沒有衝突時整段要跳過，讀者還得自己判斷什麼時候進這個 Phase。

```markdown
4. THINK 依規則萃取判準，從使用者口述與目標步驟抽出需要新增或改寫的規則。

## Phase 2 — 處理規則衝突

1. ASK 使用者採用哪一方，附上衝突分析，取得答案才往下。
```

# Rule 9 - 會阻塞流程的拍板點一律用 ASK

- 強度：必須
- 需要使用者拍板才能往下的點，寫成獨立的 ASK 步驟。
- 不把拍板藏在 REPORT 或其他動詞的描述裡。

## Good Example

- 先 REPORT 展示類別圖，再用 ASK 停下來等核准，沒拿到核准不會進 Phase 3。

```markdown
3. REPORT 向使用者展示類別圖與各類別的職責、彼此關係。
4. ASK 使用者是否核准此類別圖，取得核准才進入 Phase 3。
```

## Bad Example

- 同樣的核准藏在 REPORT 裡；REPORT 不會阻塞，執行時展示完就直接進 Phase 3 開始實作。

```markdown
3. REPORT 向使用者展示類別圖與各類別的職責、彼此關係，請使用者核准後進入 Phase 3。
```

# Rule 10 - 刻意不問人的步驟寫明「不必詢問使用者」

- 強度：建議
- 看起來需要使用者決定、但刻意由 AI 自行決定的步驟，在描述最後寫上「不必詢問使用者」。

## Good Example

- 路徑由 AI 依固定格式決定，寫明不必詢問，執行時不會停下來問路徑。

```markdown
6. THINK 定出 RuleFile 路徑 `<目標 skill>/rules/<檔名>.md`。不必詢問使用者。
```

## Bad Example

- 同一步沒寫明，執行時可能停下來問使用者檔案要放哪，多一輪來回。

```markdown
6. THINK 定出 RuleFile 路徑 `<目標 skill>/rules/<檔名>.md`。
```
