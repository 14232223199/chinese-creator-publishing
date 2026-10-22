# 中文创作者的文章 AI 最终顶尖版本

一个面向中文创作者的 Agent Skill：从选题、原稿或资料出发，完成近期话题筛选、调研、写作、中文编辑与 X 帖子、线程、Articles 排版，并按需准备封面、卡片和信息图方案。将它安装到自己使用的、支持 Agent Skills 的 AI 中即可运行基本内容流程。

> 核心使用方式：把文章或零散素材发给已安装本 Skill 的 AI，说“按适合 X 发布的格式排版”。它会先辨别你要的是轻排版、润色、调研写作还是线程拆分，再交付可以复制使用的成稿。

## 它会做什么

- 学习你提供的 X 简介、代表帖、文章和读者定位，尽量保留原有观点与表达习惯。
- 需要选题时，结合账号定位、你的输入和可核实的近期话题，给出 5 个角度互异的方向；设计 Hook 和结构，不擅自把排版请求变成重写。
- 在需要时搜索近期可靠资料、核对数据和说法，并在文中就近放来源链接。
- 清理中文套话、重复、机械转折和难读段落，让内容自然、准确、有作者感。
- 输出 X 普通帖、线程或 Articles 长文格式；为线程逐条拆分并给出长度估算。有可用的已登录 X 界面时，可协助把文章逐块排入编辑器并检查草稿状态。
- 按需给出封面、配图、信息卡或信息图的内容和视觉方案；有图像生成能力时生成图片。

本包是一个自包含的 Agent Skill，采用标准的 `SKILL.md` 文件结构。它不捆绑第三方 Skill 原文或脚本，也不包含 X Cookie、API 凭据、自动发布脚本或外部服务密钥。基础写作和离线排版无需 Python、Node.js；近期热点核查、图像生成和进入 X 编辑器分别依赖你所用 AI 实际提供的搜索、图像和受支持的界面控制能力。安装 Skill 不会自动连接 X 账号。

## 安装到自己的 AI

