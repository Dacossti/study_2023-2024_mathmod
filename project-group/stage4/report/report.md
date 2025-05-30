---
# Front matter
lang: ru-RU
title: "Химические реакции, стохастическое горение"
subtitle: "Этап 4. Защита проекта"
author: "Озьяс Стев Икнэль Дани"

## Pdf output format
toc: true # Table of contents
toc-depth: 2
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
        - spelling=modern
        - babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Цель Работы"
lotTitle: "Ход Работы"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Обсуждать результаты проекта, самооценить деятельность.

# Результаты

В ходе моделирования были рассмотрены два предельных случая протекания мономолекулярной экзотермической реакции: при нулевой и бесконечной теплопроводности. 

- **При нулевой теплопроводности** температура системы оставалась постоянной, что привело к экспоненциальному убыванию числа активных частиц. Поведение системы полностью согласуется с аналитическим решением уравнения первого порядка:  

$$N(t) = N_0 e^{-ut}, \quad u = \frac{1}{\tau} e^{-E_a/kT}$$  

Это подтверждает корректность стохастической реализации в условиях стационарной температуры.

- **В случае бесконечной теплопроводности** (адиабатический процесс) каждое химическое превращение сопровождалось ростом температуры, что, в свою очередь, увеличивало скорость последующих реакций. Такой положительный обратный эффект может привести к лавинообразному увеличению реакционной активности — аналог теплового взрыва.

Графики температуры и скорости реакции от времени показали экспоненциально ускоряющийся процесс в начальной фазе, с последующим насыщением при исчерпании активных частиц.

- Полученные численные данные демонстрируют хорошее согласие с теоретическими ожиданиями. Это подтверждает корректность как математической модели, так и алгоритма Монте-Карло, использованного для генерации случайных величин.

# Самооценка

Проект был выполнен в полном объеме и охватывает все поставленные задачи: реализация стохастического моделирования химической реакции, сравнение различных тепловых режимов, визуализация результатов. 

Язык Julia продемонстрировал высокую производительность и лаконичность при работе с массивами, случайными величинами и графиками. Особенно полезным оказалось использование встроенного логарифмического генератора распределения экспоненциальных энергий.

Работа над проектом позволила глубже понять:
- физическую сущность экзотермических реакций,
- влияние тепловых эффектов на динамику реакций,
- принципы реализации стохастических моделей и численных методов решения дифференциальных уравнений.

# Перспективы

Возможные направления для расширения и дальнейших исследований:

- **Введение обратной реакции** (модель A ⇌ B) и учет химического равновесия.
- **Моделирование теплоотвода** — например, за счет конечной теплопроводности или теплообмена с окружающей средой.
- **Переход к двумолекулярным реакциям** (например, A + B → C), что потребует учета столкновений и пространственной плотности частиц.
- **Пространственное распределение частиц** и температурное поле, с возможностью моделирования локальных вспышек, диффузии тепла и фронта горения.

Такие расширения позволят приблизить модель к более реалистичным задачам, встречающимся в химической кинетике, горении и прикладной физике.

# Выводы

Во время выполнения итогового этапа проекта мы обсуждали результаты проекта, самооценили деятельность.

В ходе реализации проекта выполнили следующие задачи:

- Построение моделей химических реакций в условиях микроскопического ансамбля частиц в случаях нулевой теплопроводности и бесконечной теплопроводности;
- Описание алгоритмов решения задачи в обеих случаях;
- Создание программного комплекса на языке Julia для реализации задачи
- Обсуждение результата проекта, самооценка деятельности.


# Список литературы

1. Медведев Д.А. и др. Моделирование физических процессов и явлений на ПК: Учеб. пособие. Новосибирск: Новосиб. гос. ун-т, 2010. 101 с.
2. Gillespie D.T. Exact stochastic simulation of coupled chemical reactions. Journal of Physical Chemistry. — 1977. — Vol. 81, No. 25. — P. 2340–2361.
3. Yu C., Cai L., Chen J.-Y. Stochastic Modeling of Partially Stirred Reactor (PaSR) for the Investigation of the Turbulence-Chemistry Interaction for the Ammonia-Air Combustion. Flow, Turbulence and Combustion. — 2023. — Vol. 111. — P. 575–597.
