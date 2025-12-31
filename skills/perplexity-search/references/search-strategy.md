# Perplexity 搜索策略与工具指南

本指南详细说明了 Perplexity 搜索工具的模式、来源选项以及选择策略，帮助你根据不同需求选择最合适的工具配置。

## 可用工具概览

| 工具 | 作用 | 特点 |
|------|------|------|
| `list_models` | 获取所有可用搜索模式和模型列表 | 了解当前支持的模型和模式选项 |
| `search` | 快速搜索 | 速度快，适合实时信息、简单事实查询和一般性问题 |
| `research` | 深度研究 | 多步推理，适合复杂分析、学术研究和深度调研报告 |

## `search` 工具详解

### 搜索模式 (Mode)

| 模式 | 模型 | 特点 | 成本 |
|------|------|------|------|
| `auto` | turbo | 快速模式，不消耗额度，适合一般性查询 | 免费 |
| `pro` | 可选择 | 专业模式，提供更准确、深入的结果，适合需要高质量信息的场景 | 付费 |

### 搜索来源 (Sources)

| 来源 | 说明 | 适用场景 |
|------|------|----------|
| `web` | 网页搜索 | 一般性查询（默认），获取广泛的网络信息 |
| `scholar` | 学术论文 | 学术研究、查找文献、获取引用 |
| `social` | 社交媒体 | 实时动态、舆论分析、突发新闻 |

### 使用示例

**1. 快速免费搜索 (实时信息)**
```yaml
search:
  query: "今天的天气"
  mode: "auto"
```

**2. 专业网页搜索 (技术文档/深度信息)**
```yaml
search:
  query: "CRISPR 基因编辑的最新进展"
  mode: "pro"
  sources: ["web"]
  language: "zh-CN"
```

**3. 学术文献搜索 (科研)**
```yaml
search:
  query: "CAR-T 细胞疗法最新临床试验结果"
  mode: "pro"
  sources: ["scholar"]
  language: "zh-CN"
```

## `research` 工具详解

### 研究模式 (Mode)

| 模式 | 特点 | 耗时 | 适用场景 |
|------|------|------|----------|
| `reasoning` | 多步推理分析 | 中等 | 需要逻辑推演、方案对比、因果分析的复杂问题 |
| `deep research` | 最全面深度研究 | 较长 | 生成综合调研报告、行业分析、全面综述 |

### reasoning 模式可用模型

*注：模型列表可能会更新，请以 `list_models` 返回结果为准。*

| 模型 | 提供商 | 特点 |
|------|--------|------|
| `gemini-3.0-pro` | Google | 默认推荐，平衡速度与质量 |
| `gpt-5.2-thinking` | OpenAI | OpenAI 思考模型，擅长逻辑推理 |
| `claude-4.5-sonnet-thinking` | Anthropic | Claude 推理模型，擅长复杂任务 |
| `kimi-k2-thinking` | Moonshot | Kimi 思考模型 |
| `grok-4.1-reasoning` | xAI | Grok 推理模型 |

### 使用示例

**1. 推理分析 (方案对比/复杂逻辑)**
```yaml
research:
  query: "分析 AlphaFold3 相对于 AlphaFold2 的改进"
  mode: "reasoning"
  model: "gemini-3.0-pro"
  language: "zh-CN"
```

**2. 深度研究 (综述/报告)**
```yaml
research:
  query: "单细胞 RNA 测序技术的发展趋势和应用前景"
  mode: "deep research"
  sources: ["scholar"]
  language: "zh-CN"
```

## 决策树：如何选择工具

```
你的问题性质？
├─ 需要深入分析、多步推理或生成报告 → 使用 research 工具
│   ├─ 需要最全面的综合调研报告 → mode: "deep research"
│   └─ 需要逻辑分析、方案对比 → mode: "reasoning"
└─ 主要是信息获取、事实查询或快速了解 → 使用 search 工具
    ├─ 简单事实查询、对准确度要求一般 → mode: "auto"（免费）
    └─ 需要高准确度、专业信息或特定来源 → mode: "pro"
        ├─ 查一般网页 → sources: ["web"]
        ├─ 查学术论文 → sources: ["scholar"]
        └─ 查社交动态 → sources: ["social"]
```

## 按场景推荐配置

| 场景 | 推荐工具 | 模式 | 来源 |
|------|----------|------|------|
| 快速获取实时信息 | `search` | `auto` | `web` |
| 一般性问题查询 | `search` | `pro` | `web` |
| 学术文献搜索 | `search` | `pro` | `scholar` |
| 社交媒体舆情 | `search` | `pro` | `social` |
| 复杂问题分析 | `research` | `reasoning` | `web`/`scholar` |
| 深度调研报告 | `research` | `deep research` | `scholar` |
| 技术方案比较 | `research` | `reasoning` | `web` |
