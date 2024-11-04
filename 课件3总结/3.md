## 课件2中的矩阵都是方阵，优化后的高斯消元法可以应用在矩阵非方阵的情况下，得到阶梯型矩阵
只需要在消元过程中遇到主元和主元下方都是0的情况，就跳过该步（消元完成），直接进入下一列，选择作为主元位置。
### 行阶梯形

对于一个具有行 \( E_{i\ast} \) 和列 \( E_{\ast j} \) 的 \( m \times n \) 矩阵 \( E \)，若满足以下两个条件，则称其为行阶梯形：

- 如果 \( E_{i\ast} \) 完全由零组成，那么 \( E_{i\ast} \) 以下的所有行也都完全为零；即，所有零行位于底部。
- 如果 \( E_{i\ast} \) 的第一个非零元素位于第 \( j \) 列，那么在 \( E_{\ast 1}, E_{\ast 2}, \ldots, E_{\ast j} \) 列中，第 \( i \) 行以下的所有元素均为零。

这两个条件表示，阶梯形中的非零元素必须位于一条从左上角开始并向右下方倾斜的阶梯线上，主元即为每行中的第一个非零元素。下图展示了行阶梯形矩阵的典型结构，其中主元位置用圆圈标出。
\[\begin{pmatrix}* & * & * & * & * & * & * & *\\ 0 & 0 & * & * & * & * & * & *\\ 0 & 0 & 0 & * & * & * & * & *\\ 0 & 0 & 0 & 0 & 0 & 0 & * & *\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\end{pmatrix}\]

由于在将矩阵 \( A \) 化为行阶梯形 \( E \) 时可以灵活地选择行操作，因此 \( E \) 中的元素并不是由 \( A \) 唯一确定的。

然而，\( E \) 的“形式”是唯一的，因为 \( E \)（和 \( A \)）中的主元位置是由 \( A \) 中的元素唯一确定的。

主元的数量也由 \( A \) 中的元素唯一确定。

这个数量称为 \( A \) 的秩（rank），它等于 \( E \) 中非零行的数量。

---

### 矩阵的秩

假设 \( A_{m \times n} \) 经过行操作化为阶梯形 \( E \)。\( A \) 的秩定义为以下数量：

\[
\text{rank}(A) = \text{主元的数量} = \text{\( E \) 中非零行的数量} = \text{\( A \) 中基本列的数量}
\]

其中，\( A \) 的基本列定义为包含主元位置的列。
**问题**：确定矩阵 \( A \) 的秩，并找出其中的基本列。

\[
A = \begin{pmatrix} 1 & 2 & 1 & 1 \\ 2 & 4 & 2 & 2 \\ 3 & 6 & 3 & 4 \end{pmatrix}.
\]

**解答**：将 \( A \) 化为行阶梯形，如下所示：

\[\mathbf{A}=\begin{pmatrix}\textcircled1&2&1&1\\2&4&2&2\\3&6&3&4\end{pmatrix}\longrightarrow\begin{pmatrix}\textcircled1&2&1&1\\0&0&0&\textcircled0\\0&0&0&1\end{pmatrix}\longrightarrow\begin{pmatrix}\textcircled1&2&1&1\\0&0&0&\textcircled1\\0&0&0&0\end{pmatrix}=\mathbf{E}.\]

因此，\(\text{rank}(A) = 2\)。主元位置位于第 1 列和第 4 列，所以 \( A \) 的基本列为 \( A_{\ast 1} \) 和 \( A_{\ast 4} \)。即，

\[
\text{基本列} = \left\{ \begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix}, \begin{pmatrix} 1 \\ 2 \\ 4 \end{pmatrix} \right\}.
\]

**请特别注意，基本列是从 \( A \) 中提取的，而不是从行阶梯形 \( E \) 中提取的。**

---
### \( E_A \) 符号


