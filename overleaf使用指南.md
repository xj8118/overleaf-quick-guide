# overleaf使用指南

一般可直接在Templates中搜想要的模版使用，里面会导入需要的包，缺少的包要自行导入

## 一、标题

```latex
一级标题 \section{}
二级标题 \subsection{}
三级标题 \subsubsection{}
四级标题 \paragraph 注：四级标题不显示标题序号
生成目录 \tableofcontents
标题后面加\label{xxx},即可引用此标题\ref{xxx}
```

## 二、文字内容

1. 文字要显示分段需在两段之间空一行，另起一行不会显示分段

2. 文字注释用`%`，注释一个段落即选中段落同时按`ctrl+？/`
3. 文字内容中，要想显示`%`，可以用`\`加在前面，即可显示
4. 有时候`~`直接输入无法显示，可以用`$\sim$`即可显示
5. 加粗用`\textbf{xxx}`，斜体用`\textit{}`，下划线用`\underline{}`

## 三、公式

1. 行内公式

   ```latex
   $a=2b$
   ```

2. 行间公式

   ```latex
   \begin{equation}
       x = \frac{b^2}{2n} + \sqrt{n^2}
   \label{eq:xxx}
   \end{equation}
   ```

   文中引用这个公式`\eqref{eq:xxx}`

3. 常见latex公式（见附录，typora中点击公式即可显示编写代码，在vscode等中也可打开）

## 四、列表

1. 无序列表

   ```latex
   \begin{itemize}
   		\item 第一件事
   		\item 第二件事
   		\item 第三件事
   \end{itemize}
   ```

2. 有序列表

   ```latex
   \begin{enumerate}
   		\item 第一件事
   		\item 第二件事
   		\item 第三件事
   \end{enumerate}
   ```

## 五、插图

先上传图片到项目内，在对应的地方插入下面的内容：

```latex
\begin{figure}
  \centering
  \includegraphics[width=1\linewidth]{figures/image1.3.pdf}
  \caption{图片的标题}
  \label{fig:xxx}
\end{figure}
```

引用这个图片`~\ref{fig:xxx}`，`[width=1\linewidth]`里面的数字可以调节图片大小0～1，`{figures/image1.3.pdf}`是图片的路径。

图片尽量不要有空白边距，不然影响显示大小。

##### 多子图

1. 一行多图

   ```latex
   \begin{figure}[htbp]
       \centering
       \begin{subfigure}[b]{0.23\textwidth}
           \includegraphics[width=\textwidth]{fig1.png}
           \caption{子图1}
           \label{fig:sub1}
       \end{subfigure}
       \hspace{0.02\textwidth} % 0.02\textwidth控制子图间距，可以根据需要调整（推荐0.01–0.03之间）。
   
       \begin{subfigure}[b]{0.23\textwidth}
           \includegraphics[width=\textwidth]{fig2.png}
           \caption{子图2}
           \label{fig:sub2}
       \end{subfigure}
       \hspace{0.02\textwidth}
   
       \begin{subfigure}[b]{0.23\textwidth}
           \includegraphics[width=\textwidth]{fig3.png}
           \caption{子图3}
           \label{fig:sub3}
       \end{subfigure}
       \hspace{0.02\textwidth}
   
       \begin{subfigure}[b]{0.23\textwidth}
           \includegraphics[width=\textwidth]{fig4.png}
           \caption{子图4}
           \label{fig:sub4}
       \end{subfigure}
   
       \caption{总标题：一行四张子图，水平间距可调}
       \label{fig:all1}
   \end{figure}
   ```

2. 2*2多行多图

   ```latex
   \begin{figure}[htbp]
       \centering
       % ---- 第一行 ----
       \begin{subfigure}[b]{0.45\textwidth}
           \includegraphics[width=\textwidth]{fig1.png}
           \caption{子图1}
           \label{fig:sub1}
       \end{subfigure}
       \hfill % 自动均匀分布水平空白
       \begin{subfigure}[b]{0.45\textwidth}
           \includegraphics[width=\textwidth]{fig2.png}
           \caption{子图2}
           \label{fig:sub2}
       \end{subfigure}
   
       \vspace{0.5em} % 控制上下两行的垂直间距
   
       % ---- 第二行 ----
       \begin{subfigure}[b]{0.45\textwidth}
           \includegraphics[width=\textwidth]{fig3.png}
           \caption{子图3}
           \label{fig:sub3}
       \end{subfigure}
       \hfill
       \begin{subfigure}[b]{0.45\textwidth}
           \includegraphics[width=\textwidth]{fig4.png}
           \caption{子图4}
           \label{fig:sub4}
       \end{subfigure}
   
       \caption{总标题：2×2 子图，水平垂直间距可调}
       \label{fig:all2}
   \end{figure}
   %说明：
   %\hfill：自动分配左右空白，使两图均匀分布。
   %\vspace{0.5em}：调整两行子图之间的垂直距离，可改成 1em 或 0pt。
   ```

3. 引用方式

- 单独引用子图：`\ref{fig:sub2}` → (b)
- 引用整个图：`\ref{fig:all}` → 图 5

## 六、表格

借用工具会简单很多：`https://tablesgenerator.com`，生成以下代码：

