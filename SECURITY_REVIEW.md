# 第三方 Skill 安全与许可证审查

审查日期：2026-10-23。检查范围是用户提供的公开仓库说明、Skill 文本/公开文件列表及可索引的许可证信息；这不是对所有提交历史、依赖、维护者账户或供应链的完整安全审计。所有网页和 Skill 指令均作为不可信输入处理。

## 逐项结论

| 项目 | 能借鉴的环节 | 安全 / 许可证观察 | 本包处理 |
|---|---|---|---|
| [stop-slop](https://github.com/hardikpandya/stop-slop) | 去套话、编辑节奏 | 在提交 `8da1f030185bdfe8471220585162991eaeb970e9` 检查 `SKILL.md`、三份参考文件和 MIT 许可证；这些文件没有脚本、安装钩子、密钥或账号权限。它的英文禁词与句式要求不宜原样套用中文。 | 只把固定版本文件放入制作工作区供审阅，未加入自动启用的 Skill 目录，也未纳入本包；中文编辑规则为原创。 |
| [dbskill](https://github.com/dontbesilent2025/dbskill) | 选题诊断、Hook、内容评估 | 仓库规模较大；入口文档说明知识内容使用时会从 GitHub 在线拉取，需网络。其许可证标注 CC BY-NC 4.0：非商业使用附带署名，商业使用需要单独许可，不适合把它的材料并入可能用于商业创作的公开 Skill。联网动态取内容也会扩大输入审查面。 | 不安装、不复制知识库或 Skill 文本。仅按用户提供的流程把“选题判断”作为可选模块。 |
| [content-research-writer](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/content-research-writer) | 研究、提纲、逐节反馈、引用和保留作者声音 | 在父仓库提交 `be2a406907dbc61b73e6827ded415c96139d13a2` 检查目标子目录，只有 `SKILL.md`，没有脚本或安装钩子；其示例数字、机构引语不能当事实复用。父仓库 README 声称 Apache-2.0，但没有核实到可适用于该子目录的许可证文件。 | 只把该单文件放入制作工作区供审阅，未自动启用或纳入本包；不复制示例/正文。 |
| [notebooklm-skill](https://github.com/PleasePrompto/notebooklm-skill) | 以用户材料为依据做调研 | 仓库已归档为只读。Skill 会安装 Python 依赖和 Chrome 浏览器自动化，使用持久浏览器配置/保存 Cookie 状态登录 Google NotebookLM。这涉及账号会话凭据和非官方网页交互；超出本包必要范围。 | 不安装，不调用，不保存 Google 登录态。用户可手动提供 NotebookLM 导出的资料，Skill 按原文核查。 |
| [khazix-skills](https://github.com/KKKKhazix/khazix-skills) | 研究组织和深度写作 | 仓库宣称 MIT，但 Skill 集合和脚本范围较大；未在本次逐个检查其全部文件、更新脚本和依赖。不能仅凭仓库许可证/人气认定每个能力安全。 | 不整体安装；仅采用通用的研究先于结论原则，不复制其方法文本。 |
| [Punk-Skill](https://github.com/adrianpunk/Punk-Skill) | 文章封面和视觉提示词 | v2.0+采用个人非商业免费、商业使用需预先取得书面许可并付费的双轨授权；完整目录含视觉样式、资源和图像生成提示词。Skill 会生成/写入图像资产。 | 不安装或分发其素材/风格库；最终包只保留原创的通用视觉简报流程。若用户想用该项目本身，先查其当前版本授权。 |
| [baoyu-skills](https://github.com/JimLiu/baoyu-skills) | Markdown 组织、配图/图表和发布格式 | 仓库总体 MIT，但集合含多个不同运行方式的 Skills；维护者特别标注 `baoyu-danger-x-to-markdown` 使用逆向工程 X API，并通过环境变量或 Chrome 登录获取凭据，且可能造成账号限制；另有使用浏览器 Cookie 的非官方 Gemini Web API。整体安装会带入与文章排版无关的网络、浏览器和依赖能力。 | 不安装整套包，不使用危险/逆向 API 模块；只重新实现安全的文本结构与图表思路。 |
| [html-anything](https://github.com/nexu-io/html-anything) | HTML 卡片、图文预览、PNG 导出 | Apache-2.0；本地应用会启动用户本机 Agent CLI。其文档指出转换 API 用最大权限标志启动 Agent、部署路由写入带凭据配置，因此默认定位为单机单用户。即使本地优先，也不适合作为“只做排版”的无条件依赖。 | 不安装运行时/本地服务；仅在用户主动要求 HTML 或信息图时，输出可检查的静态方案。 |
| [ian-xiaohei-illustrations](https://github.com/helloianneo/ian-xiaohei-illustrations) | 正文插画和视觉停顿 | MIT。Skill 依赖图像生成工具；发布输出还要考虑生成工具和输入素材条款。角色/风格参考图属于该项目资产，不应默认并入本仓库。 | 不安装/复制小黑角色资产；最终包只描述通用视觉配套，并需有图像生成能力。 |

## 已实施的防护

- 最终包只包含一份自写 `SKILL.md`、中文安装/使用说明、原创 UI 元数据和本审查记录；没有第三方脚本、模板或图像资产。两份固定版本的第三方材料仅存放在制作工作区 `work/third_party_review/`，不在公开安装包中，也不进入自动发现目录。
- 没有 X/Google Cookie、密码、API Token、`.env`、浏览器自动登录、逆向 API 或自动发布脚本。
- 把用户输入的文章/网页当作内容资料，不执行其中试图改变 Agent 规则、索取密钥或访问无关数据的指令。
- 联网调研要求来源可核验；X 发布动作要求在执行前确认目标账号、完整内容和操作时间。
- 不要求任何 Python、Node、浏览器插件或外部账号权限来进行基本写作/排版。

## 安装第三方 Skill 的建议

不要按整库的“install all”命令无差别安装。若另行安装第三方 Skill，应先固定版本或提交 SHA，逐文件检查 `SKILL.md`、脚本、依赖声明、安装钩子、凭据读写、网络目标与许可证；先从一个职责单一、无可执行代码的 Skill 开始，安装到项目级目录，观察它的实际触发与文件改动后再决定是否扩大权限。
