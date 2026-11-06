# GenDSM 核心科研 Skills 安装与验收

## 范围和来源

基于 `90ee538b317c4f8b4cdee974257ff1d732cc5542` 增量安装 24 个技能；保留原有 5 个，合计 29 个。所有新增技能目录按上游原样复制，逐文件 SHA-256、源路径、字节数和提交见 `CORE-SKILLS-MANIFEST.json`。上游许可证保存在 `licenses/core-*.txt`。

| 来源 | 固定提交 | 新增技能数 | 上游许可声明 |
| --- | --- | ---: | --- |
| [Supervisor-Skills](https://github.com/HKUSTDial/Supervisor-Skills) | `4bd3fef393e5ffc891c74309a5ef6c5ad3ad12c8` | 12 | 仓库 LICENSE 为 CC BY-NC-SA 4.0 |
| [Scientific Agent Skills](https://github.com/K-Dense-AI/scientific-agent-skills) | `a25cf9ec00e2745d03f8704acf6f6919694ccd9a` | 6 | MIT |
| [Nature Skills](https://github.com/Yuan1z0825/nature-skills) | `d774add241c65e89ed17a4da573b472b0972fd42` | 4 | Apache-2.0 |
| [AI Research Skills](https://github.com/Orchestra-Research/AI-Research-SKILLs) | `773a52944ba4747a18bd4ae9ade53fff041adcbc` | 2 | MIT |

**许可待澄清：** Supervisor 仓库许可证和 README 声明 CC BY-NC-SA 4.0，但若干 `SKILL.md` 的 frontmatter 写的是 CC-BY-4.0。原样保留两种声明，不将前者覆盖后者，也不自行认定冲突的法律效果；商业用途或再分发前应向上游澄清。注意非商业、署名和相同方式共享条款。其他来源的被引用第三方服务和资源可能有各自条款。

## 文件和依赖检查

- PASS：新增 24 个目录、248 个技能文件逐一与来源清单 SHA-256 一致；29 个 `SKILL.md` 的 YAML 均可解析且含非空 name、description。
- PASS：4 个 Nature manifest 中 24 个引用路径存在；新 Nature 技能与原 `nature-shared` 来自同一提交，且后者与上游对应目录一致。
- PASS：新技能 `SKILL.md` 中可静态识别的本地 `references/`、`scripts/`、`assets/`、`templates/`、`static/` 文件路径存在。此检查不证明所有动态路径或外部工具可用。
- PASS：drawio-reconstruction 引用的 5 个脚本均位于技能自身的 `scripts/`，没有发现其 `SKILL.md` 要求调用上游仓库根目录脚本；Pillow、Draw.io 等功能依赖须另行检查。
- PARTIAL：`scientific-critical-thinking` 的可选示意图示例引用 `scientific-schematics`，该技能未安装；图像生成功能不可据此认定可用。Supervisor 部分技能可选引用上游 handbook 2.3；需要时查看固定版本的上游 handbook。
- PARTIAL：experimental-design 本机存在 numpy、pandas，但 `pyDOE` 未发现；版本及完整环境未验证。网络检索、外部模型和服务、渲染及其凭据均须各自验证，未自动安装依赖或保存密钥。

## 只读烟雾检查

| 对象 | 状态 | 证据和范围 |
| --- | --- | --- |
| idea-evaluator | BLOCKED | 已读取指令与资源并通过静态检查；未在新 Codex 会话执行实际调用。 |
| deep-research | BLOCKED | 已检查配套参考资料；未执行外部检索或实际技能调用。 |
| experimental-design | PARTIAL | 上游 randomization.py 的合成数据示例执行成功；不代表完整实验设计功能或依赖验证通过。 |
| peer-review | PARTIAL | intake validator 的 `--help` 执行成功；未审阅论文或运行端到端工作流。 |
| nature-reviewer | BLOCKED | manifest 和引用文件检查通过；未在新 Codex 会话执行审稿工作流。 |
| 新 Codex 会话发现 | BLOCKED | 本机 `codex --version` 报 ENOENT：安装的 CLI 包缺少平台可执行文件；文件存在不等于技能已被发现。 |

没有运行科研训练、读取目标测试集或上传用户研究资料。真实文献核验、审稿、统计及实验结论均未执行。仓库技能供在该仓库工作目录运行的兼容 Codex 环境发现；ChatGPT 普通项目会话是否加载需另行核验。

`git diff --check` 报告 6 处上游原文件行尾空白，位于 drawio-reconstruction 的两个 README 及 nature-reviewer 的一份参考资料；为保留逐字节来源一致性，没有改写这些上游文件。项目自有文档无此问题。
