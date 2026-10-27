# 本地计算机专业硕士模板与排版修正

## 模板选择

使用上游已有的 `MajorFormat=cs`，保留 `Degree=graduate`、`GradLevel=master` 及作者已有的其他个人设置。

上游 `config/format/major/cs/heading.tex`、`fonts.tex` 等文件的部分设置仅在 `GradLevel=doctor` 时生效。
硕士继承通用研究生样式是当前上游的实际行为；本地没有通过切换学位或套用博士分支来改变硕士格式。
这次修正依据上游模板配置，不代表对学校最新提交规范作了认证。

参考：

- [上游使用手册](https://github.com/TheNetAdmin/zjuthesis/blob/master/docs/usage.md)
- [计算机专业标题配置](https://github.com/TheNetAdmin/zjuthesis/blob/master/config/format/major/cs/heading.tex)
- [计算机专业字体配置](https://github.com/TheNetAdmin/zjuthesis/blob/master/config/format/major/cs/fonts.tex)

## 修正原因与位置

- `zjuthesis.tex`：选择计算机专业 `cs`。
- `config/format/major/cs/layout.tex`：在硕士分支增加目录编号槽宽，为二、三级编号留出空间；其余硕士版式继承上游。
- `page/graduate/term-translation.tex`：缩略词表列宽按正文宽度减去列间距计算，避免原固定列宽越界。
- `body/graduate/content.tex`：提纲阶段采用自然页底，定义空节占位段落。
- `body/graduate/chapters/` 与附录：在没有正文的末级标题后加入可替换占位段落。连续标题原先被排成禁止分页的长块，导致第 4 章文字越过页底；这属于提纲内容结构问题，不能仅靠切换专业选项修复。

双面排版的 `TwoSide=true` 保留，因此新章从奇数页开始，可能出现用于排版的章间空白页。
目前未加入实际文献引用，参考文献为空属于提纲状态。

## 编译与检查

在论文根目录运行 `latexmk -xelatex -interaction=nonstopmode -halt-on-error -outdir=out zjuthesis.tex`。
产物为 `out/zjuthesis.pdf`。排版检查图像和日志保存在已忽略的 `out/layout-review/` 中。
写入正文后删除对应的 `\thesisdraftnote`，定稿时再根据最终版式决定是否移除 `\raggedbottom`。