对于矩阵 \( A \)，符号 \( E_A \) 将表示通过行操作从 \( A \) 派生出的**唯一**的简化行阶梯形。

---

## 矩阵 \( A \) 和行阶梯矩阵\( E_A \) 中的列关系

- 在 \( E_A \) 中的每个非基列 \( E_{\ast k} \) 都是位于 \( E_{\ast k} \) 左边的基列的组合（倍数之和）。即：

\[\begin{aligned}
\mathbf{E}_{*k}& =\mu_{1}\mathbf{E}_{*b_{1}}+\mu_{2}\mathbf{E}_{*b_{2}}+\cdots+\mu_{j}\mathbf{E}_{*b_{j}} \\
&=\mu_1\begin{pmatrix}1\\0\\\vdots\\0\\\vdots\\0\end{pmatrix}+\mu_2\begin{pmatrix}0\\1\\\vdots\\0\\\vdots\\0\end{pmatrix}+\cdots+\mu_j\begin{pmatrix}0\\0\\\vdots\\1\\\vdots\\0\end{pmatrix}=\begin{pmatrix}\mu_1\\\mu_2\\\vdots\\\mu_j\\\vdots\\0\end{pmatrix},
\end{aligned}\]

  其中 \( E_{\ast b_i} \) 是 \( E_{\ast k} \) 左边的基列，而系数 \( \mu_i \) 是 \( E_{\ast k} \) 中前 \( j \) 个条目。

- 矩阵 \( A \) 的列关系与矩阵 \( E_A \) 的列关系完全相同。特别地，如果 \( A_{\ast k} \) 是 \( A \) 中的非基列，则

  \[
  A_{\ast k} = \mu_1 A_{\ast b_1} + \mu_2 A_{\ast b_2} + \cdots + \mu_j A_{\ast b_j},
  \]

  其中 \( A_{\ast b_i} \) 是 \( A_{\ast k} \) 左边的基列，系数 \( \mu_i \) 如上所述，是 \( E_{\ast k} \) 中的前 \( j \) 个条目。

**问题**：将每个非基列写成 \( A \) 中基列的组合。

\[
A = 
\begin{pmatrix}
2 & -4 & -8 & 6 & 3 \\
0 & 1 & 3 & 2 & 3 \\
3 & -2 & 0 & 0 & 8 \\
\end{pmatrix}.
\]

**解**：将 \( A \) 转换为 \( E_A \)，如下所示。

\[\begin{gathered}
\begin{pmatrix}2&-4&-8&6&3\\0&1&3&2&3\\3&-2&0&0&8\end{pmatrix}\to\begin{pmatrix}1&-2&-4&3&\frac{3}{2}\\0&1&3&2&3\\3&-2&0&0&8\end{pmatrix}\to\begin{pmatrix}1&-2&-4&3&\frac{3}{2}\\0&1&3&2&3\\0&4&12&-9&\frac{7}{2}\end{pmatrix}\to \\
\begin{pmatrix}\textcircled{1}&0&2&7&\frac{15}{2}\\0&\textcircled{1}&3&2&3\\0&0&0&-17&-\frac{17}{2}\end{pmatrix}\to\begin{pmatrix}\textcircled{1}&0&2&7&\frac{15}{2}\\0&\textcircled{1}&3&2&3\\0&0&0&\textcircled{1}&\frac{1}{2}\end{pmatrix}\to\begin{pmatrix}\textcircled{1}&0&2&0&4\\0&\textcircled{1}&3&0&2\\0&0&0&\textcircled{1}&\frac{1}{2}\end{pmatrix} 
\end{gathered}\]

第三列和第五列是非基列。观察 \( E_A \) 中的列可以得出：

\[
E_{\ast 3} = 2E_{\ast 1} + 3E_{\ast 2} \quad \text{和} \quad E_{\ast 5} = 4E_{\ast 1} + 2E_{\ast 2} + \frac{1}{2}E_{\ast 4}.
\]

