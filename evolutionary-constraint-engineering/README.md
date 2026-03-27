# Evolutionary Constraint Engineering

这是当前正式启用的 `ECE` 主版本。

## 适用场景

在以下情况优先使用：

1. 需求模糊、矛盾、跨模块，不能直接开写。
2. 错做代价高，需要先确认假设、约束、依赖和可行性。
3. 任务可能需要判断是单代理推进，还是引入挑战者、探针或多代理协作。

不适合：

1. 单文件、低风险、已经有明确失败用例的局部修复。
2. 纯机械改动、纯文案改动、没有明显需求收敛问题的任务。

## 核心思路

这套 skill 的目标不是直接“写代码”，而是先把用户意图编译成可实现约束，再从约束进入实现。

简化流程：

1. 做 `mode decision`
2. 做假设审计
3. 发散方案
4. 归一化为原子约束
5. 正交质疑
6. 补全依赖
7. 做 probe
8. 红蓝对抗
9. 产出 EVCL
10. 再进入实现与验证

## 三种模式

### `solo`

适合局部、紧耦合、写集重叠强的问题。

### `paired`

适合实现仍由一个主代理推进，但需要额外引入一个独立角色。

子模式：

- `paired-challenge`
- `paired-probe`
- `paired-review`

### `orchestrated`

适合跨模块、高风险、可并行搜证或分工实施的任务。

## 快速判定

先给任务打分：

- 跨模块 `+1`
- 高风险 `+1`
- 需求冲突 `+1`
- 需要 probe `+1`
- 存在 2 个以上可并行子域 `+1`
- 写集可隔离 `+1`

阈值：

- `0-1` 分：`solo`
- `2-3` 分：`paired`
- `4+` 分：`orchestrated`

## 关键产物

每次使用至少保留：

- `mode decision`
- `assumption register`
- `constraint pool`
- `dependency map`
- `probe log`
- `red-blue findings`
- `EVCL draft`

## 目录说明

- `SKILL.md`
  主技能说明，实际触发入口。
- `references/mode-selection.md`
  模式选择规则。
- `references/evcl.md`
  原始 EVCL 参考。
- `references/evcl-v2-template.md`
  当前推荐的 EVCL v2 模板。
- `references/artifact-templates.md`
  轻量 artifact 模板。
- `references/pressure-scenarios.md`
  压力场景，用来验证 skill 是否真的有收益。

## 当前版本说明

当前主版本已经吸收了 v2 的有效增强：

1. `solo / paired / orchestrated` 三模式
2. 更明确的角色模型
3. EVCL v2 模板
4. 更明确的禁令和使用边界

原 `v2` 候选版已归档，不再参与默认触发，避免同类 skill 冲突。
