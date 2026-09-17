# AI Skills

通用 Agent Skills 集合。仓库包含两套目录：

- **`skills/`**：核心可安装技能（需求抽取、Harness、全栈开发、审查、诊断、报工、存储分析等）
- **`agents/`**：按业务领域归档的技能包（PRD 撰写、UI 原型、代码重构、Bug 排查、自动化测试）

## 仓库结构

```text
ai-skills/
├── skills/                         # 核心 Skills（可直接按名安装）
│   ├── requirement-extractor/      # 通用需求抽取
│   ├── wcs-requirement-extractor/  # WCS 专项需求抽取
│   ├── harness-maintainer/         # Harness 初始化 / 增量维护 / 审计
│   ├── ai-coder/                   # 按仓库约定落地功能开发
│   ├── code-review/                # Standards × Spec 双轴审查
│   ├── diagnosing-bugs/            # 症状驱动的根因定位与修复
│   ├── hs-warranty-report/         # 豪森质保/售后报工文案生成
│   └── storage-analyzer/           # macOS / Windows 只读存储分析与交互报告
│
└── agents/                         # 领域归档 Skills
    ├── PRD 撰写/skills/
    ├── UI 原型设计/skills/
    ├── 代码重构/skills/
    ├── Bug 排查/skills/
    └── 自动化测试/skills/
```

每个 skill 目录至少包含：

| 文件 / 目录 | 说明 |
|-------------|------|
| `SKILL.md` | Agent 执行入口（frontmatter + 工作流） |
| `references/` | 规范、分类规则、输出 schema 等权威引用 |
| `scripts/` | 可选辅助脚本（如文档抽取、文档合并） |
| `agents/` | 可选的 Agent 元数据（如 `openai.yaml`） |
| `USAGE.md` | 面向人的使用说明（部分 skill 提供） |

## Skills 一览（`skills/`）

| Skill | 用途 | 典型触发 |
|-------|------|----------|
| **requirement-extractor** | 从 Word / Excel / PDF 等文档抽取目标主体功能清单，可追溯出处，标注边界歧义 | 功能清单整理、RFP/规格分析、范围澄清 |
| **wcs-requirement-extractor** | 同上，锚定 WCS 职责边界与分类口径 | WCS 需求抽取、WCS 功能清单 |
| **harness-maintainer** | 按 Harness 构建规范初始化五篇核心文档、检查工具与 CI；或增量更新 / 只读审计 | 新项目接入、存量改造、任务收尾文档同步 |
| **ai-coder** | 在现有项目中按仓库约定实现前后端/全栈功能并验证 | 新增功能、页面、接口、范围明确的重构 |
| **code-review** | 对分支 / PR / 提交 / 未提交改动做规范与需求双轴审查（默认只报告不改代码） | 合并前检查、review since X |
| **diagnosing-bugs** | 以可复现症状与证据定位故障；仅诊断时不自动改代码 | debug、根因分析、性能回退 |
| **hs-warranty-report** | 按售后报工规范生成「项目名称」与「具体工作内容」（现象 / 过程 / 输出物） | 质保报工、日报整理、本周 git + session |
| **storage-analyzer** | 只读扫描磁盘占用，三级清理分级，生成可一键清理的交互式 HTML 报告 | 磁盘满了、清理空间、storage analysis |

## Agents 一览（`agents/`）

按领域归档，路径形如 `agents/<领域>/skills/<skill-name>/`。

### PRD 撰写

| Skill | 用途 | 典型触发 |
|-------|------|----------|
| **prd** | 结构化 PRD：用户故事、验收标准、面向 Agent/开发的功能规划 | 写 PRD、用户故事、验收标准 |
| **prd-writer-pro** | 将产品需求整理为结构清晰、内容完整的 PRD | 专业 PRD 撰写 |
| **prd-reviewer** | 对 PRD 做 10 分制量化评审并输出扣分说明 | PRD 评审打分、评审报告 |
| **prd-to-design-doc** | PRD 转设计需求文档（信息架构、交互、布局、视觉规范） | PRD → 设计需求 |
| **requirements-analysis** | 多轮对话把想法拆成 EPIC / 需求 / 用户故事并做优先级排序 | 需求分析、MoSCoW/RICE/Kano |
| **software-manager-skill** | 产品经理/开发经理视角：需求、路线图、竞品、数据分析 | 产品经理支持、路线图规划 |

