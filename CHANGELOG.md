# 变更记录

## 2026-11-03 首次发布（此前为空仓库）

仓库此前只有一个 0 字节 README，无技能内容。本版补齐为可独立使用的单棒发行版：

- 收录完整技能：`SKILL.md` + `references/architecture-checklist.md` + `scripts/check_architecture.py`
- 新增 `examples/06-architecture-design.example.md`：可直接照改的六节成品，实测校验脚本退出码 0
- 新增 `references/adr-template.md`：架构决策记录模板，补上「选型理由」的落点（主仓库无此文件）
- 新增 `docs/新手手册.md`（怎么做、为什么、常见错）与 `docs/技术文档.md`（输入输出契约、校验器行为、已知限制、优缺点、失败模式）
- 新增 Pages 首页、Issue 表单、PR 模板
- 定位说明：本仓库是 agent-pipeline-skills 第六棒的单体发行版，与该仓库 `architecture-designer/` 同源；改动须双向同步
