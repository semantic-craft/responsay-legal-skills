# Responsay 法律技能目录（社区只读目录）

这是 [Responsay](https://responsay.com) 的**法律技能公开目录**。App 在「法律技能 → 浏览目录」里读取本仓的 `index.json`，让用户浏览并**一键安装**社区贡献的法律技能（`*.LEGAL_SKILL.md`）。

- **只读**：App 只**读取 / 安装**，不发布、不上传；没有服务器。
- **治理**：安装后默认**关闭**，并标「第三方 · 未审」；启用后未核验的法条 / 案号仍标 `[待核]`，发送范围仍由 App 的隐私门把关。技能内容是第三方提示词，**可能不准确**。
- **curate = PR**：新增 / 更新技能 = 给本仓提 Pull Request（取代云端审核）。

## 目录格式 `index.json`

```json
{
  "schemaVersion": 1,
  "skills": [
    {
      "id": "community.example.clarify.cn",
      "title": "示例 · 清晰表达",
      "description": "一句话说明这个技能做什么。",
      "domain": "academicWriting",
      "tags": ["示例", "学术写作"],
      "author": "你的名字 / handle",
      "version": "1.0",
      "kind": "rewrite",
      "rawURL": "https://raw.githubusercontent.com/semantic-craft/responsay-legal-skills/main/skills/community.example.clarify.cn.LEGAL_SKILL.md"
    }
  ]
}
```

| 字段 | 必填 | 说明 |
|---|---|---|
| `id` | ✓ | 全局唯一，`领域.动作.语言`（如 `practice.case_strategy.cn`）。**不能与 App 内置技能 id 撞**。 |
| `title` | ✓ | 显示名 |
| `rawURL` | ✓ | 该技能 `*.LEGAL_SKILL.md` 的 raw 直链 |
| `description` / `domain` / `tags` / `author` / `version` / `kind` | 选填 | 浏览展示 + 版本比对（`version` 变大 = App 提示「有新版」） |

- `domain` 取值：`litigation` / `contract` / `privacy` / `productCompliance` / `academicWriting`
- `kind` 取值：`rewrite`（改写）/ `generation`（结构化生成）

## 怎么贡献一个技能

1. 在 `skills/` 下加一个 `<id>.LEGAL_SKILL.md`（格式见下）。
2. 在 `index.json` 的 `skills[]` 加一条，`rawURL` 指向上一步那个文件的 raw 直链。
3. 提 PR。合并后，所有 Responsay 用户在「浏览目录」里就能看到并安装。

## `*.LEGAL_SKILL.md` 格式（简）

一个 markdown 文件：**第一个** ` ```legal-skill ` 代码块是严格 JSON 元数据，后面可跟三段说明
（`## Skill Instructions` / `## Reasoning Procedure` / `## Output Constraint`）。

- `kind: rewrite` —— 必须有 `prompt` 字段或 `## Skill Instructions` 段。
- `kind: generation` —— 还必须有非空 `reasoningKernel.mandatoryMapping` 和 `risk.disclaimer`。

完整规范见 Responsay 主仓 `docs/legal-skill-platform/AUTHORING.md`。
