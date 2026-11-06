# 项目技能清单

本包为精选子集，固定于下列上游提交。`SOURCE-MANIFEST.json` 记录每个源文件路径和 Git blob SHA；`licenses/` 保留对应许可。技能内容来自上游，执行前请检查脚本与实际依赖。

| 来源 | 技能 | 提交 | 许可 |
| --- | --- | --- | --- |
| [Research-Paper-Writing-Skills](https://github.com/Master-cai/Research-Paper-Writing-Skills) | research-paper-writing | `77e7c2c1ba06f7d71844873147665437a03aac1b` | MIT |
| [Nature Skills](https://github.com/Yuan1z0825/nature-skills) | nature-data、nature-shared | `d774add241c65e89ed17a4da573b472b0972fd42` | Apache-2.0 |
| [Scientific Agent Skills](https://github.com/K-Dense-AI/scientific-agent-skills) | literature-review | `a25cf9ec00e2745d03f8704acf6f6919694ccd9a` | MIT |
| [中文科研 Academic Skills](https://github.com/zLanqing/codex-claude-academic-skills) | research-writing-skill | `7ed6377f0efb6a38951b48ef03b19d996e454b1f` | MIT |

这是精选安装，不代表上述仓库的全部技能已安装。`nature-shared` 为 Nature 技能共享资源。文献搜索需要联网；literature-review 的部分功能需要 Python、requests，PDF 导出需要 Pandoc 和 XeLaTeX；可选图像生成和搜索服务需要单独的账户或密钥。不要把密钥写入 Git。

其他来源暂未纳入：ARIS 的 Codex 工作流依赖共享参考、辅助脚本及审阅后端；[ARS-Codex](https://github.com/Imbad0202/academic-research-skills-codex) 声明为 CC BY-NC 4.0 大型套件，使用受到非商业条款约束；[claude-scholar](https://github.com/Galaxy-Dawn/claude-scholar/tree/codex) 需使用 Codex 分支并检查其安装器和配置；[Paper Craft Skills](https://github.com/zsyggg/paper-craft-skills) 的 README 声明 MIT，但 GitHub 元数据未识别独立许可文件，分发前需核对。这些项目尚未安装或测试。

将仓库克隆或打开为 Codex 工作目录后，在新会话查看技能列表并尝试调用；技能被发现不等于联网、程序依赖或结果已验证。ChatGPT 项目连接 GitHub 不保证将仓库技能自动注册到 ChatGPT 项目会话；实际可用性取决于运行环境及技能/插件安装方式。不要将公开仓库用于敏感研究材料。
