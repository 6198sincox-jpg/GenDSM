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

## GenDSM 核心科研技能增量

新增选题、文献、实验设计和审稿技能的冻结来源、许可证及验收限制见 [CORE-SKILLS-REPORT.md](CORE-SKILLS-REPORT.md)，逐文件哈希见 [CORE-SKILLS-MANIFEST.json](CORE-SKILLS-MANIFEST.json)。

## 第二批：nature-skills 扩展（18 项）

在原有 6 个 nature-* 技能基础上，补入 [Nature Skills](https://github.com/Yuan1z0825/nature-skills) 的其余 18 个可触发技能，固定于同一上游提交 `d774add241c65e89ed17a4da573b472b0972fd42`，许可 **Apache-2.0**（允许商用与再分发，需保留许可与署名；许可全文见 `licenses/core-nature-skills-v2.txt`）。

| 批次 | 技能 | 数量 |
| --- | --- | --- |
| 原有 | nature-data、nature-shared、nature-reviewer、nature-paper-xray、nature-statistics、nature-ref-verifier | 6 |
| 本批新增 | nature-figure、nature-polishing、nature-writing、nature-citation、nature-reader、nature-paper-trans、nature-paper-card、nature-response、nature-paper2ppt、nature-paper2word、nature-image2ppt、nature-paper-to-patent、nature-academic-search、nature-downloader、nature-literature-pipeline、nature-experiment-log、nature-proposal-writer、nature-social-science | 18 |

注意事项：

- 技能位于上游根级 `skills/`，而非 `.agents/skills/`；本仓库统一落到 `.agents/skills/`，目录结构原样保留。
- `nature-shared` 仍是共享依赖包，不独立触发。
- `nature-proposal-writer` 的 frontmatter 名称为 `researchwrite`，与目录名不一致，属上游现状，调用时以 frontmatter 为准。
- 按需依赖（未随仓库安装）：`nature-paper-to-patent` 需按其 `requirements.txt` 装包；`nature-academic-search` 的 MCP 服务需配置 `PUBMED_EMAIL`，Scopus/ScienceDirect 需本机凭据；`nature-downloader` 依赖浏览器登录态。凭据不得写入仓库。
- `nature-figure` 约占 34 MB，是本次体积增量的主要来源。

## PaperSpine：以安装器管理，不 vendoring

[PaperSpine5](https://github.com/WUBING2023/PaperSpine)（MIT，`licenses/core-PaperSpine.txt`）提供单个 `paper-spine` 技能，但**不适合以文件形式纳入本仓库**，原因有三：

1. 技能的 `references/installed-suite.json` 保存指向 `~/.paperspine5/.../installs/<build_id>` 的**绝对路径指针**，脱离本机即失效；
2. 技能依赖的套件含 vendored Python 运行时与二进制，本机安装后约 117 MB，超出仓库合理体积；
3. 其 `SKILL.md` 规定每次调用先执行 `scripts/paperspine_update.py --preflight --yes` 自更新整套 Web 与运行时，版本由上游决定，与"固定提交 + 逐文件哈希"的冻结原则不相容。

因此本仓库只记录来源与安装方式，不保存产物。安装命令（macOS / Linux）：

```bash
curl -sfL -o install.sh https://raw.githubusercontent.com/WUBING2023/PaperSpine/main/install.sh
sh ./install.sh --target codex
```

已在本机验证的版本为 `0.4.0-alpha.3`（build `w7p-macos-arm64-09137e38b749`）。安装后如需在其他技能宿主使用，可将 `~/.codex/skills/paper-spine` 整体复制到该宿主的技能目录，指针为绝对路径，复制后仍可解析。

已知限制：在 `LANG` 未设为 UTF-8 的环境下，安装器的 `awk` 解析会因 manifest 中的中文 `description` 报 `multibyte conversion failure`；可下载 manifest 后以 `--manifest <path>` 传入纯 ASCII 版本绕过。该问题已在 macOS 15.6 / BSD awk 上复现。
