# 介绍
高考试卷LaTeX模板，来自网友分享，提供全国卷3、北京卷、苏州卷高考数学试卷和小学数学试卷的排版的例子，提供的小学试卷排版增加了一些使用改进的例子。适合小学数学、初中数学、高中数学等数学试卷排版。


# 使用方式
## 安装TexLive

支持Windows，Linux和MacOS（https://www.tug.org/texlive/）。
尽量用TexLive，不要使用其他发行版，比如MikTex等。

## 安装相关字体
`NEMT.sty`文件里面使用了很多方正字体，请自行到百度搜索并安装，请注意字体可能有版权。

## 用TexWorks打开并使用 XeLatex编译

安装完成之后，使用`TexWorks`打开`.tex`文件，并使用`XeLatex`编译，编译成功就可以看到渲染结果。

## 把相关sty文件添加到Texlive搜索目录中(可选)
这一步可以不用进行，但是应该保证 sty文件和tex文件在同一个目录。

如果你用Windows 10，你的Texlive目录应该为 `C:/Users/stefan/texmf`：
```bash
创建目录结构：  C:/Users/stefan/texmf/tex/latex/exam
把文件 NEMT.sty variant.sty复制到 C:/Users/stefan/texmf/tex/latex/exam
```
这样，就可以在各`tex`文件里使用 `\usepackage{NEMT}`了。

其他系统，请使用如下方法获取搜索目录：
```bash
kpsewhich -var-value=TEXMFHOME
```
添加sty文件之后，使用如下命令查看是否生效：
```bash
kpsewhich NEMT.sty
```

# 试卷排版改进指南
## 表格
小学数学试卷排版会遇到大量的计算题排版，比如直接写得数、脱式计算、解方程等，其中包含了分数等一些需要一些排版才可以输出较为满意的结果。

- 有序列表内尽量不要使用'\begin{table}...\end{table}'来排版
```latex
\begin{table}
...
\end{table}
```
`\begin{table}`是用float方式布局，Latex会自动排版，如果在`enumerate`里面使用，会造成列表子项无法控制表格的位置，造成表格移位等难以控制的排版问题。
应该直接使用`tabular`、`tabular*`等直接排版。

示例：
[请参考 overLeaf的在线例子](https://www.overleaf.com/project/5c29cb9701cd4e564c780b13)

- 设置表格Cell的Margin、Padding
使用`\def\arraystretch{1.5}`来设置Margin和Padding，解决分数显示的问题。

示例：
[请参考 overLeaf的在线例子](https://www.overleaf.com/project/5c29cb9701cd4e564c780b13)

## 图片
跟`\begin{table}`一样，`\begin{figure}`也是float布局，会造成错位的问题，应该使用`minipage`.
例子：
```latex
        \item 学校图书馆购回两种新书，每种3套，一共多少钱？\\[0.5em]
          \begin{minipage}{\linewidth}
            \includegraphics[width=0.20\textwidth]{./pic/ls33.png}
          \end{minipage}
```
完成的代码请参考项目里的小学数学例子。