矩阵 \( A \) 的列关系必须与 \( E_A \) 中的关系完全相同，因此：

\[
A_{\ast 3} = 2A_{\ast 1} + 3A_{\ast 2} \quad \text{和} \quad A_{\ast 5} = 4A_{\ast 1} + 2A_{\ast 2} + \frac{1}{2}A_{\ast 4}.
\]

你可以通过直接计算来验证这些等式的正确性。

---
## 一致性(有解)

以下每一项都等价于说矩阵 \( [A|b] \) 是一致的。
- 在对 \( [A|b] \) 进行行化简时，不会出现以下形式的行：
  
  \[
  (0 \ 0 \ \cdots \ 0 \ | \ \alpha) \quad \text{其中} \quad \alpha \neq 0.
  \]

- \( b \) 是 \( [A|b] \) 中的非基列。
- \( \text{rank}([A|b]) = \text{rank}(A) \)。
- \( b \) 是 \( A \) 中基列的组合。

总之就是不出现 $(0 \ 0 \ \cdots \ 0 \ )(x \ x \ \cdots \ x_n )^T=0$ 

---

**问题**：确定以下系统是否一致：

\[
x_1 + x_2 + 2x_3 + 2x_4 + x_5 = 1
\]
\[
2x_1 + 2x_2 + 4x_3 + 4x_4 + 3x_5 = 1
\]
\[
2x_1 + 2x_2 + 4x_3 + 4x_4 + 2x_5 = 2
\]
\[
3x_1 + 5x_2 + 8x_3 + 6x_4 + 5x_5 = 3
\]

**解答**：对增广矩阵 \( [A|b] \) 应用高斯消元法，如下所示：

\[
\begin{pmatrix}
1 & 1 & 2 & 2 & 1 & | & 1 \\
2 & 2 & 4 & 4 & 3 & | & 1 \\
2 & 2 & 4 & 4 & 2 & | & 2 \\
3 & 5 & 8 & 6 & 5 & | & 3 \\
\end{pmatrix}
\rightarrow
\begin{pmatrix}
1 & 1 & 2 & 2 & 1 & | & 1 \\
0 & 0 & 0 & 0 & 1 & | & -1 \\
0 & 0 & 0 & 0 & 0 & | & 0 \\
0 & 2 & 2 & 0 & 2 & | & 0 \\
\end{pmatrix}
\rightarrow
\begin{pmatrix}
1 & 1 & 2 & 2 & 1 & | & 1 \\
0 & 2 & 2 & 0 & 2 & | & 0 \\
0 & 0 & 0 & 0 & 1 & | & -1 \\
0 & 0 & 0 & 0 & 0 & | & 0 \\
\end{pmatrix}.
\]

由于形如 \( (0 \ 0 \ \cdots \ 0 \ | \ \alpha) \) 的行从未出现且 \( \alpha \neq 0 \)，因此系统是一致的。我们还可以观察到 \( b \) 是 \( [A|b] \) 中的非基列，从而 \( \text{rank}([A|b]) = \text{rank}(A) \)。最后，通过将 \( A \) 完全化简为 \( E_A \)，可以验证 \( b \) 确实是基列 \( \{A_{\ast 1}, A_{\ast 2}, A_{\ast 5}\} \) 的组合。

---

## 齐次方程组

- 一个包含 \( n \) 个未知数的 \( m \) 个线性方程的系统

  \[
  a_{11}x_1 + a_{12}x_2 + \cdots + a_{1n}x_n = 0, \\
  a_{21}x_1 + a_{22}x_2 + \cdots + a_{2n}x_n = 0, \\
  \vdots \\
  a_{m1}x_1 + a_{m2}x_2 + \cdots + a_{mn}x_n = 0.
  \]

  被称为**齐次系统**（homogeneous system）。

- 如果右侧至少有一个非零数，则该系统称为**非齐次系统**（nonhomogeneous system）。

