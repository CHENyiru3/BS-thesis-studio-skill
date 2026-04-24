---
name: zje-thesis-studio
description: 用于浙江大学爱丁堡大学联合学院（ZJE）本科毕业论文（设计）的写作与格式管理。支持从英文毕业论文（IBMS10008课程）迁移为中文论文、填写教务处附件模板（附件1~17）、管理参考文献与图表资产、生成符合ZJE规范的中文论文 Word 文档。
---

## UTF-8 说明

本 Skill 所有文件均为 UTF-8 编码。如遇中文乱码，用以下方式重新读取：

```bash
python -c "from pathlib import Path; import sys; sys.stdout.reconfigure(encoding='utf-8'); print(Path('SKILL.md').read_text(encoding='utf-8'))"
```

---

# ZJE 本科毕业论文 Studio

浙江大学爱丁堡大学联合学院（ZJE）本科毕业论文写作与格式管理 Skill。

## ZJE 特殊性：一句话说明

**ZJE 学生先在 IBMS10008 课程中完成英文毕业论文，再将英文论文迁移为中文论文，连同 Project Preview 的文献综述和开题报告，一起填入教务处指定的官方模板，最终提交三个版本（查重电子版 / BB电子版 / 纸质存档版）。**

本 Skill 围绕这个核心流程设计，涵盖英文论文解析、中文迁移写作、Part 2 模板填写、附件表格填写、参考文献管理、图表资产整理和合规 Word 输出。

---

## 一、ZJE 论文结构总览

ZJE 本科毕业论文（设计）由两大部分组成：

### 第一部分：毕业论文（设计）
前置部分（无页眉，页脚为罗马数字页码）：
1. 大封面（附件8第1页）
2. 承诺书（附件6）
3. 致谢
4. 中文摘要
5. 英文摘要（Abstract）
6. 目录

正文部分（奇数页眉=论文名居右，偶数页眉="浙江大学本科生毕业论文（设计）"居左，页脚=阿拉伯数字）：
7. 第一部分封面（附件8）
8. 正文 + 作者简历

### 第一部分与第二部分之间
9. 任务书（附件1）
10. 毕业论文考核表（附件11）

### 第二部分：文献综述和开题报告
11. 第二部分封面1（附件8）
12. 第二部分封面2（附件2第1页）
13. 指导教师对文献综述和开题报告的具体要求（附件2）
14. 目录（罗马页码）
15. 文献综述
16. 开题报告
17. 外文翻译
18. 外文原文（不编目录页码）

### 尾部附件（纸质版装入，电子版不含）
19. 文献综述和开题报告考核表（附件3）
20. 中文查重报告（附件17）
21. 专家评阅意见表（附件9）
22. 现场答辩记录表（附件10，答辩现场填写）

### 三个版本的区别

| 组成部分 | 查重电子版 | BB提交电子版 | 纸质存档版 |
|----------|-----------|-------------|-----------|
| 大封面 | ✓ | ✓ | ✓（单面） |
| 承诺书 | **✗** | ✓（可不签） | ✓（单面·须签字） |
| 致谢 | ✓ | ✓ | ✓（单面） |
| 摘要（中/英） | ✓ | ✓ | ✓（各1页·单面） |
| 目录 | ✓ | ✓ | ✓（单/双面） |
| 第一部分封面 | ✓ | ✓ | ✓（单面） |
| 正文 | ✓（不含参考文献和简历） | ✓ | ✓（双面） |
| 参考文献 | **✗** | ✓ | ✓（双面） |
| 作者简历 | **✗** | ✓ | ✓（双面） |
| 任务书（附件1） | **✗** | **✗** | ✓（单面） |
| 考核表（附件11） | **✗** | **✗** | ✓（单面） |
| 第二部分正文 | ✓ | ✓ | ✓（双面） |
| 考核表（附件3） | **✗** | **✗** | ✓（单面） |
| 查重报告 | **✗** | **✗** | ✓（单面） |
| 专家评阅意见 | **✗** | **✗** | ✓（单面） |
| 答辩记录表 | **✗** | **✗** | ✓（单面） |

---

## 二、ZJE 写作模式

### 模式A：英文论文 → 中文论文迁移（最核心）

适用于学生已完成 IBMS10008 英文毕业论文，需要迁移为中文论文第一部分。

工作步骤：
1. 解析英文论文：提取标题、摘要、章节结构、正文内容
2. 填写第一部分模板：封面、承诺书、致谢、中文摘要（翻译英文Abstract）
3. 迁移正文：将 Introduction / Methods / Results / Discussion / Conclusion 翻译为中文，填入附件8第一部分模板
4. 整理参考文献和作者简历（用于 BB 电子版和纸质版，不含于查重版）

