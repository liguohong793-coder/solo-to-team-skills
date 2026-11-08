# examples（主示例｜上手先走这一条）

> 状态：**v0.9-draft**，非最终发布稿。English: see [README.en.md](../README.en.md) → "How to start"; full English walkthrough: [walkthrough-meeting-notes/README.en.md](walkthrough-meeting-notes/README.en.md).
>
> 已在多个 Agent 工具中完成实际使用验证（取得→装／配置→按名调用→产出登记行；另外当前包上八家各有一例有限任务的验收记录（真实成果→对照要求检查→人工验收）：Codex 保留此前单独验证的一例，其余七家按同一会议转写题补验，部分宿主经受阻重跑或退回修订后才通过；不代表稳定性或所有任务都能做成，调用方式各家不同（有的由使用者本人在宿主里发出，有的命令行或代点），部分宿主未保留技能加载的原始轨迹；不表示每家四个技能都逐一被调用，也不证明效果，见下文「验证环境」）：**Codex、WorkBuddy、DeepSeek Harness、Cursor、CodeBuddy、Kimi Work、千问办公（QwenWork）** 为「支持」；**Grok Bot** 为「支持，需手动配置」；**Claude Code** 结构已备、走通待补，不在首发支持之列。

本目录放上手示例。目标只有一个：用本包**完成一件实际小任务**，并顺手核一遍本包**能装能调**。只读正文、只看目录结构不算走通。

实测（Cursor CLI，非交互、提示词事先备好）：约 **0.5 分钟**（29.6 秒）。前提：已装并登录 Cursor（含 CLI）、已取得本包、网络可用；从把四支技能拷进 `~/.cursor/skills/` 算到打出可读的「待收」行。不含装、注册宿主，也不含手动打字的时间。这测的只是**已备好环境时用 CLI 打出登记行**要多久，不是陌生人从零装宿主到做完一整件任务的总时长。「约十分钟」仍可作为设计目标／含装宿主的对外口径，**不得写成已测保证**。

## 按你的情况从哪进

- **零基础（刚开始接触 AI 或编程）**：从一张表开始——照下面「主示例」用记事本或表格把派、收、核练一遍。这一步练的是方法；要让 AI 助手按名调用技能，还得先装好一个 Agent 工具（见上级 [README](../README.md)「各宿主怎么装、怎么叫」）。
- **已经在用 AI 助手**：先在你的宿主里装或配置本包（各家装法不同，见上级 [README](../README.md)「各宿主怎么装、怎么叫」），再走主示例，让助手按名调用技能。
- **已在跑多个助手**：直接看每步的「核什么」，把它接进你自己的流程。

不需要先读任何团队制度。装上技能 ≠ 自动成队：到点查、跨助手叫醒这类事，宿主有就用，没有就由人来做（`hooks: {}`＝无自动叫醒）。

## 主示例：派一件小活，收回来，核过再说完成

虚构场景：你让一个 AI 助手把一段会议转写整理成要点，放到指定文件里。（人名、文件名均为虚构。）

**完整跟做在这里：[`walkthrough-meeting-notes/`](walkthrough-meeting-notes/)**（English: [README.en.md](walkthrough-meeting-notes/README.en.md)）。有给定输入 [`input.md`](walkthrough-meeting-notes/input.md)、可复制的派活指令、能通过的成果 [`output-ok.md`](walkthrough-meeting-notes/output-ok.md)、缺项该退回的成果 [`output-missing.md`](walkthrough-meeting-notes/output-missing.md)，以及从「待收」到「已验收」的全部登记行 [`register-lines.md`](walkthrough-meeting-notes/register-lines.md)（含退回分支）。不联网、不登录，记事本就能跟做。下表是它的步骤总览：

| 步 | 流程 | 你做什么 | 用哪支技能／模板 | 核什么 |
|---|---|---|---|---|
| 1 | 提目标 | 写清：整理什么、结果放哪（如 `notes/会议要点.md`）、几点交、做到什么算完 | [`task-register-line.md`](../templates/task-register-line.md) | 一句话能说清「做到什么算完」 |
| 2 | 分工 | 派活前先写一行「待收」：谁在干、谁来收、谁到点查 | [`dispatch-accept-verify`](../skills/dispatch-accept-verify/) | 「待收」行在派活之前已写下 |
| 3 | 交接 | 对方接下记「已接单」；到点去查，文件在约定位置才记「已收到成果」，没交就「续期」（原预计保留）或「升级」 | [`dispatch-accept-verify`](../skills/dispatch-accept-verify/) | 到点有人查，不靠等对方想起来；接单≠成果回来 |
| 4 | 核对 | 说完成前，亲手打开结果文件，对照第 1 步逐条看 | [`evidence-before-done`](../skills/evidence-before-done/) | 证据对得上这一版成果，不是转述；补交后只补核改动部分 |
| 5 | 判断 | 你决定：收下记「已验收」、退回记「退回」、还是改目标 | — （人拍板） | 只有「已验收」或「已取消」才退出未完清单 |

