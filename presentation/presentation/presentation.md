---
## Front matter
lang: ru-RU
title: Доклад
subtitle: Программное решение обыкновенных дифференциальных уравнений
author:
  - Демидова Е. А.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 29 мая 2023

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Демидова Екатерина Алексеевна
  * студентка группы НКНбд-01-21
  * Российский университет дружбы народов
  * <https://github.com/eademidova>

:::
::: {.column width="30%"}

![](./image/ava.jpg)

:::
::::::::::::::

# Введение

## Цель работы

Исследовать программные решения обыкновенных дифференциальных уравнений.

## Задачи

- Описать метод Эйлера и методы Рунге-Кутты
- Исследовать возможности Octave и Julia для решения ОДУ
- Решить конкретную задачу Коши с помощью Octave и Julia
- Провести сравнительный анализ результатов

# Общие сведения о дифференциальных уравнениях

## Дифференциальное уравнение n-го порядка

$$F(x,y,y',y'',\dots,y^{(n)}) = 0$$

## Система дифференциальных уравнений первого порядка

$$
y'(x) = f_k(x,y(x)),\tag{1}
$$
$$
y = {y_1,y_2,\dots,y_n}, f = {f_1,f_2,\dots,f_n}.
$$

# Численные методы

# Метод Эйлера

## Метод Эйлера

Требуется найти функцию $y=y(x)$, являющуюся решением задачи Коши.

$$
y'(x)=f(x,y) \tag{1}
$$
$$
y(x_0) = y_0 \tag{2}
$$

## Метод Эйлера

Проведём разбиение отрезка $[x_0;x_n]$.

$$
x_i = x_0 + ih,  i = \overline{1,n}
$$
$$
h = \frac{x_n - x_0}{n}
$$

## Метод Эйлера

$$
y(x_1) = y(x_0 + h) = y(x_0) + y'(x_0)h+y''(x_0)\frac{h^2}{2}+\dots
$$

$$
y_2 = y_1+hf(x_1,y_1)
$$

$$
y_{i+1} = y_i + hf(x_i, y_i)
$$


# Методы Рунге-Кутты

## Схема метода

$$
 \textbf{y}_{n+1} = \textbf{y}_n + h\sum_{i=1}^n b_i \textbf{k}_i,
$$

$$
\begin{cases}
&\textbf{k}_1 = \textbf{f}(x_n, \textbf{y}_n),\\
&\textbf{k}_2 = \textbf{f}(x_n+c_2h, \textbf{y}_n+a_{21}h\textbf{k}_1),\\
&\dots\\
&\textbf{k}_s = \textbf{f}(x_n+c_sh, \textbf{y}_n+a_{s1}h\textbf{k}_1+a_{s2}h\textbf{k}_2+\cdots+a_{s,s-1}h\textbf{k}_{s-1}).
\end{cases}
$$

## Таблица Бутчера

\begin{table}
\caption{Таблица Бутчера}
\begin{center}
\begin{tabular}{c|ccccc}
 $c_1$ & $a_{11}$ & $a_{12}$ & $\dots$ & $a_{1s}$ \\ 
 $c_2$ & $a_{21}$ & $a_{22}$ & $\dots$ & $a_{2s}$ \\
 $\vdots$ & $\vdots$ & $\vdots$ & $\ddots$ & $\vdots$ \\  
 $c_s$ & $a_{s1}$ & $a_{s2}$ & $\dots$ & $a_{ss}$ \\ \hline
       & $b_1$    & $b_2$    & $\dots$ & $b_s$    \\
\end{tabular}
\end{center}
\end{table}

$\sum_{j=1}^{i-1} a_{ij} = c_i$ для  $i=2,\ldots,s$.


## Таблица Бутчера для метода Богацки-Шампина

\begin{table}
\caption{Таблица Бутчера для метода Богацки-Шампина}
\begin{center}
\begin{tabular}{c|cccc}
 $0$ &       &    &   &     \\
$\frac{1}{2}$& $\frac{1}{2}$&       &       &      \\
$\frac{3}{4}$&$0$&$\frac{3}{4}$&      &        \\
$1$& $\frac{2}{9}$&$\frac{1}{3}$&$\frac{4}{9}$&   \\ \hline
 &$\frac{2}{9}$&$\frac{1}{3}$&$\frac{4}{9}$&$0$\\ 
 &$\frac{7}{24}$&$\frac{1}{4}$&$\frac{1}{3}$&$\frac{1}{8}$\\ 
\end{tabular}
\end{center}
\end{table}

# Решение задачи Коши с помощью программных средств

## Рассматриваемая задача Коши

$$\begin{cases}
&y'(x) = 11y +e^{10x}+x^4+x^3-sin(x)\\
&y(0) = 5 
\end{cases}$$

## Точное решение

$$y(x) = - \dfrac{x^4}{11} - \dfrac{15x^3}{121} - \dfrac{45x^2}{1331} - \dfrac{90x}{14641} + \dfrac{cos(x)}{122} + \dfrac{11sin(x)}{122} + \dfrac{117739261e^{11x}}{19648222} - e^{10x} -\dfrac{90}{161051}$$

# Решение задачи Коши с помощью Octave

## Методы решения в Octave

- `ode23(@f, interval, X0, options)` -- метод Богацки-Шампина
- `ode45(@f, interval, X0, options)` -- метод Дормана-Принса

Опции:

- `RelTol` -- относительная точность решения
- `AbsTol` -- абсолютная точность решения
- `InitialStep` -- начальное значение шага
- `MaxStep` -- максимальное значение шага

## Решение методом Богацки-Шампина в Octave

```julia
function dydx = f(x,y)
  dydx = y*11 +exp(10*x)+(x^4+x^3)-sin(x);
endfunction

[X23,Y23]=ode23(@f,[0 0.5],5);
```


## Решение методом Богацки-Шампина в Octave


![Графики решения методом ode23() и точного решения](image/rel23_octave.png){#fig:001 width=60%}


## Решение методом Дормана-Принса в Octave

```julia
function dydx = f(x,y)
  dydx = y*11 +exp(10*x)+(x^4+x^3)-sin(x);
endfunction

[X45,Y45]=ode45(@f,[0 0.5],5);
```

## Решение методом Дормана-Принса в Octave


![Графики решения методом ode45() и точного решения](image/rel45_octave.png){#fig:002 width=70%}

# Решение задачи Коши с помощью Julia

## Инструменты для решения в Julia

- `ODEProblem(f::ODEFunction,u0,tspan,p=NullParameters();kwargs...)` 

- `solve(prob, alg; kwargs)`

  - `BS3()` -- соответствует `ode23()`
  - `DP5()` -- соответствует `ode45()`

## Решение методом Богацки-Шампина в Julia

```julia
function F!( y, p, x)
 	dydx = x*11+exp(10*x)+(x.^4+x.^3)-sin(x);
end

begin
	x0 = 5.0
	X = (0.0, 0.5)
	prob = ODEProblem(F!, y0, x)
end

sol = solve(prob, BS3(), dtmax=0.025, dt=0.025, abstol = 1e-3, reltol = 1e-3);
```

## Решение методом Богацки-Шампина в Julia


![Графики решения методом BS3() и точного решения](image/rel23_julia.png){#fig:003 width=70%}


## Решение методом Дормана-Принса в Julia

```julia
function F!( y, p, x)
 	dydx = x*11+exp(10*x)+(x.^4+x.^3)-sin(x);
end

begin
	x0 = 5.0
	X = (0.0, 0.5)
	prob = ODEProblem(F!, y0, x)
end

sol = solve(prob, DP5(), dtmax=0.025, dt=0.025, abstol = 1e-3, reltol = 1e-3);

```

## Решение методом Дормана-Принса в Julia


![Графики решения методом DP5() и точного решения](image/rel45_julia.png){#fig:004 width=70%}

# Сравнительный анализ решений

## Сравнение решений методом Богацки-Шампина

![Абсолютные погрешности](image/error23.png){#fig:005 width=70%}

## Сравнение решений методом Богацки-Шампина

![Найденные точки решения](image/sol23_scatter.png){#fig:006 width=70%}

## Сравнение решений методом Богацки-Шампина

![Найденные решения](image/sol23.png){#fig:007 width=70%}

## Сравнение решений методом Дормана-Принса

![Абсолютные погрешности](image/error45.png){#fig:008 width=70%}

## Сравнение решений методом Дормана-Принса

![Найденные точки решения](image/sol45_scatter.png){#fig:009 width=70%}

## Сравнение решений методом Дормана-Принса

![Найденные решения](image/sol45.png){#fig:010 width=70%}

# Выводы

- Программные решения достаточно точно решают задачу Коши
- Julia решает точнее Octave

## Список литературы

1. Понтрягин Л.С. Дифференциальные уравнения и их приложения. Наука, 1988. 207 с.
2. Калиткин Н.Н. Численные методы. Наука, 1978. 512 с.
3. GNU Octave Documentation [Электронный ресурс]. Free Software Foundation, 2023. URL: https://docs.octave.org/v4.2.0/Matlab_002dcompatible-solvers.html.
4. Julia Documentation [Электронный ресурс]. JuliaLang.org contributors, 2023. URL: https://docs.sciml.ai/DiffEqDocs/stable/.