# Rule 1 - READ 同時列出骨架與範例

- 強度：必須
- 掛上樣板的 READ 步驟，在同一行列出骨架與範例兩個路徑，寫成 `READ <骨架> 與 <範例>`。
- 不只列骨架；只讀骨架時，執行的 AI 看不到填好的成品，佔位符要填成什麼程度只能自己猜。

## Good Example

- 骨架與範例在同一行 READ，執行時兩份都會讀到。

```markdown
1. READ `templates/class-diagram.md` 與 `templates/class-diagram.example.md`。
2. WRITE 依 class-diagram 樣板，複製骨架並參照範例填入內容，存入 `docs/design/<功能名稱>-class-diagram.md`。
```

## Bad Example

- 同一步只 READ 骨架，範例檔雖然存在卻沒人讀，`{{類別 1 職責}}` 該寫一句話還是一整段，執行時沒有依據。

```markdown
1. READ `templates/class-diagram.md`。
2. WRITE 依 class-diagram 樣板，複製骨架並填入內容，存入 `docs/design/<功能名稱>-class-diagram.md`。
```

# Rule 2 - 目標步驟寫明依樣板複製骨架、參照範例

- 強度：必須
- 目標步驟寫成「依 <樣板名> 樣板，複製骨架並參照範例填入內容，存入 <產出路徑>」。
- 產出路徑保留在目標步驟裡，樣板只決定內容長相，不決定存到哪裡。

## Good Example

- WRITE 寫出依哪份樣板、怎麼用骨架與範例，以及存到哪裡。

```markdown
2. WRITE 依 class-diagram 樣板，複製骨架並參照範例填入內容，存入 `docs/design/<功能名稱>-class-diagram.md`。
```

## Bad Example

- 同一步只寫「依樣板」，沒說是哪份樣板，也沒說骨架與範例各怎麼用；產出路徑被刪掉，WRITE 不知道存到哪裡。

```markdown
2. WRITE 依樣板產出類別圖。
```

# Rule 3 - 改寫既有樣板時 SOP 不動

- 強度：建議
- 改寫既有樣板時，骨架與範例的路徑不變，SOP 的 READ 與目標步驟都保持原樣。
- 不另加一行 READ 讀同一份樣板。

## Good Example

- `class-diagram` 樣板多了一段 `## 類別職責`，Phase 2 原本就 READ 它，SOP 一字不改。

```markdown
1. READ `templates/class-diagram.md` 與 `templates/class-diagram.example.md`。
2. WRITE 依 class-diagram 樣板，複製骨架並參照範例填入內容，存入 `docs/design/<功能名稱>-class-diagram.md`。
```

## Bad Example

- 同樣是改寫，又插入一行 READ 讀同一份樣板。多出的步驟沒有作用，WRITE 卻從步驟 2 被推到步驟 3，SOP 裡指向它的「退回步驟 2」也得跟著修。

```markdown
1. READ `templates/class-diagram.md` 與 `templates/class-diagram.example.md`。
2. READ `templates/class-diagram.md` 與 `templates/class-diagram.example.md`。
3. WRITE 依 class-diagram 樣板，複製骨架並參照範例填入內容，存入 `docs/design/<功能名稱>-class-diagram.md`。
```

# Rule 4 - 搬進樣板的格式描述從 RuleFile 刪除

- 強度：必須
- 目標步驟之前已 READ 的 RuleFile 裡，已經搬進樣板的格式描述要刪除，同一個格式只寫在樣板裡。
- 整條規則都被搬走時刪掉整條，後面的規則依序重新編號；只搬走一部分時，只刪那幾行。
- 刪完後 RuleFile 沒有任何規則時，刪掉整份檔案，並刪除 SOP 裡 READ 它的部分。

## Good Example

- `mermaid-classdiagram-語法.md` 的「節點標記」已寫進骨架，所以從 RuleFile 刪掉；「關係符號」仍是畫圖時的判斷依據，保留。

```markdown
# Mermaid 類別圖語法備忘

## 關係符號
- `--|>` 繼承（inheritance）
- `*--` 組合（composition，整體消失、部分也跟著消失）
```

## Bad Example

- 同樣的節點標記在骨架與 RuleFile 各寫一次；之後只改了骨架，RuleFile 還是舊寫法，執行時兩份互相矛盾。

````markdown
# Mermaid 類別圖語法備忘

## 關係符號
- `--|>` 繼承（inheritance）
- `*--` 組合（composition，整體消失、部分也跟著消失）

## 節點標記
```
class ClassName {
  +publicField
  +publicMethod()
}
```
````
