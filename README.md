# game-concept-gate

一个用于 [Codex](https://developers.openai.com/codex/) 的游戏概念澄清与立项闸门 Skill。

它通过十个核心问题，帮助你把模糊的游戏想法整理成可讨论、可验证的概念方案。在核心玩法尚未明确、概念存在根本矛盾，或用户尚未确认立项前，它不会直接进入正式开发。

## 解决的问题

游戏开发中最常见的问题之一，是在目标、核心循环和玩家决策还不清楚时就开始写代码、选技术栈或排期。

这个 Skill 把“先想清楚再开发”变成了一个可执行流程：

- 分组提问，而不是一次抛出十个问题
- 把模糊形容词追问成可执行规则
- 检查目标、选择、代价和反馈是否形成闭环
- 输出统一的《游戏概念立项摘要》
- 在用户明确确认前阻止正式项目开发
- 允许有边界的探索性原型，避免闸门过度僵化

## 核心流程

```text
草稿 → 待确认 → 已确认
```

1. **草稿**：信息不完整或规则不可执行。
2. **待确认**：十项已回答，没有阻塞性矛盾，概念摘要已准备好。
3. **已确认**：用户明确同意立项，可以进入 MVP、技术栈和开发规划。

## 安装


将仓库克隆到 Codex 的个人 Skill 目录：

```bash
git clone https://github.com/George-Zh-Cool/game-concept-gate.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/game-concept-gate"
```

安装后，在新任务中即可使用。如果 Codex 尚未发现 Skill，请新建一个任务后再试。

也可以下载仓库 ZIP，将解压后包含 `SKILL.md` 的目录放到：

```text
~/.codex/skills/game-concept-gate
```

最终目录结构应为：

```text
game-concept-gate/
├── SKILL.md
├── README.md
├── .gitignore
├── LICENSE
└── agents/
    └── openai.yaml
```

## 使用

直接描述你的游戏想法，Codex 会根据 `description` 判断是否调用：

```text
我想做一款单机回合制武侠 Roguelite，但我还没有想清楚核心循环。
```

也可以显式调用：

```text
$game-concept-gate 我想做一款……
```

## 输出

完成澄清后，Skill 会整理出：

- 核心目的与目标玩家
- 玩家模式
- 终极目标与短期目标
- 独有核心规则
- 核心资源
- 局内和局外核心循环
- 玩家行为与关键选择
- 公开信息和隐藏信息
- 核心障碍与牺牲
- 单局及整体结束条件
- 核心游玩体验
- 主要设计风险
- 未解决问题
- 立项结论

## 适用范围

适用于：

- 新游戏概念立项
- 开发前玩法澄清
- 已有设计文档的缺口审计
- 判断一个想法是否值得继续投入

不适用于：

- 纯头脑风暴或灵感发散
- 多个游戏概念的理论比较
- 已确认立项后的局部功能实现
- Bug 修复、数值调整和美术修改

## 设计原则

- 不用“开放世界”“高自由度”“沉浸感”等形容词代替具体规则。
- 不把用户未确认的推断写成确定结论。
- 不为了填满模板而编造内容。
- 不用原型验证替代正式立项判断。
- 用户明确确认前，不开始正式项目开发。

## 验证

使用 Codex Skill Creator 提供的校验脚本：

```bash
python3 "${CODEX_HOME:-$HOME/.codex}/skills/.system/skill-creator/scripts/quick_validate.py" \
  "${CODEX_HOME:-$HOME/.codex}/skills/game-concept-gate"
```

校验通过时会输出：

```text
Skill is valid!
```

## 贡献

欢迎通过 Issue 报告问题、提出改进建议，或通过 Pull Request 提交修改。

提交修改前，请尽量：

- 保持 Skill 的触发范围清晰
- 避免把通用建议写成强制规则
- 运行 `quick_validate.py` 检查格式
- 在真实游戏想法上测试修改后的行为

## License

本项目采用 [MIT License](LICENSE)。

你可以自由使用、复制、修改、合并、发布、分发、再许可和销售本项目的副本，但需要保留原版权声明和许可证声明。
