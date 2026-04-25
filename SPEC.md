# ZJE Thesis Studio — 规格说明书

本文档定义 SKILL.md 之外的结构化规格：数据模型字段、Schema 定义、文件更新规则。

---

## 一、数据模型字段

### 1.1 project_manifest.md

| 字段 | 说明 |
|------|------|
| `thesis_title_en` | 英文论文题目 |
| `thesis_title_zh` | 中文论文题目 |
| `supervisor` | 指导教师 |
| `author` | 作者姓名 |
| `mode` | 当前写作模式（A/B/C/D/E） |
| `ibms10008_status` | IBMS10008 完成状态 |
| `preview_status` | Project Preview 完成状态 |
| `assets` | 已有资产列表 |
| `missing` | 缺失项列表 |

### 1.2 thesis_master_index.md

| 字段 | 说明 |
|------|------|
| `outline` | 两部分大纲（章节树） |
| `chapter_status` | 各章节完成状态 |
| `glossary` | 术语表 |
| `open_issues` | 开放问题 |

### 1.3 Asset Manifest（figures/tables/code/data）

| 字段 | 说明 |
|------|------|
| `asset_id` | 唯一标识（如 `FIG-01`） |
| `description` | 描述（用于占位符匹配） |
| `file_path` | 资产文件路径 |
| `caption_zh` | 中文图题/表题 |
| `caption_en` | 英文图题/表题 |
| `notes` | 备注 |

### 1.4 project_state.json

Schema 定义在 `assets/project_state.schema.json`，核心字段：

| 字段 | 说明 |
|------|------|
| `version` | Schema 版本 |
| `project_path` | 项目根目录 |
| `generated_at` | 生成时间戳 |
| `chapters` | 各章节状态对象 |
| `figures` | 图片资产清单 |
| `tables` | 表格资产清单 |
| `references` | 参考文献清单 |
| `working_xml_path` | 当前工作 XML 路径 |

---

## 二、写作模式

| 模式 | 描述 |
|------|------|
| Mode A | 英文论文 → 中文论文迁移（核心） |
| Mode B | 填写 Part 2 模板（文献综述 + 开题报告 + 外文翻译） |
| Mode C | 填写附件表格（附件1~11） |
| Mode D | 参考文献与资产管理 |
| Mode E | 三版本 Word 输出 |

---

## 三、文件更新规则

| 规则 | 说明 |
|------|------|
| 占位符标签 | 新增占位符使用 `[[FIG:]]`、`[[TBL:]]`、`[[EQ:]]`、`[[REF:]]` |
| 润色保护 | 润色内容时不得删除或重写已有占位符 |
| 禁止硬编码 | 不得在正文中硬编码图号/表号 |
| 快照保留 | 写回 Word 前保留时间戳快照 |
| 模板保护 | 禁止修改 `examples/` 中的教务处原始模板 |

---

## 五、Project Preview 评分标准

### 评分结构

Project Preview 包含两部分，各占不同权重：

| 组成部分 | 说明 | 权重 |
|----------|------|------|
| Literature Review | 1000字英文文献综述 | 2.5 ZJU 学分 |
| Research Proposal | 1000字英文开题报告 | 10 UoE 学分 |

### 评分等级参考

| 等级 | 典型描述 |
|------|---------|
| 86–90 (Excellent) | 所有评分要素均出色完成，仅有微小组织或表达问题 |
| 80–85 (Very Good) | 整体优秀，包含一两个组织、结构或内容上的小问题 |
| 70–79 (Good) | 整体良好，实验技术和使用理由清晰 |
| 60–69 (Satisfactory) | 实验技术和理由说明清楚，可能存在理解上的小问题 |
| 50–59 (Pass) | 达到基本要求 |

### 评分要素（Literature Review）

| 要素 | 说明 |
|------|------|
| 逻辑结构 | 围绕核心科学问题（paradox/motivation）组织，而非堆砌事实 |
| 论证力度 | 清晰论证为何现有方法不足，为新框架提供依据 |
| 文献质量 | 引用前沿文献（近年顶刊），展示领域前沿理解 |
| 可读性 | 有背景概述帮助读者理解，逐步引入核心概念 |

### 评分要素（Research Proposal）

| 要素 | 说明 |
|------|------|
| 可行性 | 明确分离核心阶段与扩展阶段，在8周时限内可完成 |
| 技术论证 | 清楚解释为何现有技术（DEG等）不足，替代方案的必要性 |
| Gantt Chart | 时间线详细合理 |
| Contingency | 对数据整合、样本量等技术难点有备选方案 |
| 动物模型 | 说明动物模型选择依据 |
| 样本量论证 | scRNA-seq等高成本技术需说明样本量合理性 |

### Sample Thesis 评分示例

| 项目 | 得分 | 亮点 | 改进点 |
|------|------|------|--------|
| Literature Review | 88 | 用生物学悖论（DQ vs. Senescence）结构化；引用前沿（2024/2025）；指出静态 aging clock 的局限性 | 开头缺 aging 对肌肉影响的背景；entropy 概念引入太晚 |
| Research Proposal | 86 | Phase 1/2 分离策略好；DEG vs. entropy velocity 对比清晰；Gantt chart 详细 | 缺跨平台数据整合 contingency；CIBERSORTx 用途未说明；动物模型和样本量缺论证 |

---

## 六、脚本能力边界

| 脚本 | 能力 |
|------|------|
| `init_thesis_workspace.py` | 创建项目目录结构 |
| `build_new_docx.py` | 从 XML 生成 Word |
| `reverse_parse_docx.py` | 从 Word 提取回 Markdown/XML |
| `apply_markdown_to_xml.py` | 将 Markdown 章节写入工作 XML |
| `parse_template_xml.py` | 解析 ZJE 模板结构 |
| `embed_figures_docx.py` | 插入图片到 DOCX |
| `validate_xml_docx.py` | 验证 DOCX 结构完整性 |
| `reference_tools.py` | 格式化参考文献（GB/T 7714） |
| `flat_opc_converter.py` | DOCX ↔ OPC XML 互转 |
| `word_xml_core.py` | 共享 XML/Word 工具 |

**不提供**：自动翻译、自动内容生成（Mode A/B 内容由用户提供）