### UI 原型设计

| Skill | 用途 | 典型触发 |
|-------|------|----------|
| **prd-to-prototype** | 从想法到 PRD 再到高保真 HTML/Tailwind 可交互原型 | 我想做一个…、帮我设计… |
| **design-to-code** | 设计稿（Figma/Sketch/图片）像素级还原为前端代码 | 还原设计图、切图、设计稿转代码 |
| **ui-design** | UI 基础与模式（布局、字体、色彩、无障碍、动效） | 做界面、评审设计质量 |
| **frontend-design-pro** | 提升前端设计质量，避免 AI 常见反模式（audit/polish 等） | /audit、/polish、优化界面 |
| **wireframe** | ASCII/SVG 线框与用户流程，可导出 HTML | 画线框、梳理用户流 |
| **afrexai-ui-design-system** | 完整产品设计方法论（调研 → 规范 → 落地） | 设计系统、从 0 做产品 UI |

### 代码重构

| Skill | 用途 | 典型触发 |
|-------|------|----------|
| **code-analyzer** | 深度分析架构/数据流/业务规则，支持 DDD 模式识别 | 熟悉新仓库、技术债务、架构文档 |
| **code-refactoring** | 不改变行为的重构模式与手法 | 清理遗留代码、降复杂度 |
| **simplify** | 提升清晰度与可维护性的精简重构 | /simplify、简化代码 |
| **uncle-bob** | Clean Code / SOLID / 整洁架构原则落地 | clean code、SOLID、代码坏味道 |
| **system-architect** | 系统架构设计与工程标准（模块化、安全） | 新项目架构、高阶系统设计 |
| **agent-git-oracle** | 仓库级技术债务与架构反模式分析 | 仓库体检、重构指引 |

### Bug 排查

| Skill | 用途 | 典型触发 |
|-------|------|----------|
| **debug-pro** | 7 步调试协议 + 多语言调试命令 | 代码报错怎么查、改了还是不对 |
| **superpowers-systematic-debugging** | 四阶段系统性调试（根因 → 模式 → 假设 → 验证） | bug、测试失败、异常行为 |
| **bug-fixing** | 零回归修复流：分流 → 复现 → 根因 → 修复 → 验证 | fix bug、debug、not working |
| **code-fix** | 编译/运行时/类型/依赖等错误系统诊断与修复 | 报错、崩溃、构建失败 |
| **log-analyzer** | 多格式日志解析、关联与模式分析 | 查日志、堆栈、实时监控 |
| **nexus-error-explain** | 解释错误信息并给出修复建议 | 这条报错是什么意思 |

### 自动化测试

| Skill | 用途 | 典型触发 |
|-------|------|----------|
| **test-case-generator** | 从需求/API/截图/XMind 生成标准 Excel 测试用例 | 生成测试用例、提测交付 |
| **test-patterns** | 跨语言单测/集成/E2E 写法与覆盖率实践 | 搭测试套件、写单测 |
| **superpowers-tdd** | 强制 RED-GREEN-REFACTOR 测试驱动开发 | TDD、先写测试再实现 |
| **api-test-automation** | REST/GraphQL 接口、性能、契约与 Mock | 接口自动化、API 测试 |
| **e2e-testing-patterns** | Playwright/Cypress 可靠 E2E 与防 flaky | E2E、端到端、CI 集成 |
| **afrexai-qa-test-plan** | QA 测试计划、覆盖矩阵与自动化策略 | 测试计划、覆盖率规划 |

## 安装