可选：

- 某一步只能你本人做（如登录、确认付款）→ 按 [`beginner-ops-writing`](../skills/beginner-ops-writing/)（含两个虚构示例）只写「请本人来」，不写代做办法。
- 想看真活里这条线在哪漏过 → 翻 [`ops-case-notes`](../skills/ops-case-notes/)。

## 验证环境

验证标准每家一样：取得 → 装／配置 → 按名调用 → 有可检查产出（例如写出一行可读的「待收」登记行）。各家装法与能力不同，下表只说明每家实际验到了哪一步，不说明各家功能相同。

**分开看**：下表的走通记录证明的是「能装、能按名调用、能产出登记行」；上面 [`walkthrough-meeting-notes/`](walkthrough-meeting-notes/) 演示的是一件完整小任务从输入走到验收，样例由作者照方法写好，不是各家宿主的重新测试。

| 宿主 | 状态 | 怎么装（摘要） | 已验证的产出／范围 |
|---|---|---|---|
| Codex | 支持 | 本机包根：`codex plugin marketplace add "$(pwd)"` → `codex plugin add solo-to-team-skills@solo-to-team-skills`（本包自带 `.agents/plugins/marketplace.json`） | 登记行（装／配置＋按名调用已验） |
| WorkBuddy | 支持 | `~/.workbuddy/skills/`、项目 `.workbuddy/skills/` 或上传 zip | 登记行（装／配置＋按名调用已验） |
| DeepSeek Harness | 支持 | `.dsh/skills/`、`~/.dsh/skills/` 或 `.agents/skills/`（`dsh plugin add`≠装技能正文） | 登记行（装／配置＋按名调用已验） |
| Cursor | 支持 | `~/.cursor/skills/`；CLI `--trust`＝信任工作区，不是关安全 | 登记行（装／配置＋按名调用已验） |
| CodeBuddy | 支持 | `~/.codebuddy/skills/` 或项目 `.codebuddy/skills/` | 登记行（装／配置＋按名调用已验） |
| Grok Bot | 支持，需手动配置 | 对话里把 `SKILL.md` Save 为私有技能，再按名调用 | 登记行（装／配置＋按名调用已验） |
| Kimi Work | 支持 | `daimon-share/daimon/skills/`；本人在界面粘贴调用 | 登记行（装／配置＋按名调用已验） |
| 千问办公（QwenWork） | 支持 | `~/.qwenworkcn/skills/`；本人在界面粘贴调用 | 登记行（装／配置＋按名调用已验） |
| Claude Code | 结构已备，走通待补 | `.claude-plugin/` | 条件合适时再验证；未走通前不纳入首发支持 |
| 纯手工（记事本／表格） | 不用装 | — | 待补走通记录 |

**完整任务闭环**（产出真实成果→对照要求检查→验收）：上表「走通」一栏只记到登记行；另外，当前包上八家各有一例有限任务的验收记录（真实成果→对照要求检查→人工验收）：Codex 保留此前单独验证的一例，其余七家按同一会议转写题补验，部分宿主经受阻重跑或退回修订后才通过；不代表稳定性或所有任务都能做成，调用方式各家不同（有的由使用者本人在宿主里发出，有的命令行或代点），部分宿主未保留技能加载的原始轨迹；不表示每家四个技能都逐一被调用，也不证明效果。上面 [`walkthrough-meeting-notes/`](walkthrough-meeting-notes/) 是教学样例，不是实测记录。

- 容易混的：CodeBuddy ≠ WorkBuddy；千问办公 ≠ 通义灵码；Kimi Work ≠ Kimi Code CLI。Grok Bot 的「支持」只指这一款产品里的私有技能，不代表 Grok 其他客户端能同样装。
- Grok Bot 是这套方法最早练出来的地方；加载技能 ≠ 整套自动运行，定时、跨助手、交接靠宿主原有能力。
- 通义灵码、TRAE、Comate 等：尚未验证。
- 走通记录对外只留脱敏的方法级结论，不附内部编号。
