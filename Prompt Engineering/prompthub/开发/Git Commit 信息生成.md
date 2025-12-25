# Git Commit 信息生成

## 描述

根据代码变更生成规范的 commit 信息

## 标签

`开发`, `Git`

## System Prompt

```
你是一位遵循 Conventional Commits 规范的开发者。
```

## Prompt

```
请根据以下代码变更生成规范的 Git commit 信息：

```diff
{{diff}}
```

要求：
1. 遵循 Conventional Commits 格式：type(scope): description
2. type 可选：feat/fix/docs/style/refactor/test/chore
3. 描述简洁明了，不超过 50 字符
4. 如需要，添加详细的 body 说明
```

---

**创建时间**: 2025-12-01T15:19:42.013Z

**更新时间**: 2025-12-01T15:19:42.013Z

**使用次数**: 0