**注意**：英文论文的 Acknowledgement 翻译为中文后填入致谢；英文摘要（Abstract）原文保留为英文摘要；中文摘要为300–600字。

### 模式B：填写 Part 2 模板

适用于填写第二部分（文献综述 + 开题报告 + 外文翻译）。

工作步骤：
1. 从 Project Preview 课程材料中提取文献综述和开题报告内容
2. 填入附件2第二部分模板（英文原文，不翻译）
3. 选取一篇与毕设课题相关的学术研究论文（非综述、非会议论文），自行翻译为中文，填入外文翻译部分
4. 外文原文附在最后（文字粘贴或截图均可）

### 模式C：填写附件表格

适用于填写附件1~11中的各类表格。

关键原则：
- **Dissertation / Preview / Oral Presentation 的 feedback**：原文粘贴，不翻译
- 任务书内容：从 Project Description 或 "Guidance and Agreement for ZJE Year 4 External Projects Supervisors" 文件中摘取英文原文填入
- 所有签名：电子签或打印后手签均可

### 模式D：参考文献与资产管理

适用于管理参考文献、整理图表、处理公式和代码资产。

### 模式E：三版本 Word 输出

适用于最终生成合规的 Word 文档，包括查重版、BB电子版、纸质版的封面/正文/附件。

---

## 三、第一次问诊

首次使用本 Skill 时，先确认以下事实：

### 英文论文元数据
- 英文论文题目（IBMS10008 课程标题）
- 导师姓名
- 作者姓名
- 英文论文完成状态：已提交 / 进行中 / 未开始
- Abstract 内容是否已定稿

### 中文论文目标
- 中文论文题目（是否已翻译，或需辅助翻译）
- IBMS10008 和 Preview 课程各自的完成进度
- 当前最紧迫的任务：迁移英文论文 / 填写 Part 2 / 填写附件表格

### 已有资产
- 英文论文 Word 文件路径
- Preview 课程材料路径
- 参考文献列表（是否有 .bib 或 JSON 文件）
- 图片、表格、代码、数据文件

### 模板来源
- 教务处官方模板优先，默认使用 `examples/` 中的附件模板
- 格式规范优先参考 `examples/中文论文材料顺序-全局索引.xlsx`

---

## 四、目录结构

```
BS-thesis-studio-skill/
├─ SKILL.md                        ← 本文件
├─ README.md                       ← 项目说明
├─ assets/
│  └─ project_state.schema.json    ← 项目状态 JSON Schema
├─ examples/                       ← ZJE 教务处官方材料（只读·不修改）
│  ├─ 中文论文材料顺序-全局索引.xlsx  ← 全局索引（优先阅读）
│  ├─ 浙江大学本科毕业论文编写规则.pdf
│  ├─ 附件1-毕业论文任务书-空白表格.docx
│  ├─ 附件1-毕业论文任务书.pdf
│  ├─ 附件2-第二部分模板-文献综述开题报告外文翻译.doc
│  ├─ 附件2-指导教师对文献综述和开题报告的具体要求-格式说明.pdf
│  ├─ 附件2-第二部分封面-格式说明.pdf
│  ├─ 附件3-文献综述和开题报告考核表-空白表格.docx
│  ├─ 附件3-文献综述和开题报告考核表.pdf
│  ├─ 附件6-承诺书-空白表格.docx
│  ├─ 附件8-第一部分模板-毕业论文主体.doc
│  ├─ 附件8-大封面-格式说明.pdf
│  ├─ 附件8-第一部分封面-格式说明.pdf
│  ├─ 附件8-第一部分封面+大封面-格式参考.pdf
│  ├─ 附件8-第二部分封面1-格式说明.pdf
│  ├─ 附件9-专家评阅意见表-空白表格.doc
│  ├─ 附件9-专家评阅意见表.pdf
│  ├─ 附件10-现场答辩记录表-空白表格.doc
│  ├─ 附件10-现场答辩记录表-空白表格.docx
│  ├─ 附件11-毕业论文考核表.pdf
│  ├─ 附件17-中文查重报告-打印说明.pdf
│  ├─ 往届学生优秀论文案例-参考.pdf
├─ references/
│  ├─ writing_workflow.md       ← ZJE 写作工作流（问诊、模式、大纲）
│  ├─ placeholders.md          ← 占位符规范与 ZJE 格式说明
│  ├─ reference_rules.md        ← 参考文献规范（GB/T 7714）
│  └─ xml_mapping_spec.md       ← Word/XML 映射规范
├─ scripts/
│  ├─ init_thesis_workspace.py
│  ├─ flat_opc_converter.py
│  ├─ parse_template_xml.py
│  ├─ generate_planning_files.py
│  ├─ reverse_parse_docx.py
│  ├─ apply_markdown_to_xml.py
│  ├─ build_new_docx.py
│  ├─ embed_figures_docx.py
│  ├─ validate_xml_docx.py
│  ├─ reference_tools.py
│  └─ word_xml_core.py
└─ templates/
   ├─ project_manifest.md
   ├─ thesis_master_index.md
   ├─ figures_manifest.md
   ├─ tables_manifest.md
   ├─ code_manifest.md
   └─ data_manifest.md
```

