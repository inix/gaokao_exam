# 介绍
高考试卷LaTeX模板，来自网友分享，提供全国卷3、北京卷、苏州卷高考数学试卷和小学数学试卷的排版的例子，提供的小学试卷排版增加了一些使用改进的例子。适合小学数学、初中数学、高中数学等数学试卷排版。


# 使用方式
## 安装TexLive

Windows系统: 下载并安装 [Texlive windows](http://mirror.ctan.org/systems/texlive/tlnet/install-tl-windows.exe)；

MacOS: 下载MacTex并安装 [MacTex](https://www.tug.org/mactex/)。

## 用TexWorks打开并使用 XeLatex编译

安装完成之后，使用`TexWorks`打开`.tex`文件，并使用`XeLatex`编译，编译成功便看到渲染结果。

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
