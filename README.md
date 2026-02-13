# pig-plugin-summary

> 聊天总结插件 - [pig-sender](https://github.com/PJWaurora/pig-sender) QQ 机器人模块

## 功能

- **智能总结** — 使用 LLM（大语言模型）分析群聊天记录，生成结构化总结报告
- **并发分析** — 支持并发 LLM 处理，加速大量消息的分析
- **话题提取** — 自动识别聊天中的热门话题和讨论主题
- **金句挖掘** — 从对话中提取精彩语录和金句
- **词频统计** — 使用 jieba 分词进行关键词词频分析
- **发言排行** — 统计群成员发言次数和活跃度排行
- **可视化报告** — 生成精美的图片报告，包含话题、金句、词云、排行榜等
- **重试机制** — LLM 请求支持自动重试和指数退避，提升稳定性

## 架构

```
summary/
├── manifest.json          # 模块元信息与配置 schema
├── summary.py             # 主模块（SummaryModule）— 入口
├── analyzer.py            # 消息分析器 — 词频统计、发言排行
├── llm_analyzer.py        # LLM 分析器 — 话题提取和金句分析
└── image_generator.py     # 报告图片生成器
```

## 配置

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `llm_timeout` | integer | `30` | 单次 LLM 请求超时（秒） |
| `llm_retries` | integer | `3` | LLM 请求最大重试次数 |
| `llm_backoff` | number | `2.0` | 重试间隔退避基值（秒） |
| `max_topics` | integer | `5` | 分析结果显示的最大话题数 |
| `max_golden_quotes` | integer | `3` | 分析结果显示的最大金句数 |
| `enable_golden_quotes` | boolean | `true` | 是否启用金句分析 |
| `topic_prompt` | string | `""` | 自定义话题分析 Prompt 模板 |
| `golden_quote_prompt` | string | `""` | 自定义金句分析 Prompt 模板 |

## 使用方法

```
@机器人 总结        # 生成当日聊天总结
@机器人 总结 100    # 总结最近100条消息
```

## 依赖

- `jieba` — 中文分词
- `Pillow` — 图片渲染
- `openai` — LLM API 调用

## 许可

MIT