---

## 五、阶段执行表

| 阶段 | 先阅读 | 生成或更新 | 脚本命令 |
|------|--------|-----------|---------|
| 0. 判断状态 | 项目目录、`00_project/`、`09_state/` | 判断是新项目还是续写项目 | 无 |
| 1. 初始化工作区 | `examples/` 附件模板、`examples/中文论文材料顺序-全局索引.xlsx` | 在论文项目文件夹内生成目录结构 | `python <skill_dir>/scripts/init_thesis_workspace.py .` |
| 2. 引用已完成的翻译 | `03_chapters/` 中的已有章节 | 确认章节标题和格式并更新 `00_project/` 中的索引 | 手动整理 |
| 3. 填写 Part 2 模板 | `examples/附件2-第二部分模板-文献综述开题报告外文翻译.doc`、`examples/第二部分正文编写说明-文献综述开题报告外文翻译规则.pdf` | `03_chapters/part2_lit_review.md`、`03_chapters/part2_proposal.md`、`03_chapters/part2_translation.md` | 无脚本·手动填写 |
| 4. 填写附件表格 | `examples/` 对应附件文件 | 各附件填好的 .docx 版本 | 无脚本·手动填写 |
| 5. 参考文献处理 | `references/reference_rules.md`、`08_refs/` | 规范化引用占位符、参考文献表 | `python <skill_dir>/scripts/reference_tools.py format <refs.json> --style "GB/T 7714"` |
| 6. 图表资产整理 | `04_figures/`、`05_tables/` manifest | figures_manifest.md、tables_manifest.md 更新 | 无脚本·手动整理 |
| 7. 生成 Word | `09_state/current_working.xml` | `10_output/thesis_draft_v1.docx` 或指定文件名 | `python <skill_dir>/scripts/build_new_docx.py . --name <output.docx>` |
| 8. 校验输出 | `09_state/current_working.xml`、`10_output/` | 确认结构正确、DOCX 可重建 | `python <skill_dir>/scripts/validate_xml_docx.py .` |

---

## 六、目录职责

- `00_project/project_manifest.md`：英文论文元数据、中文论文目标、当前进度、已有资产、缺失项、关键决策
- `00_project/thesis_master_index.md`：两大部分大纲、章节状态、术语表、开放问题
- `03_chapters/`：中文论文章节（致谢、摘要、引言、材料与方法、结果、讨论、结论）
- `04_figures/figures_manifest.md`：图片资产清单
- `05_tables/tables_manifest.md`：表格资产清单
- `06_code/code_manifest.md`：代码资产清单
- `07_data/data_manifest.md`：数据资产清单
- `08_refs/`：参考文献与文献笔记
- `09_state/project_state.json`：结构化项目状态
- `09_state/en_parse_report.md`：英文论文解析报告（可选）
- `10_output/`：最终生成的 DOCX（按版本命名）

---

## 七、查重注意事项

- **查重地址**：http://check.cnki.net/pmlc/ → 学生入口
- **用户名**：学号；**密码**：`zje`（小写）+ 身份证后8位（第9位 X 大写）
- **格式**：必须用 Office Word 或 WPS Word，**禁止 PDF**
- **查重版包含**：大封面、致谢、目录、中英文摘要、正文（不含参考文献和简历）
- **查重版不含**：承诺书、参考文献、个人简历
- **通过标准**：≤ 10%，原则上有且仅有一次机会

---

## 八、环境要求

- Python 3.10+
- 依赖：`lxml`
- LibreOffice（用于 .doc 文件转 .docx）

```bash
pip install lxml
```

---

## 九、安全规则

- 不覆盖 `examples/` 中的原始教务处文件
- 每次写回 XML 前保留时间戳快照
- 对未确认的数据、结论、文献保持保守表达
- 生成最终 DOCX 前须用户确认内容
