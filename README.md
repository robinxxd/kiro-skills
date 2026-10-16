# kiro-skills

一组 Kiro AI 技能（Agent Skills），覆盖研发质量链路的多个评审 / 拆分 / 写作环节。每个子目录是一个独立技能，包含 `SKILL.md`（Kiro 标准格式：YAML frontmatter + 正文）。

## 技能清单

| 技能 | 用途 | 关键词 |
|---|---|---|
| [`code-review`](./code-review) | 对 Spark SQL / Python 数据任务做分级代码检查，输出 P0–P3 问题清单；重点排查能跑通但结果错、或静默失败的 ETL 陷阱（NOT IN 的 NULL 陷阱、窗口函数与 where 的执行顺序、主键稳定性、清理脚本无差别删除等）。 | 代码评审, Spark SQL, Python, ETL, 问题分级 |
| [`dba-schema-review`](./dba-schema-review) | 建表 / 改数据模型的变更评审清单：schema 划分、跨域引用、枚举与时间列约定、软删、约束保不变量、索引对齐查询、迁移规范，以及两条真实脑裂事故防线（同仓建表查重、跨仓 schema 所有权）。 | 数据库, schema, DDL, 建表, 迁移 |
| [`test-case-generator`](./test-case-generator) | 从需求 / 设计稿生成结构化测试用例：P0–P3 优先级、断言分层（错误码 / 业务语义 / 集成副作用）、权限逐角色断言、禁止恒真空断言、冗余用例合并。 | 测试用例, 优先级, 断言, 验收标准 |
| [`ui-design-review`](./ui-design-review) | UI 设计评审：对照需求查覆盖度、逐像素对比设计稿与实现、P0–P3 分级、三层面走查（本能 / 行为 / 反思层）、响应式与状态变体检查。 | UI 评审, 设计走查, 视觉还原 |
| [`user-story-splitting`](./user-story-splitting) | 把需求 / PRD 拆成可排期的用户故事：角色-目标-价值、故事点数（Fibonacci 相对估算）、可测验收标准、非功能与护栏验收、依赖顺序、FR↔US 覆盖检查。 | 用户故事, story point, 需求拆分 |
| [`writing-style`](./writing-style) | 中文文案规约：中英混排半角标点加空格、朴素用词、避免 AI 腔、面向同事说话、ISO 日期。写给人看的中文文字都套用。 | 文风, 中文写作, 文案, 标点 |
| [`dw-model-review`](./dw-model-review) | 数仓模型 / 维度建模评审：表粒度与命名、维度一致性、缓慢变化维（SCD）、指标口径、分区分桶、血缘与复用、空值 / 退化维度处理等。 | 数仓, 维度建模, 数据模型, 评审, 指标口径 |

## 目录结构

```
kiro-skills/
├── README.md
├── code-review/
│   └── SKILL.md
├── dba-schema-review/
│   └── SKILL.md
├── test-case-generator/
│   └── SKILL.md
├── ui-design-review/
│   └── SKILL.md
├── user-story-splitting/
│   └── SKILL.md
├── writing-style/
│   └── SKILL.md
└── dw-model-review/
    └── SKILL.md
```

## 如何使用

把需要的技能目录复制到你的 Kiro（或兼容 Agent Skills 规范的工具）的 `skills/` 目录下即可，例如：

```bash
cp -r code-review ~/.kiro/skills/
```

每个 `SKILL.md` 的 frontmatter 里含 `name` / `description` / `version` / `keywords`，便于检索与触发。

---

> 本仓库由 WorkBuddy 从本地 `~/.kiro/skills` 同步上传，仅作备份与分享用途。