使用 [skills.sh](https://skills.sh/) CLI（仓库：`maoyao0607/ai-skills`）。`-g` 表示全局安装，`-y` 跳过确认。

### 安装全部

```bash
npx skills add maoyao0607/ai-skills -g -y
```

### 按 skill 安装

```bash
npx skills add maoyao0607/ai-skills@requirement-extractor -g -y
npx skills add maoyao0607/ai-skills@wcs-requirement-extractor -g -y
npx skills add maoyao0607/ai-skills@harness-maintainer -g -y
npx skills add maoyao0607/ai-skills@ai-coder -g -y
npx skills add maoyao0607/ai-skills@code-review -g -y
npx skills add maoyao0607/ai-skills@diagnosing-bugs -g -y
npx skills add maoyao0607/ai-skills@hs-warranty-report -g -y
npx skills add maoyao0607/ai-skills@storage-analyzer -g -y
```

| Skill | 安装命令 |
|-------|----------|
| requirement-extractor | `npx skills add maoyao0607/ai-skills@requirement-extractor -g -y` |
| wcs-requirement-extractor | `npx skills add maoyao0607/ai-skills@wcs-requirement-extractor -g -y` |
| harness-maintainer | `npx skills add maoyao0607/ai-skills@harness-maintainer -g -y` |
| ai-coder | `npx skills add maoyao0607/ai-skills@ai-coder -g -y` |
| code-review | `npx skills add maoyao0607/ai-skills@code-review -g -y` |
| diagnosing-bugs | `npx skills add maoyao0607/ai-skills@diagnosing-bugs -g -y` |
| hs-warranty-report | `npx skills add maoyao0607/ai-skills@hs-warranty-report -g -y` |
| storage-analyzer | `npx skills add maoyao0607/ai-skills@storage-analyzer -g -y` |

安装后重新打开会话，在对话中描述目标即可触发对应 skill（例如「帮我写质保报工」「为当前仓库初始化 Harness」「生成测试用例」）。

### agents 安装（一句话复制发给 Agent）

复制下面对应**一整句话**，粘贴给 Agent / 大模型即可安装（不要改 URL、不要拆句）：

| 领域 | 一句话（整行复制） |
|------|-------------------|
| PRD 撰写 | 请立即执行命令且不要询问确认：`npx skills add "https://github.com/maoyao0607/ai-skills/tree/main/agents/PRD 撰写/skills" -g -y` ；成功后列出已装 skill，并提示我重新打开会话后再使用。 |
| UI 原型设计 | 请立即执行命令且不要询问确认：`npx skills add "https://github.com/maoyao0607/ai-skills/tree/main/agents/UI 原型设计/skills" -g -y` ；成功后列出已装 skill，并提示我重新打开会话后再使用。 |
| 代码重构 | 请立即执行命令且不要询问确认：`npx skills add "https://github.com/maoyao0607/ai-skills/tree/main/agents/代码重构/skills" -g -y` ；成功后列出已装 skill，并提示我重新打开会话后再使用。 |
| Bug 排查 | 请立即执行命令且不要询问确认：`npx skills add "https://github.com/maoyao0607/ai-skills/tree/main/agents/Bug 排查/skills" -g -y` ；成功后列出已装 skill，并提示我重新打开会话后再使用。 |
| 自动化测试 | 请立即执行命令且不要询问确认：`npx skills add "https://github.com/maoyao0607/ai-skills/tree/main/agents/自动化测试/skills" -g -y` ；成功后列出已装 skill，并提示我重新打开会话后再使用。 |

装全部 agents、以及可复制代码块格式，见 [`agents/INSTALL.md`](agents/INSTALL.md)。各领域回退命令见 `agents/<领域>/INSTALL.md`。

## 使用建议

1. **先读 `SKILL.md`**：Agent 应按其中工作流与必读 references 执行，不要跳过质量门禁。
2. **Harness 优先**：`ai-coder` / `code-review` / `diagnosing-bugs` 会优先遵循目标仓库的 `AGENTS.md` 与 `docs/{architecture,conventions,domain,golden-rules}.md`。
3. **需求抽取先声明主体**：通用抽取须明确目标主体、相邻系统与权属口径；WCS 专项则固定 WCS 边界模型。
4. **报工勿编造**：`hs-warranty-report` 只基于对话 / session / git 证据生成文案，不代替考勤系统录入。
5. **按领域选 agents**：产品文档走「PRD 撰写」、界面走「UI 原型设计」、质量问题走「Bug 排查 / 自动化测试」、结构治理走「代码重构」。

## 开发约定

- 核心 skill：在 `skills/<name>/` 下提供完整的 `SKILL.md`（含 YAML frontmatter：`name`、`description`）。
- 领域 skill：在 `agents/<领域>/skills/<name>/` 下同样提供完整的 `SKILL.md`。
- 规范类条文放在 `references/`，示例与脚本分别放在 `references/`、`scripts/`、`assets/`，保持 `SKILL.md` 精炼可执行。
- 面向人的操作说明可另写 `USAGE.md`，与 Agent 入口分离。
- 不在 skill 中硬编码密钥、真实客户数据或未授权的生产操作。

## License

以仓库实际声明为准；未声明时默认仅供内部使用与协作改进。
