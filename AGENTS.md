# 法律技能目录维护

本仓是 App 消费的公开技能目录；应用实现不在此仓。格式与治理边界见 [README](README.md)。

- 目录索引：[index.json](index.json)；技能正文：[skills](skills/)。新增条目须让索引 ID、文件名、版本和 rawURL 对应，保留 `schemaVersion` 契约。
- 技能文件中的第一个 `legal-skill` 代码块是 JSON 元数据；按 README 区分 rewrite 和 generation 的必需字段。
- 目前没有统一的应用验收套件。检查 JSON 可解析、引用文件存在，并使用 [现有源码检查](scripts/check-secrets.sh)；App 中下载、默认关闭和启用后的行为属于调用方验收。
- 内容是第三方提示词，法律事实仍需核实；不要把新增目录项当成已审定的法律依据。
实现、评审或验收前读相关 [lessons](lessons.md)；出现可复用的纠正或漏验时更新原条目。
