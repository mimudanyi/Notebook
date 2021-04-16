# Latex 基础

## 一、命令（Command）

```latex
\【命令名】[【属性名=属性值】]{【参数】}
```

```latex
\documentclass{article}	%文档的类型
```

## 二、前言（Preamble）

位于 `\begin{document}` 之前的内容都被称作是前言（Preamble）

```latex
\title{【文章标题】}
\author{【作者名】}
\date{【时间】}	%参数【时间】是 \today 的话会自动显示今天的时间
```

## 三、环境

在同一个环境中的内容将会共享相同的文字格式

```latex
\begin{}
...
\end{}
```

## 三、正文（Body）

```latex
\begin{document}

\end{document}
```

## 四、部（Part）、章（Chapters）和节（Sections）

```latex
\part{【部名】

\chapter{【章名】}

\section{【节名】}	%开启一个新的章节
\subsection{【子节名】}	%开启一个子章节
\subsubsection{【三级节名】}	%开启一个三级章节
```

## 五、格式化

```latex
\textbf{【文字】}	%加粗
\textit{【文字】}	%斜体
\underline{【文字】}	%下划线
```

## 六、图片

```latex
\usepackage{graphicx}	%引入 graphicx 这个包，包含若干个绘制图片的指令

\begin{figure}
\centering	%居中显示
\includegraphics[width=0.5\textwidth]{【图片名，不加后缀扩展名】}	%导入图片，添加尺寸属性
\caption{【图片名】}	%给图片命名
\end{figure}
```

## 七、列表（Lists）

### 7.1 无序列表

```latex
\begin{itemize}
\item 【列表项1】
\item 【列表项2】
\item 【列表项3】
\end{itemize}
```

### 7.2 有序列

```latex
\begin{enumerate}
\item 【列表项1】
\item 【列表项2】
\item 【列表项3】
\end{enumerate}
```

## 八、数学公式

### 8.1 行内公式

```latex
$...$
```

### 8.2 单行公式

```latex
\begin{equation}
E=mc^2
\end{equation}

以上可以简写为
\[
E=mc^2
\]
```

## 九、表格

```latex
% c（centering）居中对齐
% l 左对齐
% r 右对齐

%以下为无边框表格
\begin{tabular}{c l r}	%有几个字母表示有几列
单元格1 & 单元格2 & 单元格3 \\	%单元格用 & 隔开，行用 \\ 隔开
单元格1 & 单元格2 & 单元格3 \\
单元格1 & 单元格2 & 单元格3
\end{tabular}

%以下为有表框表格，|表示竖线，\hline表示横线，输入两次\hline表示双横线
\begin{tabular}{|c|l|r}	%有几个字母表示有几列
\hline
单元格1 & 单元格2 & 单元格3 \\	%单元格用 & 隔开，行用 \\ 隔开
\hline
单元格1 & 单元格2 & 单元格3 \\
\hline
单元格1 & 单元格2 & 单元格3
\hline
\end{tabular}

%如果要设置每一列的宽度可以用 p={多少cm}，p 代表paragragh
\begin{tabular}{|p={2cm}|l|r}	%有几个字母表示有几列
\hline
单元格1 & 单元格2 & 单元格3 \\	%单元格用 & 隔开，行用 \\ 隔开
\hline
单元格1 & 单元格2 & 单元格3 \\
\hline
单元格1 & 单元格2 & 单元格3
\hline
\end{tabular}

% 可以给表格添加居中属性，可以添加表格名字等
\begin{table}
\center	%居中显示
\begin{tabular}{|p={2cm}|l|r}	%有几个字母表示有几列
\hline
单元格1 & 单元格2 & 单元格3 \\	%单元格用 & 隔开，行用 \\ 隔开
\hline
单元格1 & 单元格2 & 单元格3 \\
\hline
单元格1 & 单元格2 & 单元格3
\hline
\end{tabular}
\caption{【可以添加表格名字】
\end{table}
```

## 六、注释（Annotation）

```latex
在LaTex中的注释有以下3种

1、注释一行：使用%注释一行文字， 在%后的文字都不予编译；

2、注释一段：使用\iffalse .... \fi 包含一段文字，被包含的文字被注释掉了；

3、注释一段： 用\begin{comment} ... \end{comment} 包含被注释的文字, 但是需要在引言区包括相应的宏包, 即 \usepackage{verbatim}.
```

