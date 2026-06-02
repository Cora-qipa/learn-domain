# learn-domain

> **快速入门一个陌生的专业领域** — 一个 Claude Code / Claude Agent Skill
> **Get up to speed in an unfamiliar field, fast** — a skill for Claude Code / Claude Agent

中文 · [English below](#english)

---

## 这是什么

遇到本专业之外、看不懂的内容(行业报告、技术文章、论文、监管文件……),`learn-domain` 把 Claude 变成一个**会因材施教的领域家教**:不是把领域百科倒给你,而是砍到只剩骨架、排好学习顺序、边讲边校准,直到你能**独立读懂**这个领域。

它的方法骨架借鉴了[数字生命卡兹克的"横纵分析法"](https://mp.weixin.qq.com/),但把"穷尽式研究报告"改造成了"自适应教学引擎"。

## 核心设计

**点 · 线 · 面 · 体** 四维讲解框架(横纵分析法是中间那根"线",上下各长一层):

| 维度 | 讲什么 |
|---|---|
| **点** | 概念内核:一句话本质 + 一个好类比 |
| **线** | 横纵法:纵(什么问题逼出了它,讲成故事)+ 横(跟相邻概念划边界) |
| **面** | 领域全景:概念依赖图 + 学习顺序 + 80/20 最小集 |
| **体** | 怎么上手:最小动作 + 社区 + 在吵什么 + 新手坑 |

**五阶段工作流**:定终点(锁边界)→ 测绘地形(先地图)→ 诊断水平(自适应 2–4 题)→ 点线面体讲解(关卡制)→ 可选结业考(用真实文章验证)。

> **v2 新特性 · 概念边界优先**:初学者最大的困惑不是"A 是什么",而是"A 和 B 到底差在哪"。v2 把"划清概念边界"从可选变成主菜——测绘时显式标出易混概念对的关系(并列/包含/层级/易混)和混淆风险并画成边界网;讲解时遇到高混淆对**主动前置切边界**(一句话本质区别),不等你问。

**三种学习终点**,进来先选一个,它决定讲多深、怎么考:
- ① **看懂/会聊** — 读懂内容、跟人聊不露怯
- ② **会判断** — 做选型/评估/决策
- ③ **会上手** — 真动手写第一行

## 安装

```bash
git clone <repo-url> ~/.claude/skills/learn-domain
```

(用户级 skill 装在 `~/.claude/skills/`;也可装到项目级 `.claude/skills/`。)

## 使用

在 Claude Code 里:

```
/learn-domain 扩散模型
```

或者直接说"带我入门期权""这篇讲 RAG 的文章我看不懂"——skill 会自动触发。

然后跟着走:它会先问你学了想干嘛(锁定终点),给你一张领域地图,问几个问题摸清你的水平,再一个概念一个概念地讲,最后(可选)丢给你一篇真实文章验证你是否真入门。

完整运行示范见 [`examples/`](examples/)。

## 在其他模型上使用(GPT / Gemini / 国产模型)

Skill 机制是 Claude 专属的,但 learn-domain 的方法论本质是一段结构化指令,**任何模型都能用**。我们提供了一份自包含的通用 Prompt:

👉 **[`dist/learn-domain-prompt.md`](dist/learn-domain-prompt.md)** — 复制里面的内容,粘贴进 GPT / Gemini / 豆包 / Kimi / DeepSeek / 文心 等任意模型的对话框,然后说"我想入门 XX"即可。

详细说明见 [`dist/README.md`](dist/README.md)。

## 仓库结构

```
SKILL.md              主文件:信条 + 框架 + 五阶段骨架(按需加载 references)
references/           7 个细节文件,各阶段按需加载
examples/             2 个端到端走查样例(也是回归基线)
tests/                触发矩阵 + 评分量表 + 怎么跑
```

## 设计取舍(为什么这么做)

- **输入是领域名,不是文章**。但这砍掉了文章原本扛的两根支柱——范围边界和防幻觉锚。前者用"学习终点"顶替,后者用一套[防幻觉铁律](references/anti-hallucination.md)顶替(三档标注 / 快变领域联网核查 / 类比标边界 / 宁缺勿编 / 高风险免责)。
- **被砍掉的文章没消失**,它从"输入"挪到了"输出"——变成可选的结业考。读懂一篇真实文章 = 真入门。
- **叙事张力刻意保留**。快≠干,纯骨架用户读不下去。每个概念的来历讲成 mini 故事,但服务于"让概念立住",不为凑字数。

---

<a name="english"></a>
## English

### What it is

When you hit content outside your field that you just can't parse (industry reports, technical articles, papers, regulatory docs…), `learn-domain` turns Claude into an **adaptive tutor**: instead of dumping an encyclopedia, it strips the field down to its skeleton, orders the concepts by dependency, and calibrates as it goes — until you can read the field **on your own**.

The method skeleton adapts the "vertical-horizontal analysis" framework, reworked from an exhaustive *research report* into an adaptive *teaching engine*.

### Core design

**Point · Line · Plane · Solid** — a 4-dimension teaching frame (the vertical-horizontal method is the middle "Line"):

| Dim | What it covers |
|---|---|
| **Point** | Concept core: one-sentence essence + one good analogy |
| **Line** | Vertical (what problem forced it into existence, told as a story) + Horizontal (boundaries vs adjacent concepts) |
| **Plane** | Field map: dependency graph + learning order + 80/20 minimal set |
| **Solid** | Getting hands-on: minimal action + community + live debates + beginner traps |

**5-stage flow**: lock the endpoint (set the boundary) → map the terrain → diagnose the user (adaptive 2–4 questions) → teach concept-by-concept (checkpointed) → optional graduation test (verify with a real article).

> **v2 · Concept Boundary-First**: a beginner's biggest confusion isn't "what is A" but "how is A different from B". v2 promotes boundary-drawing from optional to default — the terrain map explicitly tags confusable concept pairs by relation (parallel / containment / hierarchy / confusable) and confusion-risk, and during teaching it **proactively cuts the boundary first** (one-sentence essential difference) for high-risk pairs, without waiting to be asked.

**3 learning endpoints**, picked up front — they decide depth and how you're tested:
- ① **Comprehend/Converse** — read the content, hold a conversation
- ② **Judge** — make a selection/evaluation/decision
- ③ **Hands-on** — actually write your first line

### Install

```bash
git clone <repo-url> ~/.claude/skills/learn-domain
```

### Use

In Claude Code:

```
/learn-domain diffusion-models
```

Or just say "get me started on options trading" / "I can't follow this article on RAG" — the skill auto-triggers. See [`examples/`](examples/) for full runs.

## Use on other models (GPT / Gemini / non-Claude)

The Skill mechanism is Claude-only, but learn-domain's method is just a structured prompt — **any model can run it**. We ship a self-contained universal prompt:

👉 **[`dist/learn-domain-prompt.md`](dist/learn-domain-prompt.md)** — copy its contents, paste into any model's chat box (GPT / Gemini / domestic models), then say "I want to learn X". See [`dist/README.md`](dist/README.md) for details.

## License

MIT — see [LICENSE](LICENSE).