- 齐次系统始终是一致的，不存在一致性问题。

- \( x_1 = x_2 = \cdots = x_n = 0 \) 是一种解，这种解不依赖于系数的取值，称为**平凡解**（trivial solution）。

### 总结

设 \( A_{m \times n} \) 为一个包含 \( n \) 个未知数和 \( m \) 个线性方程的齐次系统的系数矩阵，并假设 \( \text{rank}(A) = r \)

- 与基列位置（即主元位置）对应的未知数称为**基变量**（basic variables），而与非基列位置对应的未知数称为**自由变量**（free variables）。
  
- 系统中恰好有 \( r \) 个基变量和 \( n - r \) 个自由变量。

- 为了描述所有解，将 \( A \) 用高斯消元法化简为行梯形形式，然后使用回代来求出基变量关于自由变量的表达式。这会产生具有以下形式的**通解**（general solution）：

  \[
  x = x_{f_1} h_1 + x_{f_2} h_2 + \cdots + x_{f_{n-r}} h_{n-r},
  \]

  其中，\( x_{f_1}, x_{f_2}, \ldots, x_{f_{n-r}} \) 是自由变量，而 \( h_1, h_2, \ldots, h_{n-r} \) 是 \( n \times 1 \) 的列向量，代表齐次系统的特定解。\( h_i \) 与在回代过程中使用的行梯形形式无关。由于自由变量 \( x_i \) 可以取所有可能值，因此通解生成了所有可能的解。

- （非）齐次系统在且仅在 \( \text{rank}(A) = n \) 时（即没有自由变量时）具有唯一解（即平凡解）。
- 其次系统的\( \text{rank}(A) =\text{rank}(A|b)  \)

**问题**：解释为什么以下齐次系统有无穷多个解，并给出通解：

\[
x_1 + 2x_2 + 2x_3 = 0\\
2x_1 + 5x_2 + 7x_3 = 0\\
3x_1 + 6x_2 + 6x_3 = 0\\
\]

**解答**：

\[
A = \begin{pmatrix} 1 & 2 & 2 \\ 2 & 5 & 7 \\ 3 & 6 & 6 \end{pmatrix} \rightarrow \begin{pmatrix} 1 & 2 & 2 \\ 0 & 1 & 3 \\ 0 & 0 & 0 \end{pmatrix} = E
\]

显示了 \( \text{rank}(A) = 2 < n = 3 \)。由于基列在位置1和2，\( x_1 \) 和 \( x_2 \) 是基变量，而 \( x_3 \) 是自由变量。使用对 \( [E|0] \) 的回代，求出基变量关于自由变量的表达式得到 \( x_2 = -3x_3 \) 和 \( x_1 = -2x_2 - 2x_3 = 4x_3 \)，因此通解为：

\[
\begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = x_3 \begin{pmatrix} 4 \\ -3 \\ 1 \end{pmatrix}, \quad \text{其中} \ x_3 \ \text{是自由的}.
\]

也就是说，每个解都是一个特解 \( h_1 = \begin{pmatrix} 4 \\ -3 \\ 1 \end{pmatrix} \) 的倍数。

---

## 非齐次方程组

设 \( [A|b] \) 为一个一致的 \( m \times n \) 非齐次系统的增广矩阵，其中 \( \text{rank}(A) = r \)。

- 通过使用高斯消元法将 \( [A|b] \) 化简为行梯形形式，并求出基变量关于自由变量的表达式，得到**通解**（general solution）：

  \[
  x = p + x_{f_1} h_1 + x_{f_2} h_2 + \cdots + x_{f_{n-r}} h_{n-r}.
  \]

  当自由变量 \( x_{f_i} \) 取所有可能的值时，这个通解生成了系统的所有可能解。

- 列向量 \( p \) 是非齐次系统的一个特解。

- 表达式 \( x_{f_1} h_1 + x_{f_2} h_2 + \cdots + x_{f_{n-r}} h_{n-r} \) 是对应齐次系统的通解。

