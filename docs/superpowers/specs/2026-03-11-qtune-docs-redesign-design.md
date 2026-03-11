# Qtune Documentation Redesign Design

## Goal

将当前以 `Laser Piano / ESP32 单排激光琴键原型` 为中心的项目文档，重构为以 `Qtune 光影音乐工作站` 为核心的完整产品文档体系，覆盖硬件设备、配套 App、内容/社区平台三大部分，并保留足够的技术架构深度支持后续实现。

## Context

当前仓库文档存在三个结构性问题：

1. 顶层叙事仍然围绕激光钢琴原型，产品定位过窄，无法承接新的完整产品定义。
2. 现有文档职责交叉，`README`、架构文档和实施计划之间存在重复叙述。
3. 部分链接和命名残留旧项目路径或旧产品表述，不适合作为后续项目基础。

用户已经确认以下约束：

- 只保留 `Qtune` 命名，不使用 `LumiBeats`
- 不再做激光钢琴项目
- 文档需要同时覆盖 `硬件设备 + 配套 App + 内容/社区平台`
- 文档体系需要兼顾产品定义和技术落地

## Recommended Approach

采用“产品主线 + 技术落地 + 交付计划”的分层文档结构：

- 顶层入口文档负责统一项目定位和导航
- 产品文档负责说明用户价值、场景和功能规格
- 技术文档负责说明系统、硬件、App、平台四个层面的架构边界
- 路线图和实施计划单独管理，避免和产品规格、系统架构相互污染

该结构比“单一大文档”更容易维护，也比“纯按子系统拆散”更容易建立完整认知。

## Information Architecture

### 1. Repository Entry

`README.md`

职责：

- 定义 `Qtune 光影音乐工作站` 是什么
- 概述核心价值和系统组成
- 提供文档导航
- 说明当前版本范围

不包含：

- 详细硬件参数表
- 完整功能规格表
- 具体模块实现细节

### 2. Product Layer

`docs/product-overview.md`

职责：

- 说明产品背景、目标用户、核心价值主张
- 定义典型使用场景
- 说明核心交互原则和版本边界

`docs/prd.md`

职责：

- 汇总完整产品需求
- 覆盖硬件规格、App 功能、社区平台功能、性能目标、风险与商业化摘要

不包含：

- 设备端和云端的内部模块实现方式

### 3. Technical Architecture Layer

`docs/system-architecture.md`

职责：

- 描述 `Qtune 设备`、`移动 App`、`云端服务`、`社区平台` 的系统边界
- 说明校准、演奏、录制、同步、分享等核心链路的数据流

`docs/hardware-architecture.md`

职责：

- 描述投影、感应、处理器、音频、连接、电池、结构、热设计等硬件组成
- 记录关键技术风险和预案

`docs/app-architecture.md`

职责：

- 描述 App 的功能模式、编辑器能力、录制分享、设备连接、账户与同步模型

`docs/platform-architecture.md`

职责：

- 描述社区平台中的作品、模板、谱面、推荐分发、审核和后台运营能力

### 4. Delivery Layer

`docs/roadmap.md`

职责：

- 以版本视角说明 `V1.0 / V1.5 / V2.0` 的边界和演进顺序

`docs/implementation-plan.md`

职责：

- 从实施角度拆分阶段目标和交付顺序
- 为后续设计细化和开发准备提供执行路线

## Document Boundaries

为避免重复，文档之间采用以下边界：

- `README.md` 只做入口和导航，不承载完整规格
- `product-overview.md` 解释“为什么做”和“为谁做”
- `prd.md` 解释“产品必须具备什么”
- `system-architecture.md` 解释“系统各部分如何协同”
- `hardware-architecture.md`、`app-architecture.md`、`platform-architecture.md` 分别解释“各子系统如何组织”
- `roadmap.md` 只说明版本递进，不重复完整规格
- `implementation-plan.md` 只说明实施顺序和阶段目标，不代替架构文档

## Content Mapping From Existing PRD

用户给出的产品需求内容将按以下方式拆分：

- 产品背景、定位、核心价值、目标用户 -> `docs/product-overview.md`
- 硬件规格、软件功能、交互原则、技术可行性、商业模式摘要 -> `docs/prd.md`
- 设备、App、平台之间的关系 -> `docs/system-architecture.md`
- 硬件规格与风险细化 -> `docs/hardware-architecture.md`
- App 模式与内容编辑能力 -> `docs/app-architecture.md`
- 社区、模板、分享与内容流转 -> `docs/platform-architecture.md`
- `V1.0 / V1.5 / V2.0` 版本规划 -> `docs/roadmap.md`

## Migration Strategy

文档迁移将采用重写为主、保留路径最小化冲突的策略：

1. 重写 `README.md`，切换仓库主叙事
2. 新增产品和架构文档，承接新的信息结构
3. 重写现有 `docs/implementation-plan.md`
4. 让旧的 `docs/architecture.md` 和 `docs/hardware.md` 退出主路径，避免名称继续误导

推荐做法是直接以更明确的新文件名新增文档，而不是延续旧标题。

## Risks And Controls

### Risk 1: 产品文档和技术文档互相重复

控制方式：

- 在每份文档开头明确职责
- 表格、流程和架构图按单一职责归属

### Risk 2: 旧术语残留导致认知混乱

控制方式：

- 全仓统一替换 `Laser Piano`、激光琴键原型等旧表述
- 所有文档只保留 `Qtune`

### Risk 3: 产品野心过大，文档失去边界

控制方式：

- 明确 `V1.0 / V1.5 / V2.0` 的能力边界
- 将未来能力集中在路线图文档，不塞入首版架构强约束

## Testing And Verification

本次是文档重构，不涉及代码运行验证，完成标准如下：

- 所有主文档标题、定位和命名统一为 `Qtune`
- 文档导航链路可用，没有残留旧项目绝对路径
- 顶层文档与子文档边界清晰，没有明显重复段落
- 现有 PRD 核心信息已拆解到对应文档，而不是堆在单一文件中