```latex
\begin{table}
\centering
\caption{通用目标检测与消费电子产品表面缺陷检测的比较}
\begin{tabular}{ccc}
\toprule
类别  & 通用目标检测 &消费电子产品表面缺陷检测\\
\midrule
分辨率 &低分辨率 & 高分辨率\\
目标特征 &尺度分布较集中 &尺度分布更分散  \\
形态	&通常可定义为固定形态 &难以为缺陷定义固定形态 \\
数据集中小目标比例 &较小 &比例更高 \\
对比度 &通常清晰 &对比度低、边界模糊 \\
\bottomrule
\end{tabular}
\label{tab:xxx}
\end{table}
```

![](/Users/guoyuyan/Documents/工作/overleaf快速使用指南与实用小工具/image1.png)

其中，`{ccc}`这里可以设置每一列的宽度和对齐方式，`{}`里面换成下面三列，就设置成了每列的宽度为3cm 3.5cm 3.5cm，垂直居中对齐。

```latex
    >{\centering\arraybackslash}m{3cm} 
    >{\centering\arraybackslash}m{3.5cm}
    >{\centering\arraybackslash}m{3.5cm}
```

用`~\ref{tab:xxx}`引用这个表格。下面加在表格内可以在表格尾添加注释：

```latex
\begin{tablenotes}
    \item [*] 附注：*xxx
\end{tablenotes}
```

## 七、参考文献引用

在`.bib`文件中复制进文献的`BibTaX`引用格式，并修改第一行给出label，如下面的bib4，引用时在文字后面加上`\cite{bib4}`即可引用，不用关注顺序，会自动调整。在主文件最后加入`\bibliography{ref/refs} `即可在正文后面显示参考文献。

```latex
@article{bib4,
  title={A fast and robust convolutional neural network-based defect detection model in product quality control},
  author={Wang, Tian and Chen, Yang and Qiao, Meina and Snoussi, Hichem},
  journal={The International Journal of Advanced Manufacturing Technology},
  volume={94},
  number={9},
  pages={3465--3471},
  year={2018},
  publisher={Springer}
}
```

## 八、浮动位置参数

表格、图片等在`\begin{table}`或`\begin{figure}`后面可以加上浮动位置参数，告诉编译器优先将浮动体放置在哪里。

| 控制符 | 含义                                | 优点                           | 缺点                               | 典型应用场景                                   |
| ------ | ----------------------------------- | ------------------------------ | ---------------------------------- | ---------------------------------------------- |
| `h`    | here（当前位置）                    | 尽量贴近代码位置               | 不保证一定放在当前位置，可能被移走 | 小图、小表，希望接近正文处                     |
| `t`    | top（页顶）                         | 排版整洁，图片在页顶更美观     | 不适合和正文紧密关联的图表         | 跨页大图、大表，或文章结构化图片               |
| `b`    | bottom（页底）                      | 保持段落完整性，避免正文被打断 | 不适合正文中紧跟的说明             | 章节末尾附带图表                               |
| `p`    | page（浮动页）                      | 专门一页放置浮动体，整洁       | 可能导致图表与正文分离，阅读不便   | 图表很多、排版复杂时                           |
| `!`    | override（忽略限制）                | 更倾向于遵守用户指定的位置     | 可能破坏版面美观                   | `[!ht]`：需要更强制位置时                      |
| `H`    | Here，强制当前位置（需 `float` 包） | 严格按代码位置放置             | 可能破坏版面布局，留白不美观       | 绝对必须跟随正文的图表，如流程图、关键公式附图 |

##### 使用建议

- **一般使用**：`[htbp]`，给 LaTeX 足够的自由度，让排版美观。
- **正文紧密相关的图/表**：`[ht]` 或 `[!ht]`。
- **严格不允许浮动**：`[H]`（需 `\usepackage{float}`）。
- **图表较多，正文简洁**：`[p]`，专页展示图表。

##### 常见组合

- `[h]`：尽量放在当前位置，但 LaTeX 可能仍会移动它。
- `[ht]`：优先当前位置，放不下就放页顶（最常用）。
- `[htbp]`：当前位置、顶端、底部、单独页都可以，LaTeX 自由决定（默认的最佳实践）。
- `[!htbp]`：更强烈地要求优先按照 `[htbp]` 排布，忽略部分内部规则。
- `[H]`：使用 `float` 包时，绝对强制放在代码处。

## 九、代码块

1. 使用 `verbatim` 环境（最简单）

```latex
\begin{verbatim}
for i = 1:10
    print(i)
end
\end{verbatim}
```

- **特点**：保持原始格式，不支持语法高亮。
- **适用**：简单代码展示。

------

2. 使用 `listings` 宏包（常用，有语法高亮）

导言区加载宏包：

