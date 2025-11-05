\documentclass{article}
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{amssymb}
\usepackage[utf8]{inputenc}
\usepackage[russian]{babel}

\begin{document}

\section*{Нахождение ранга матрицы методом Гаусса}

Дана матрица:
$$ A = \begin{pmatrix}
1 & 2 & -4 \\
-3 & t-8 & 15 \\
-4 & -t-10 & t+18
\end{pmatrix} $$

Приведем матрицу к ступенчатому виду с помощью элементарных преобразований строк.

\subsection*{Шаг 1: Обнуление элементов под первым ведущим элементом}
Выполним преобразования:
\begin{enumerate}
    \item $R_2 \leftarrow R_2 + 3R_1$
    \item $R_3 \leftarrow R_3 + 4R_1$
\end{enumerate}
$$ A \sim \begin{pmatrix}
1 & 2 & -4 \\
-3 + 3(1) & (t-8) + 3(2) & 15 + 3(-4) \\
-4 + 4(1) & (-t-10) + 4(2) & (t+18) + 4(-4)
\end{pmatrix} $$
$$ A \sim \begin{pmatrix}
1 & 2 & -4 \\
0 & t-8+6 & 15-12 \\
0 & -t-10+8 & t+18-16
\end{pmatrix} $$
$$ A \sim \begin{pmatrix}
1 & 2 & -4 \\
0 & t-2 & 3 \\
0 & -t-2 & t+2
\end{pmatrix} $$

\subsection*{Шаг 2: Обнуление элемента во втором столбце под вторым ведущим элементом}

\subsubsection*{Случай 1: $t-2 \neq 0 \implies t \neq 2$}
В этом случае $t-2$ является ведущим элементом. Выполним преобразование:
$R_3 \leftarrow (t-2)R_3 + (t+2)R_2$

Элементы третьей строки после преобразования:
\begin{itemize}
    \item Второй элемент: $(t-2)(-t-2) + (t+2)(t-2) = -(t-2)(t+2) + (t+2)(t-2) = 0$
    \item Третий элемент: $(t-2)(t+2) + (t+2)(3) = (t+2)((t-2)+3) = (t+2)(t+1)$
\end{itemize}
Матрица примет вид:
$$ A \sim \begin{pmatrix}
1 & 2 & -4 \\
0 & t-2 & 3 \\
0 & 0 & (t+2)(t+1)
\end{pmatrix} $$
Анализ ранга для $t \neq 2$:
\begin{itemize}
    \item Если $(t+2)(t+1) \neq 0$ (т.е., $t \neq -1$ и $t \neq -2$):
    Все три строки ненулевые. $\text{rank}(A) = 3$.
    \item Если $(t+2)(t+1) = 0$ (т.е., $t = -1$ или $t = -2$):
    Третья строка становится нулевой. Первые две строки ненулевые (так как $t \neq 2$, то $t-2 \neq 0$). $\text{rank}(A) = 2$.
\end{itemize}

\subsubsection*{Случай 2: $t-2 = 0 \implies t = 2$}
Подставим $t=2$ в матрицу, полученную после Шага 1:
$$ A \sim \begin{pmatrix}
1 & 2 & -4 \\
0 & 2-2 & 3 \\
0 & -2-2 & 2+2
\end{pmatrix} = \begin{pmatrix}
1 & 2 & -4 \\
0 & 0 & 3 \\
0 & -4 & 4
\end{pmatrix} $$
Поменяем местами вторую и третью строки ($R_2 \leftrightarrow R_3$):
$$ A \sim \begin{pmatrix}
1 & 2 & -4 \\
0 & -4 & 4 \\
0 & 0 & 3
\end{pmatrix} $$
Все три строки ненулевые. Следовательно, $\text{rank}(A) = 3$.

\subsection*{Окончательный вывод по рангу матрицы}
\begin{itemize}
    \item Если $t \neq -1$ и $t \neq -2$, то $\text{rank}(A) = 3$.
    \item Если $t = -1$ или $t = -2$, то $\text{rank}(A) = 2$.
\end{itemize}

\end{document}
