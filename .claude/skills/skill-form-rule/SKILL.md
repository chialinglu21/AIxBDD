---
name: skill-form-rule
description: 撰寫 skill 之 rules/ 底下 RuleFile 類型的檔案時，必須使用此 skill。
---

# SOP

## Phase 1 — 收斂規則清單

1. READ 目標 skill 的 SKILL.md 與相關檔案，找出哪一步會 READ 這份 RuleFile、要它規範什麼。
2. THINK 從使用者口述與上一步讀到的檔案抽出規則，一條只規範一件事，記下每條的出處。
   - 若口述與檔案內容衝突 → 以口述為準。
3. READ `rules/強度判準.md`。
4. THINK 依強度判準，為每條規則定出強度。
5. THINK 依目標 skill 使用規則的順序排列，決定編號。
6. THINK 定出 RuleFile 路徑 `<目標 skill>/rules/<檔名>.md`。不必詢問使用者。

**產出**：RuleFile 路徑，以及含編號、Rule name、強度、出處的規則清單。

## Phase 2 — 寫出 RuleFile

1. READ `rules/RuleFile-格式規範.md`，這是 RuleFile 唯一的格式規範，不參照其他文件的格式。
2. WRITE 依格式規範，將規則清單寫入 Phase 1 定出的 RuleFile 路徑。
   - 若規則出自目標 skill 的檔案 → 範例優先取用其中的真實片段，不自行編造。

**產出**：RuleFile 草稿。

## Phase 3 — 驗收並交付

1. CHECK 逐條對照格式規範，不合就退回 Phase 2 步驟 2 修改。
2. CHECK 拿每條規則去套它的 Good 與 Bad：Good 符合、Bad 違反才算通過，否則退回 Phase 2 步驟 2 重寫範例。
3. REPORT 交出 RuleFile，列出規則清單、每條的強度、違反時的結果與出處，請使用者確認。

**產出**：RuleFile，以及使用者對規則清單、強度與出處的確認。