```latex
\usepackage{listings}
\usepackage{xcolor}

\lstset{
    basicstyle=\ttfamily\small,  % 基本字体
    keywordstyle=\color{blue},   % 关键字颜色
    commentstyle=\color{green!50!black}, % 注释颜色
    stringstyle=\color{red},     % 字符串颜色
    showstringspaces=false,      % 不显示空格
    numbers=left,                % 行号显示在左侧
    numberstyle=\tiny\color{gray},
    frame=single,                % 给代码加边框
    breaklines=true              % 自动换行
}
```

正文插入代码：

```latex
\begin{lstlisting}[language=Python, caption={示例代码}, label={lst:example}]
def hello():
    print("Hello, Overleaf!")
# 注释行
\end{lstlisting}
```

- **特点**：支持多种语言 (`language=Python, C, Java, etc.`)，可加标题和引用。
- **适用**：大多数论文代码展示。

------

3. 使用 `minted` 宏包（最漂亮，有语法高亮）

导言区：

```latex
\usepackage{minted}
```

> **注意**：编译时需启用 `-shell-escape`，Overleaf 需要在 **Menu → Compiler → LaTeX → LaTeX (XeLaTeX) + shell-escape**。

正文：

```latex
\begin{minted}[fontsize=\small, linenos, frame=lines]{python}
def hello():
    print("Hello, Minted!")
\end{minted}
```

- **特点**：高亮效果好、支持多语言、可选行号、配色多样。
- **适用**：需要美观展示源码的论文。

------

4. 引用代码块

- `listings` 引用：`\ref{lst:example}` → Listing 1
- `minted` 引用：同理使用 `\label`。

## 十、字体等设置

字体、字号、行距等全放在一个独立文件里统一管理，然后在主文件中一行引入即可

用 `preamble.tex`

**preamble.tex**（和主文件放同一目录）：

```latex
% ===== Global preamble: preamble.tex =====
% 引擎分支（建议用 XeLaTeX/LuaLaTeX 以便中文字体）
\usepackage{iftex}
\ifPDFTeX
  \usepackage[T1]{fontenc}
  \usepackage[utf8]{inputenc}
  \usepackage{newtxtext,newtxmath} % 英文字体 Times 风格
\else
  \usepackage{fontspec}
  \usepackage{unicode-math} % 如不需要数学字体可去掉
  % 英文字体
  \setmainfont{Times New Roman}
  \setsansfont{Arial}
  \setmonofont{Courier New}
  % 中文（xeCJK for XeLaTeX / LuaLaTeX）
  \usepackage{xeCJK}
  \setCJKmainfont{SimSun}        % 宋体
  \setCJKsansfont{SimHei}        % 黑体
  \setCJKmonofont{FangSong}      % 仿宋
\fi

% 行距（论文常用 1.5 倍）
\usepackage{setspace}
\onehalfspacing

% 段落样式（按需）
\setlength{\parindent}{2em}   % 首行缩进
\setlength{\parskip}{0pt}     % 段前后间距

% 页面与标题（按需）
\usepackage[a4paper,margin=2.5cm]{geometry}
\usepackage{titlesec}
\titleformat{\section}{\large\bfseries}{\thesection}{0.5em}{}
\titleformat{\subsection}{\normalsize\bfseries}{\thesubsection}{0.5em}{}

% 图表标题与间距（按需）
\usepackage{caption}
\captionsetup{
  font=small,
  labelfont=bf,
  labelsep=period, % “图 1.” 这种
  skip=6pt         % 图与标题的垂直间距
}
\usepackage{subcaption}
\captionsetup[sub]{font=small,labelfont=bf}

% 代码块（任选其一：listings 或 minted）
\usepackage{xcolor}
\usepackage{listings}
\lstset{
  basicstyle=\ttfamily\small,
  numbers=left, numberstyle=\tiny\color{gray},
  frame=single, breaklines=true, showstringspaces=false,
  keywordstyle=\color{blue}, commentstyle=\color{green!50!black}, stringstyle=\color{red}
}

% 常用宏（示例）
\newcommand{\eng}[1]{\textsf{#1}}   % 英文术语格式
```

**主文件 main.tex：**

```latex
\documentclass[12pt,a4paper]{article}
\input{preamble}  % ← 一行引入全局设置

\begin{document}
\section{示例}
这里使用的是统一设置的字体、字号与行距。

% 代码示例
\begin{lstlisting}[language=Python, caption={示例代码}]
def hello():
    print("Hello, Overleaf!")
\end{lstlisting}

\end{document}
```

> 更换字体/行距时，只改 `preamble.tex`，全局生效。

------

兼容/注意事项

- **编译引擎**：如果用中文字体，建议 **XeLaTeX 或 LuaLaTeX**。pdfLaTeX 下中文需 CJK 宏包，字体配置不一样。
- **学校/模板类文档（如 thuthesis）**：这些类文件可能自带字体/行距设定。若“冲突或被覆盖”，可把你的设置放到 `\AtBeginDocument{ ... }` 中，或查模板的选项开关（有的需要关闭模板的默认字体设定）。
- **可配置参数**：把容易调整的值（如行距、页边距、标题大小）集中成宏，方便统一修改。
- **字体显示问题**字体有可能显示不出来，因为编译环境的问题。可以在本地编译，或者在项目中导入需要的字体包。



