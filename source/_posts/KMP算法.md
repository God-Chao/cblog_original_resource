---
title: KMP算法
category: 笔记
tags:
  - 算法
  - 字串匹配问题
banner_img: /img/banner/kmp.jpg
index_img: /img/cover/kmp.jpg
excerpt: 详细讲解KMP算法的原理及应用
date: 2022-11-22 14:26:45
---
## 1.串的朴素模式匹配算法

**什么是字串匹配：**

在主串中找到与模式串相同的字串并返回其位置，如主串google、模式串gle，则结果为3

**算法思路：**

相当于拿着模式串和主串对齐，对比其第一个字符。不相等则模式串往右移一位，相等则匹配剩下的字符，计算方式如下：

$$
\begin{array}{|c|c|c|c|c|c|c|c|}
	\hline  &1&2&3&4&5&6&7\\
	\hline S&w&a&n&g&d&a&o\\
	\hline T&g&d&a\\
	\hline
\end{array}
$$

$$
\begin{array}{|c|c|c|c|c|c|c|c|}
	\hline k&1&2&3&4&4&4&4\\
	\hline i&1&2&3&4&5&6&7\\
	\hline j&1&1&1&1&2&3&4\\
	\hline
\end{array}
$$

**缺点：**

当某些字符串与模式串能部分匹配时，主串的扫描指针i经常回溯，导致时间开销增加

**朴素模式匹配算法代码：**

```c++
// S为主串，T为模式串
int Index(String S, String T) {
    // i用来遍历主串
    // k用来标记当前匹配串的第一个字符
    // j用来遍历模式串
    int i = k = j = 1;
    while (i <= S.length && j <= T.length) {
        if (S[i] == T[j]) {
            i++;
            j++;
        } else {
            k++;
            i = k;
            j = 1;
        }
    }
    // 用j是否超出边界作为成功标志
    if (j > T.length) {
        return k;
    } else {
        return 0;
    }
}
```

## 2.KMP算法

**优点：**

在上述朴素模式匹配算法中，当模式串第一个字符匹配时，j和i都继续++去匹配剩下的字符，但一旦当模式串第j个字符不匹配时，i和j都回溯，即模式串往右移动一格。但是其实大部分时候可以通过计算不回溯这么多（某些模式串中回溯到特点值就可保证最短不匹配）。例如：模式串google当j=5时不匹配，此时可发现只要i不变，j回溯到1即可满足最短不匹配，即模式串往右移了4格。KMP算法就是在i不回溯的情况下给出一个next数组用于表示当不匹配时j应该回溯到哪里，这样在模式匹配算法的基础上进一步优化了性能，解决了i经常回溯的问题。

**求next数组：**

$$
next[j] =
\begin{cases} 
    0,  & \text{当j=1时} \\
    1,  & \text{当j=2时} \\
    前j-1个字串的最长相等前后缀长度+1,   & \text{当j>2时}
\end{cases}
$$

前j-1个字串的最长相等前后缀长度：当前j-1个字串为abcab时，ab为前缀和后缀最长相等部分，结果为2；当前j-1个子串为abc时，没有前后缀相等部分，结果为0。

$$
\begin{array}{|c|c|c|c|c|c|c|}
	\hline 序号j&1&2&3&4&5&6\\
	\hline 模式串&a&b&a&b&a&a\\
	\hline next[j]&0&1&1&2&3&4\\
	\hline
\end{array}
$$

**KMP算法代码：**

```c++
int Index_KMP(String S, String T, int next[]) {
    int i = j = 1;
    while (i <= S.length && j <= T.length) {
        if (j==0 || S[i] == T[j]) {
            i++;
            j++;
        } else {
            j = next[j];        // i不回溯，j查找next数组回溯
        }
    }
    if (j > T.length) {
        return i - T.length;    // 匹配成功
    } else {
        return 0;
    }
}
```

## 3.KMP算法的优化

当模式串为google，j=4时。原KMP算法的next[4]=1，但是其实此处不需要再重新匹配第一位，所以应该优化为next[4]＝0。因此引入next的优化数组nextVal。

$$
nextVal[j] =
\begin{cases} 
    0,  & \text{当j=1时} \\
    next[j],  & \text{当j>1 且 T[next[j]]!=T[j]时} \\
    nextVal[next[j]],  & \text{当j>1 且 T[next[j]]==T[j]时} \\
\end{cases}
$$

$$
\begin{array}{|c|c|c|c|c|c|c|}
	\hline 序号j&1&2&3&4&5&6\\
	\hline 模式串&a&b&a&b&a&a\\
	\hline next[j]&0&1&1&2&3&4\\
    \hline nextVal[j]&0&1&0&1&0&4\\
	\hline
\end{array}
$$
