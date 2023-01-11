---
title: MarkDown数学表达式
category: 笔记
tags:
  - markdown
banner_img: /img/banner/md_math.jpg
index_img: /img/cover/md_math.jpg
excerpt: markdown中常见数学公式及语法
date: 2022-11-27 11:37:55
---
## 1.创建代码块

行内式：`$x+y$`，$x+y$

独立公式：

```text
$$
x+y
$$
```

## 2.常用的符号

空格：`\quad`

上标：`x^2`，$x^2$

下标：`x_1`，$x_1$

分数：`\frac{a}{b}`，$\frac{a}{b}$

加减号：`\pm`，$\pm$

乘号：`\times`，$\times$

星乘号：`\ast`，$\ast$

除号：`\div`，$\div$

因为：`\because`，$\because$

所以：`\therefore`，$\therefore$

下划线：`\underline{a}`，$\underline{a}$

上划线：`\overline{a}`，$\overline{a}$

异或：`\bigoplus`，$\bigoplus$

根号：`\sqrt{a}`，$\sqrt{a}$

省略号：`\cdots`，$\cdots$

小于等于：`\leq`，$\leq$

大于等于：`geq`，$\geq$

不等于：`\ne`，$\ne$

无穷：`\infty`，$\infty$

对数：`\log_{2}{8}`，$\log_{2}{8}$

矢量：`\vec{F}`，$\vec{F}$

累加：`\sum_{i=1}^{n}{a_i}`，$\sum_{i=1}^{n}{a_i}$

累乘：`\prod_{i=1}^{n}{a_i}`，$\prod_{i=1}^{n}{a_i}$

求极限：`$\lim_{a\to+\infty}{a+b}$`，$\lim_{a\to+\infty}{a+b}$

积分：`\int_{0}^{1} {x^2} dx`，$\int_{0}^{1} {x^2} dx$

上箭头：`\uparrow`，$\uparrow$

下箭头：`\downarrow`，$\downarrow$

左箭头：`\leftarrow`，$\leftarrow$

右箭头：`\rightarrow`，$\rightarrow$

阿尔法：`\alpha`，$\alpha$

角度：`\theta`，$\theta$

德尔塔：`\Delta`，$\Delta$

派：`\pi`，$\pi$

大括号：`\left\{ a+b \right\}`，$\left\{ a+b \right\}$

中括号：`\left[ a+b \right]`，$\left[ a+b \right]$

小括号：`\left( a+b \right)`，$\left( a+b \right)$

连线：`\underbrace{a+b+c+d}_{Sample}`，$\underbrace{a+b+c+d}_{Sample}$

更改颜色：`\color{red}{aa}`，$\color{red}{a}$

## 3.特殊结构

### 方程组

$$
\begin{cases}

3x + 5y +  z \\

7x - 2y + 4z \\

-6x + 3y + 2z

\end{cases}
$$

```text
\begin{cases}
3x + 5y +  z \\
7x - 2y + 4z \\
-6x + 3y + 2z
\end{cases}
```

### 条件表达式

$$
f(n) =

\begin{cases} 

n/2,  & \text{if }n\text{ is even} \\

3n+1, & \text{if }n\text{ is odd}

\end{cases}
$$

```text
f(n) =
\begin{cases} 
n/2,  & \text{if }n\text{ is even} \\
3n+1, & \text{if }n\text{ is odd}
\end{cases}
```

### 表格

$$
\begin{array}{|c|c|c|}

    \hline2&9&4\\

    \hline7&5&3\\

    \hline6&1&8\\

    \hline

\end{array}
$$

```text
\begin{array}{|c|c|c|}
    \hline 2&9&4\\
    \hline 7&5&3\\
    \hline 6&1&8\\
    \hline
\end{array}
```

### 矩阵

$$
\begin{matrix}

 1 & 2 & 3 \\

 4 & 5 & 6 \\

 7 & 8 & 9 \\

\end{matrix} \tag{1}
$$

```text
\begin{matrix}
 1 & 2 & 3 \\
 4 & 5 & 6 \\
 7 & 8 & 9 \\
\end{matrix} \tag{1}
```

### 真值表

$$
\begin{array}{cc|c}

            A&B&F\\ 

    \hline  0&0&0\\

            0&1&1\\

            1&0&1\\

            1&1&1\\

\end{array}
$$

```text
\begin{array}{cc|c}
           A&B&F\\
    \hline 0&0&0\\
           0&1&1\\
           1&0&1\\
           1&1&1\\
\end{array}
```

参考资料：

[^1]: [Maxkit: 如何在 Markdown 輸入數學公式及符號](https://blog.maxkit.com.tw/2020/02/markdown.html)
    
[^2]: [Typora数学公式汇总（Markdown） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/261750408)
