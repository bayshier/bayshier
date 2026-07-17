<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=3DDC84&height=180&section=header&text=Easin's%20Code%20Lab&fontSize=60&fontColor=ffffff" width="100%"/>

  <img src="https://raw.githubusercontent.com/bayshier/Jetpack-Mvvm/main/62773-yoga-developer.gif" width="150" style="margin-bottom: 10px;">

  <h3>📱 资深 Android 开发者 | 🤖 AI Coding 探索者 | 🛠 跨平台实践者</h3>

  <p>
    <i>“不再是单纯的代码编写者，而是与 AI 协同进化的应用架构师。”</i>
  </p>
</div>

---

### 💻 现代 Android 实践 (Modern Android Development)

技术选型的重点不在于"追新"，而在于看清每一项变更背后的工程动机——它解决了什么、又把复杂度转移到了哪里。

#### 🎨 UI · Jetpack Compose & Material 3 Expressive

全程以 Compose 声明式 UI 为基准，但更值得关注的是 **Material 3 Expressive**（M3 1.4+）带来的范式转变：

- **动画的主题化：** `MotionScheme` 把"动效"提升为一等公民——就像 `ColorScheme` 之于颜色。动画不再散落在各处手搓 `tween`，而是可被主题统一编排、可切换。宜用它来收敛全应用的动效一致性。
- **新的组合式组件：** `FloatingToolbar`、`ButtonGroup`、`SplitButton`、`WideNavigationRail` ——这些不是简单的 UI 控件，而是对"上下文操作"和"大屏/折叠屏导航"的官方回答。折叠屏适配中应优先评估它们，而非自行造轮子。
- **重组与性能：** 审视 Compose 代码的粒度，应是"哪些状态读取会导致重组、范围多大"，而非泛泛地"用 remember 优化"。

> 对应真实变更：Material Icons 体系在 1.4 起被移除，迁移至 Material Symbols——这类"看似只是换图标"的改动，背后是图标系统的可变字体化，主动跟进才能避免被动踩坑。

#### 🏗 架构 · UDF 与分层 (不是教条的 MVI)

Google 在《Guide to App Architecture》中真正推荐的是 **单向数据流 (UDF) + 分层架构 (UI / Domain / Data)**，而非某个特定缩写。实践应建立在这个本质上：

- **状态是单向流动的：** UI 事件 → Intent → ViewModel 归约 → 不可变 UiState → UI 渲染。坚持 `UiState` 的不可变与单一数据源，因为它让"状态从哪来"这个问题永远有确定答案。
- **Domain 层按需而非教条：** 不必为了"干净"而强行套用 UseCase。当多个 ViewModel 复用同一块业务逻辑、或需要把业务规则与数据层解耦时，Domain 层才显现价值——它应服务于"复用与可测试性"，而不是架构图的对称性。
- **参考但不盲从 NiA：** Google 的 [Now in Android](https://github.com/android/nowinandroid) 是绝佳的参考实现，但更应关心它"为什么这样切模块"，而不是照搬它的目录结构。

#### ⚙️ 平台演进 · 把系统变更当作架构契机

跟踪 Android 平台的**行为变更**远多于"新特性"，因为前者才决定线上稳定性：

- **Android 15 · 16KB page size：** 要求所有 NDK 依赖重新编译对齐。对纯 Kotlin 应用影响有限，但它把"原生库的内存对齐"这件过去被忽略的事推到了台前——宜将其纳入 CI 的合规检查。
- **Predictive Back（预测式返回）：** 返回手势从"黑盒"变成可预测动画，但代价是必须放弃框架层的旧转场、改用 `androidx` 转场与 Navigation/Fragment 管理的返回栈。把它当作一次理清导航状态机的机会。
- **min-target 提升至 24、Edge-to-edge：** 这些"强制项"宜在升级窗口期一次性消化，而非逐版本打补丁。

#### 🚀 跨平台与工程化 (KMP · Build · Performance)

- **KMP 的务实边界：** 拥抱 Kotlin Multiplatform 共享网络/数据/核心逻辑，但对 **Compose Multiplatform 共享 UI** 保持审慎——它是否适合，取决于团队是否能接受 UI 层的妥协。默认策略应是"逻辑下沉、UI 各端原生"。
- **K2 编译器：** Kotlin 2.x 的 K2 编译器已稳定，带来的不只是编译提速，更是前端重写后更可预测的增量编译行为。
- **构建即代码：** Version Catalogs (TOML) 统一依赖、Convention Plugins 收敛构建约定。模块化的目标不是把工程拆得多碎，而是让每个模块的构建配置**可被复用、可被推导**。
- **性能可度量：** Baseline Profiles + Macrobenchmark，让启动优化从"感觉变快了"变成"基准曲线下降了 X ms"。

---

### 🧠 AI 驱动的工作流 (AI-Powered Workflow)

> **"AI 并未取代开发工作，它让人跳出繁琐的样板代码，专注于系统设计与创新。"**
>
> AI 工具不是"更聪明的补全"，而是一个**需要被正确调度的协作者**。关键在于：把什么交给它、把什么牢牢握在自己手里。

| 工具 | 在工作流中的定位 | 如何使用 |
| :--- | :--- | :--- |
| **Claude Code**<br/>*(Anthropic)* | **深度推理型协作者** | 面对祖传代码时，让它先通读整个模块、输出"现状—痛点—迁移方案—影响面"的结构化分析，再逐行 Review 决定取舍。它擅长长上下文与逻辑推演，但**架构判断与最终合并权始终在工程师手中**。 |
| **Google Gemini**<br/>*(Gemini 2.5 Pro)* | **Android 生态向导** | 解决 SDK 兼容性、Crash 归因这类"需要贴近官方生态"的问题。同时关注 **Google AI Edge**——把生成式模型部署到端侧、实现离线与隐私优先的推理，是端侧 AI 的务实路径。 |
| **OpenAI Codex**<br/>*(GitHub Copilot)* | **高频行级生成** | IDE 内的毫秒级补全、批量生成 data class 与样板代码。价值在于**把人从重复中解放**，但产出的每一段都需要理解后才会采纳。 |
| **MCP 协议** | **连接 AI 与工具链的桥梁** | Model Context Protocol 让 AI 能结构化地访问工具与上下文。它是让 Agent 真正"动手"而非"动嘴"的协议基础。 |

**关于 AI Coding 的一个判断：** 决定资深开发者能否用好 AI 的，不是会用多少工具，而是**能否清晰地把意图与约束传达出去、并在 AI 产出后保持足够的批判性审查**。越是让 AI 生成代码，越要能读懂它、证伪它。

---

### 📫 获取连接 (Initialize Connection)

```bash
# 随时欢迎技术交流或探讨 AI 工具的最新玩法
$ ping easin.developer

> Response:
> [Email]  Easinex@gmail.com
```