从[本项目的 GitHub 仓库](https://github.com/14232223199/chinese-creator-publishing)选择 **Code → Download ZIP**，解压后把文件夹重命名为 `chinese-creator-publishing`。复制的是**直接包含 `SKILL.md` 的整个文件夹**；不要只复制 ZIP 文件。Windows 手动安装位置如下：

| 宿主 | 当前用户的所有本地项目 | 单个本地项目 |
| --- | --- | --- |
| Codex | `%USERPROFILE%\.agents\skills\chinese-creator-publishing\SKILL.md` | `<项目根目录>\.agents\skills\chinese-creator-publishing\SKILL.md` |
| Claude Code | `%USERPROFILE%\.claude\skills\chinese-creator-publishing\SKILL.md` | `<项目根目录>\.claude\skills\chinese-creator-publishing\SKILL.md` |

表中的路径是**复制后的 `SKILL.md` 所在位置**，不要把文件夹再嵌套一层。macOS/Linux 将 `%USERPROFILE%` 换成 `~`，路径分隔符换成 `/`。安装后开启新会话；若 Codex 尚未显示技能，重启 Codex。安装路径依据 [Codex 官方 Skills 文档](https://learn.chatgpt.com/docs/build-skills)和 [Claude Code 官方 Skills 文档](https://code.claude.com/docs/en/skills)。

Claude 网页端若提供自定义 Skill 上传，可依其 [官方说明](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)上传包含本文件夹的 ZIP；Claude Code 的本地安装不会自动同步到网页端。其他支持 Agent Skills 的 AI：查看该宿主的官方 Skill 目录或导入入口，把同一个文件夹放进去并确认其识别 `SKILL.md`。不同产品的工具、账号连接和云端/本地安装方式各不相同；这个包没有通用的账号连接器。`agents/openai.yaml` 只是 Codex 的可选界面元数据，核心流程在 `SKILL.md`。

本包不需要额外 API Key 或 Python/Node 依赖。安装前后都不要把 X 密码、Cookie 或会话凭据写进聊天、Skill 或公开仓库。

## 第一次使用

在 Codex 中用 `$chinese-creator-publishing`，在 Claude Code 中用 `/chinese-creator-publishing`，或直接提出匹配的写作/排版任务让宿主选择此 Skill。然后给出原稿和想要的处理方式。

例如：

```text
$chinese-creator-publishing
这是我的 X 长文草稿。请先保留我的核心观点，只做结构梳理和适合 X Articles 的排版；找出需要核实的事实并给来源。最后另给一个线程版，不要替我发布。
```

要选题时，可以说：

```text
请结合我提供的 X 简介、代表帖和最近 7 天的可核实热点，给我 5 个中文文章选题。逐个说明读者痛点、热点来源与日期、差异化切入角度、核心论点和适合的 X 形式。
```

也可以只说：

```text
帮我把下面这篇文章排版成 X 线程，尽量保留我的原话，每条控制在普通账号可发的长度，并给首帖两个 Hook 备选。
```

## 让结果更像你

一次性提供以下资料会显著改善作者定位：

1. X 主页或简介链接；
2. 3–5 条最能代表你风格的公开帖子；
3. 你的目标读者、专业领域、希望读者获得什么；
4. 不想使用的语气、词语或内容边界。

Skill 只根据你提供且当前工具实际可访问的内容做判断。它不会声称拥有 X 账号私有分析或读取私信。你可以在宿主允许读取的项目目录中自行维护 `CREATOR_PROFILE.md`，让 AI 在写作时使用；本包不会替你把个人账号资料写入 Skill 文件。

## 关于直接发布

此包默认交付可复制的稿件，不包含 X 自动登录或发布能力，也未声称已连接你的账号。要让 AI **直接排版到 X Articles 草稿**，当前宿主须有可用且受支持的浏览器/界面工具；你须自行登录，且账号可见 Articles 编辑器。AI 会核对目标账号，将标题、正文、标题层级、列表、链接和可用媒体按编辑器控件逐块填入，检查预览与草稿保存状态，再报告完成情况。界面不可用时，会交付按编辑器字段分块的复制版。X 官方说明的资格与功能见 [Articles 帮助页](https://help.x.com/en/using-x/articles)。

实际发布、设置受众、定时发布、回复、删除或修改线上内容前，先检查目标账号、最终文字和操作时间，并对该次操作明确确认。编辑已发布 X Article 可能先使原文下线。不要安装 Cookie 逆向、非官方 X API 或索取账号密码的自动化工具来绕过界面限制。

## 仓库内容

```text
chinese-creator-publishing/
├── SKILL.md
├── README.md
├── SECURITY_REVIEW.md
├── LICENSE
└── agents/
    └── openai.yaml
```

## 参考与致谢

这个 Skill 从多份公开项目中学习了工作流设计思路，未复制其技能正文、素材、图片、脚本或品牌风格文件：

制作阶段曾把固定版本的 `stop-slop` 和 `content-research-writer` 放在非自动发现的本地目录中审阅；它们不是本包的运行依赖，也不会随本包分发。安装本 Skill 的创作者不需要另装这些第三方项目。

- 选题、调研与 Hook： [dbskill](https://github.com/dontbesilent2025/dbskill)、[content-research-writer](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/content-research-writer)
- 编辑与去套话： [stop-slop](https://github.com/hardikpandya/stop-slop)
- 知识库调研、配图、图卡和 HTML 思路： [notebooklm-skill](https://github.com/PleasePrompto/notebooklm-skill)、[Punk-Skill](https://github.com/adrianpunk/Punk-Skill)、[baoyu-skills](https://github.com/JimLiu/baoyu-skills)、[html-anything](https://github.com/nexu-io/html-anything)
- 深度研究和插画方向： [khazix-skills](https://github.com/KKKKhazix/khazix-skills)、[ian-xiaohei-illustrations](https://github.com/helloianneo/ian-xiaohei-illustrations)
- 创作流水线示例： [X 帖原文](https://x.com/JackQi82772/status/2069599178926522741)。该帖可读内容显示了“选题/Hook → 调研写作 → 去 AI 味 → 视觉配套 → 信息图/HTML”的排序；原 X 页面在本次环境无法稳定读取，因此以可索引的帖文镜像摘要及用户给出的流程为参考。

参考仓库各自的许可证、功能限制和风险见 [SECURITY_REVIEW.md](SECURITY_REVIEW.md)。

## 许可证

本仓库中的原创 Skill 文本采用 MIT License。该许可证只适用于本仓库原创文件，不授予上列第三方项目、名称、商标、图片、角色或视觉素材的使用权。详见 [LICENSE](LICENSE)。