- 列向量 \( p \) 以及列向量 \( h_i \) 与 \( [A|b] \) 被化简到的行梯形形式无关。

- 系统当且仅当以下任意一项成立时具有唯一解：
  - \( \text{rank}(A) = n = \) 未知数的个数。
  - 没有自由变量。
  - 对应的齐次系统仅有平凡解。

**问题**：确定以下非齐次系统的通解，并将其与对应齐次系统的通解进行比较：

\[
x_1 + x_2 + 2x_3 + 2x_4 + x_5 = 1\\
2x_1 + 2x_2 + 4x_3 + 4x_4 + 3x_5 = 1\\
2x_1 + 2x_2 + 4x_3 + 4x_4 + 2x_5 = 2\\
3x_1 + 5x_2 + 8x_3 + 6x_4 + 5x_5 = 3
\]

**解答**：将增广矩阵 \( [A|b] \) 化简为 \( E_{[A|b]} \) 得到。

\[\mathbf{A}=\begin{pmatrix}1&1&2&2&1&1\\2&2&4&4&3&1\\2&2&4&4&2&2\\3&5&8&6&5&3\end{pmatrix}\longrightarrow\begin{pmatrix}1&1&2&2&1&1\\0&0&0&0&1&-1\\0&0&0&0&0&0\\0&2&2&0&2&0\end{pmatrix}\\
\longrightarrow\begin{pmatrix}1&1&2&2&1&1\\0&2&2&0&2&0\\0&0&0&0&1&-1\\0&0&0&0&0&0\end{pmatrix}\longrightarrow\begin{pmatrix}1&1&2&2&1&1\\0&1&1&0&1&0\\0&0&0&0&1&-1\\0&0&0&0&0&0\end{pmatrix}\\\longrightarrow\begin{pmatrix}1&0&1&2&0&1\\0&1&1&0&1&0\\0&0&0&0&1&-1\\0&0&0&0&0&0\end{pmatrix}\longrightarrow\begin{pmatrix}1&0&1&2&0&1\\0&1&1&0&0&1\\0&0&0&0&1&-1\\0&0&0&0&0&0\end{pmatrix}\]

可以看到系统是一致的，因为最后一列是非基列。通过将化简后的系统中基变量 \( x_1 \)、\( x_2 \) 和 \( x_5 \) 用自由变量 \( x_3 \) 和 \( x_4 \) 表示，得到：

\[\begin{aligned}
&x_1 = 1 - x_3 - 2x_4\\
&x_2 = 1 - x_3\\
&x_3 \ \text{是自由变量}\\
&x_4 \ \text{是自由变量}\\
&x_5 = -1
\end{aligned}\]

非齐次系统的通解为：

\[
x = \begin{pmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \\ x_5 \end{pmatrix} = \begin{pmatrix} 1 - x_3 - 2x_4 \\ 1 - x_3 \\ x_3 \\ x_4 \\ -1 \end{pmatrix} = \begin{pmatrix} 1 \\ 1 \\ 0 \\ 0 \\ -1 \end{pmatrix} + x_3 \begin{pmatrix} -1 \\ -1 \\ 1 \\ 0 \\ 0 \end{pmatrix} + x_4 \begin{pmatrix} -2 \\ 0 \\ 0 \\ 1 \\ 0 \end{pmatrix}
\]

对应的齐次系统的通解为：

\[
x = \begin{pmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \\ x_5 \end{pmatrix} = \begin{pmatrix} -x_3 - 2x_4 \\ -x_3 \\ x_3 \\ x_4 \\ 0 \end{pmatrix} = x_3 \begin{pmatrix} -1 \\ -1 \\ 1 \\ 0 \\ 0 \end{pmatrix} + x_4 \begin{pmatrix} -2 \\ 0 \\ 0 \\ 1 \\ 0 \end{pmatrix}
\]

