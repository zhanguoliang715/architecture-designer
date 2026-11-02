# architecture-designer

**给系统定分层、定模块边界、定扩展点——写代码之前先把骨架画对。产出 `06-architecture-design.md`，交稿前跑脚本过门禁，缺分层/模块/扩展性直接非 0 退出。**

![Python](https://img.shields.io/badge/python-3.9%2B-3776AB)
![Dependencies](https://img.shields.io/badge/pip%20install-0%20个依赖-2E7D32)
![License](https://img.shields.io/badge/license-MIT-yellow)

## 它解决什么问题

架构做错的代价不是"代码丑"，是**第二个功能加不进去**：

- 分层没定，业务逻辑和 SQL 混在一个文件里，换数据库要改全部代码；
- 模块边界没定，两个模块互相读对方的表，改一处崩两处；
- 扩展点没留，加个"到期提醒"要动五个既有文件；
- 技术选型没写理由，半年后没人敢换，也没人知道当初为什么选它。

这个技能把这些写成一份**有固定六节结构、能被脚本校验**的文档。不是让你"想想架构"，是把架构落到纸上、能被下游开发照着写。

## 30 秒上手

```bash
git clone https://github.com/zhanguoliang715/architecture-designer.git
cd architecture-designer
python scripts/check_architecture.py examples/06-architecture-design.example.md
```

退出码 0 说明脚本正常工作、示例产物合格。然后让 Agent 按 `SKILL.md` 干活，产出你的 `06-architecture-design.md`，再跑同一个脚本校验。

## 产出结构（六节，固定）

```
一、架构总览      一句话 + 分层图（文字化）
二、分层架构      层 / 职责 / 依赖的下层 / 关键组件
三、模块划分      模块 / 职责 / 对外接口 / 依赖模块
四、技术选型      关注点 / 选型 / 理由
五、扩展性设计    新功能怎么加 + 数据模型怎么演进
六、约束与约定    目录结构、命名、依赖方向等硬规则
```

## 开工门禁（最容易被忽略的部分）

**第 0 步不是设计，是确认能不能开工**：

1. 必须有 `02-requirement-review.md`，结论为 **YES**；
2. 必须有 `01-prd.md`，含 FR 编号清单；
3. 必须有 `05-database-design.md`（持久化层要照着它分）；
4. 缺任何一项，**停下，不边猜边设计**。

## 独立使用 与 主仓库的关系

本仓库是 [agent-pipeline-skills](https://github.com/zhanguoliang715/agent-pipeline-skills) 第六棒的单体发行版，内容与该仓库 `architecture-designer/` 目录同源。

| 你的情况 | 用哪个 |
|---|---|
| 只要架构设计这一棒，需求与数据库设计已有现成文档 | **本仓库**，拷走根目录即可 |
| 要走完整流水线（需求→评审→设计→开发→测试→安全） | [主仓库](https://github.com/zhanguoliang715/agent-pipeline-skills)，各棒产物按 `01-` 到 `09-` 串联 |

本仓库额外提供主仓库里没有的 [ADR 决策记录模板](references/adr-template.md)——技术选型的理由需要一个比"当时觉得挺好"更硬的落点。

## 文档

| 想看什么 | 去哪 |
|---|---|
| 第一次用，怎么一步步做 | [docs/新手手册.md](docs/新手手册.md) |
| 边界、失败模式、已知限制 | [docs/技术文档.md](docs/技术文档.md) |
| 完整规则原文 | [SKILL.md](SKILL.md) |
| 可照改的成品示例 | [examples/](examples/) |
| 官网 | [zhanguoliang715.github.io/architecture-designer](https://zhanguoliang715.github.io/architecture-designer/) |

## 它不是什么

- **不是通用架构建议**。它假定你要交付的是**有前后端的中小型 Web 项目**。换成嵌入式固件、纯算法库、数据分析脚本，分层与模块这两节基本用不上。
- **不替你写代码**。它给开发骨架，不给实现。
- **不判断技术选型对不对**，只要求你写清理由与代价。真正的对错由你的约束决定。
- **不适合微服务拆分**。默认形态是"分层单体"，服务拆分需要另一套判据。

## 环境

Python ≥ 3.9，仅标准库，零 `pip install`。

## License

[MIT](LICENSE)
