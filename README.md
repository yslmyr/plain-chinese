# plain-chinese

让 AI 用简明中文回答：先说重点，用日常用词和短句，给出清楚的操作步骤，同时保留必要的条件、风险和不确定性。

适用于中文问答、任务说明、进度汇报和错误解释。用户要求详细分析或完整内容时，仍应完整回答，不为简短而漏掉信息。

## 目录与规范

本仓库本身就是一个技能目录，符合 [Agent Skills 公开格式规范](https://agentskills.io/specification)：

```text
plain-chinese/
├── SKILL.md    # 技能入口：YAML 元数据和完整表达规则
├── README.md   # 仓库说明与安装方法
└── LICENSE     # 仓库许可证
```

- `SKILL.md` 是必需文件，包含 `name`、`description` 和 Markdown 正文。
- 技能目录名 `plain-chinese` 与 `name: plain-chinese` 一致；名称及描述符合规范要求。
- `scripts/`、`references/`、`assets/` 是可选目录。本技能只提供表达规则，不需要脚本、额外参考文件或素材。
- README 和许可证是允许的附加文件；无需再嵌套一层 `plain-chinese/`，也无需创建空目录。

格式符合规范不代表每个客户端都会自动发现技能。安装位置、加载方式和自动选择机制，以所用客户端的文档为准。

## 安装

1. 在客户端文档中确认技能目录的位置。
2. 将本仓库克隆到该目录下，保留文件夹名称 `plain-chinese`。PowerShell 示例（先替换路径）：

   ```powershell
   $skillsRoot = 'C:\你的客户端技能目录'
   git clone https://github.com/yslmyr/plain-chinese.git "$skillsRoot\plain-chinese"
   ```

3. 按客户端要求重新加载技能或开启新会话，确认技能列表中出现 `plain-chinese`。

也可以下载仓库后，把包含 `SKILL.md` 的文件夹复制到技能目录，命名为 `plain-chinese`。不要只复制 README，也不要保留下载包默认的 `plain-chinese-main` 文件夹名作为技能目录名。

## 使用

在支持技能调用的客户端中，明确要求加载 `plain-chinese`。例如：

> 请使用 plain-chinese 技能回答：先给结论，少用黑话，多步骤按编号说明。

具体调用语法由客户端决定；上面的自然语言示例不保证在所有客户端中自动触发加载。若客户端支持自动选择技能，元数据中的描述可帮助它识别适用场景。

加载后，技能主要引导助手：

- 先给答案、成果或阻碍，再补必要说明。
- 用常见词和短句，写清楚谁做什么、结果是什么。
- 多步骤按编号说明，每步安排一个主要动作。
- 删除套话和重复内容，保留条件、风险及不确定性。
- 如实报告进度和错误，不把尝试写成成功。

完整十节规则和改写示例见 [SKILL.md](SKILL.md)。这些规则不替代授权和安全要求，也不保证未加载技能的其他会话自动遵守。

## 许可证

许可证全文见 [LICENSE](LICENSE)（GNU General Public License，Version 3）。
