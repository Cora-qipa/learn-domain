# Changelog

All notable changes to this skill are documented here.
The format is based on [Keep a Changelog](https://keepachangelog.com/).

## [2.1.0] — 2026-06-02

**跨模型可用 / Universal Prompt**。让 learn-domain 脱离 Claude 生态,任何模型都能用。同时 v2 核心机制稳定,去掉 -beta 转正。

### Added
- **通用 Prompt 单文件** `dist/learn-domain-prompt.md`:把 SKILL.md + 8 个 reference 揉成一份自包含、连贯的 prompt。复制粘贴进 GPT / Gemini / 豆包 / Kimi / DeepSeek / 文心 等任意模型即可使用,无需 Claude。
- **dist 使用说明** `dist/README.md`:给非 Claude 用户的三步上手 + 各模型注意事项(联网/离线)。
- 主 README 新增"在其他模型上使用"章节(中英双语)。

### Changed
- 通用版的联网核查改为**优雅降级**:能联网的模型自动查证,不能联网的明确声明"建议自查"而非编造。
- 版本号 `2.0.0-beta` → `2.1.0`(v2 概念边界机制经设计验证稳定,正式转正)。

### Notes
- v2.1 后续:真实用户(跨模型)走查反馈 → 沉淀领域混淆风险库。
- v3 计划:跨会话记忆 / 插件市场可订阅。

## [2.0.0-beta] — 2026-06-02

**概念边界优先 / Concept Boundary-First**。基于 v1 真实用户反馈("不够本质,不会主动理清 CPU 和 GPU 的区别")。

### Added
- **概念边界机制**:新增 `references/concept-boundaries.md`——四类概念关系(并列/包含/层级/易混淆兜底)+ 混淆风险判断(高/中/低启发式)+ 边界切分话术库。
- **概念边界网**:阶段1 测绘时显式标注概念对的关系与混淆风险,并用 ASCII 图可视化(四个原子模板 + 防失控三纪律)。

### Changed
- **讲解单元从"单概念"变成"概念对优先"**:遇到高混淆对,强制**前置切边界**(一句话本质区别)→ 再各自展开 → 关卡确认。
- "线-横"(概念对比)从可选配菜**升为必经环节**。
- 失败模式新增一条:"高混淆概念对不主动切边界,等用户问才对比"。

### Notes
- v2.0 正式版:待真实用户走查通过后去掉 -beta。
- v2.1 计划:沉淀领域混淆风险库。
- v3 计划:跨会话记忆 / 插件市场可订阅。

## [1.0.0] — 2026-06-01

首个正式发布版本。First public release.

### Added
- **核心框架**:点·线·面·体四维讲解(在横纵分析法的"线"上扩展)。
- **五阶段工作流**:定终点 → 测绘地形 → 诊断水平 → 点线面体讲解 → 可选结业考。
- **三种学习终点模式**:看懂/会聊、会判断、会上手。
- **7 个 references**:终点模式、测绘地形、用户诊断、教学引擎、叙事写作、防幻觉、结业考(渐进式按需加载)。
- **防幻觉铁律**:三档标注 / 快慢领域联网核查 / 类比标边界 / 宁缺勿编 / 高风险免责。可移植的联网核查(WebSearch/WebFetch 优先,web-access 可选增强)。
- **2 个端到端 examples**:扩散模型(模式①)、可转债(模式②,含高风险处理)。
- **测试套件**:触发矩阵、流程评分量表、评测运行说明。
- 中英双语 README、MIT License。

### Notes
- v2 计划:做成 Claude Code 插件市场可订阅。
