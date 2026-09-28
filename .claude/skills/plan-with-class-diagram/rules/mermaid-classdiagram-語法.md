# Mermaid 類別圖語法備忘

## 關係符號
- `--|>` 繼承（inheritance）
- `*--` 組合（composition，整體消失、部分也跟著消失）
- `o--` 聚合（aggregation，整體消失、部分仍可獨立存在）
- `-->` 關聯（association）
- `..>` 依賴（dependency）
- `..|>` 實作介面（interface realization）

## 節點標記
```
class ClassName {
  +publicField
  -privateField
  +publicMethod()
  -privateMethod()
}
```

## 非物件導向專案的比擬方式
- module → 視為一個 class 節點，對外的 exported functions 列為 `+method()`
- interface／type → 節點頂端加 `<<interface>>` 或 `<<type>>` 標記
- struct（如 Go）→ 視為 class 節點，欄位列為 `+field`
</content>
