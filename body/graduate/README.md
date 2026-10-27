# 多物理场仿真论文正文框架

当前主文件选择 `Degree=graduate`、`GradLevel=master`、`MajorFormat=cs`、`Language=chinese`。
`zjuthesis.tex` 经模板的 `\inputbody{content}` 加载本目录的 `content.tex`，无需调整主文件。

## 章节安排

| 文件 | 章节与用途 |
| --- | --- |
| `chapters/01-introduction.tex` | 绪论：两项研究问题、工作范围与组织结构 |
| `chapters/02-foundations.tex` | 相关研究与理论基础：装配、映射、热弹性与误差来源 |
| `chapters/03-parallel-assembly.tex` | 第一项研究：空间分割前驱图并行装配 |
| `chapters/04-adaptive-mapping.tex` | 第二项研究：局部误差选择、映射与虚功一致性校正 |
| `chapters/05-implementation.tex` | MPIS 数据结构、算法实现和耦合流程 |
| `chapters/06-experiments.tex` | 装配、解析场映射、热力响应、参数扫描和消融实验 |
| `chapters/07-conclusion.tex` | 总结、局限与后续研究 |
| `post/appendix.tex` | 符号、配置及实验复现资料的附录提纲 |

## 补写约定

- `% TODO：` 为写作提示，不显示在 PDF 中；当前文件是基本框架，不代表实验已经完成。
- 空节的 `\thesisdraftnote` 显示“本节内容待补充”，防止连续空标题形成不能分页的长块；补写该节正文时删除对应命令。提纲阶段使用 `\raggedbottom`，不把稀疏内容拉伸到整页；定稿时可移除这一行恢复模板默认页底对齐。
- 两条主线是系统装配和场间传递。第 3、4 章写方法与分析，第 5 章写工程实现，第 6 章统一写实验，避免重复。
- 依据 `HARNESS_ROOT/docs/thesis-proposal/多物理场第二创新点研究/` 的四份资料，并采用后续讨论确定的范围：当前线性四面体、节点标量/多分量场、稳态单向 Heat→Force 验证。
- 早期资料中的“独立二维原型”是选题阶段方案。正文需以实际完成的 MPIS 实现和实验记录说明工作，不直接照搬旧的实现状态描述。
- 空间分割前驱图、P1、投影、RBF 等已有技术必须说明来源；本人的改进和可验证贡献需单独界定。仅集成软件或运行案例不构成方法创新结论。
- 参考文献核查材料作为检索线索。正式引用前核对原文及书目信息，再写入 `body/ref.bib`；本次没有添加未经复核的引用条目。
- 图表、加速比、误差和结论等待实际数据补齐；不预设自适应方法优于所有基线。
- 摘要、致谢等前置内容位于 `page/graduate/`；主文件的题目、研究方向和提交日期仍需作者确定。

## 本地编译

按根目录 README 的要求，在论文根目录执行 `latexmk -xelatex -outdir=out zjuthesis.tex`。
需要 XeLaTeX、latexmk 及模板依赖。编译产物放入已有忽略规则覆盖的 `out/`。

原始模板已在 Git 提交 `5f5afa4` 保存；可使用 `git show 5f5afa4:body/graduate/content.tex` 查看原始正文示例。
