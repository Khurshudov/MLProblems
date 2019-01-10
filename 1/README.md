# Прогнозирование временных рядов

## Временные ряды

Временной ряд: <a href="https://www.codecogs.com/eqnedit.php?latex={\color{DarkOrange}&space;y_1,&space;...&space;y_T,&space;...,&space;y_T\in&space;\mathbb{R}^n,&space;}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_1,&space;...&space;y_T,&space;...,&space;y_T\in&space;\mathbb{R}^n,&space;}" title="{\color{DarkOrange} y_1, ... y_T, ..., y_T\in \mathbb{R}^n, }" /></a> - признак, измеренный через постоянные временные интервалы.

Задача прогнозирования - найти функцию <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange} f_T: y_{T+d} \approx f_T(y_T,...y_1,d) \equiv \widehat{y}_{T+d|T},}" /> где <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange} d \in {1,...,D}}" /> - отсрочка прогноза, <img src="https://latex.codecogs.com/gif.latex?{\color{Red} D}" /> - горизонт прогнозирования