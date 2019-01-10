# Прогнозирование временных рядов

## Временные ряды

### Прогнозирование временного ряда

Временной ряд: <a href="https://www.codecogs.com/eqnedit.php?latex={\color{DarkOrange}&space;y_1,&space;...&space;y_T,&space;...,&space;y_T\in&space;\mathbb{R}^n,&space;}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_1,&space;...&space;y_T,&space;...,&space;y_T\in&space;\mathbb{R}^n,&space;}" title="{\color{DarkOrange} y_1, ... y_T, ..., y_T\in \mathbb{R}^n, }" /></a> - признак, измеренный через постоянные временные интервалы.

Задача прогнозирования - найти функцию <a href="https://www.codecogs.com/eqnedit.php?latex={\color{DarkOrange}&space;f_T:&space;y_{T&plus;d}&space;\approx&space;f_T(y_T,...y_1,d)&space;\equiv&space;\widehat{y}_{T&plus;d|T},}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;f_T:&space;y_{T&plus;d}&space;\approx&space;f_T(y_T,...y_1,d)&space;\equiv&space;\widehat{y}_{T&plus;d|T},}" title="{\color{DarkOrange} f_T: y_{T+d} \approx f_T(y_T,...y_1,d) \equiv \widehat{y}_{T+d|T},}" /></a> где <a href="https://www.codecogs.com/eqnedit.php?latex={\color{DarkOrange}&space;d&space;\in&space;{1,...,D}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;d&space;\in&space;{1,...,D}}" title="{\color{DarkOrange} d \in {1,...,D}}" /></a> - отсрочка прогноза, <a href="https://www.codecogs.com/eqnedit.php?latex={\color{DarkOrange}&space;D}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;D}" title="{\color{DarkOrange} D}" /></a> - горизонт прогнозирования

### Главная особенность временных рядов

* В классических задачах анализа данных предполагается независимость наблюдений, а про прогнозировании временных рядов, наоборот, мы надеемся, что значения ряда в прошлом содержат информацию о его поведении в будущем.

### Компоненты временных рядов
* __Тренд__ - плавное долгосрочное изменение уровня ряда
* __Сезонность__ - циклические изменения уровня ряда с постоянным периодом
* __Цикл__ - изменение уровня ряда с переменным периодом(экономические циклы, периоды солнечной активности)
* __Ошибка__ - непрогнозируемая случайная компонента ряда

## Автокорреляция

### Построение графиков

Построение графиков в осях <a href="https://www.codecogs.com/eqnedit.php?latex={\color{DarkOrange}&space;y_t,&space;y_{t&plus;k}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t,&space;y_{t&plus;k}}" title="{\color{DarkOrange} y_t, y_{t+k}}" /></a>, где k - период(например если измерения происходят каждй месяц, то при t=1 получим изменения относительно прошлого месяца)

### Автокорреляция

<a href="https://www.codecogs.com/eqnedit.php?latex={\color{DarkOrange}&space;r_\tau&space;=&space;\frac{&space;\mathbb{E}(&space;(y_t&space;-&space;\mathbb{E}y)&space;(y_{t&plus;\tau}&space;-&space;\mathbb{E}_y)&space;)&space;}{\mathbb{D}_y}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;r_\tau&space;=&space;\frac{&space;\mathbb{E}(&space;(y_t&space;-&space;\mathbb{E}y)&space;(y_{t&plus;\tau}&space;-&space;\mathbb{E}_y)&space;)&space;}{\mathbb{D}_y}}" title="{\color{DarkOrange} r_\tau = \frac{ \mathbb{E}( (y_t - \mathbb{E}y) (y_{t+\tau} - \mathbb{E}_y) ) }{\mathbb{D}_y}}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex={\color{DarkOrange}&space;r_\tau&space;\in&space;[-1,1],&space;\tau}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;r_\tau&space;\in&space;[-1,1],&space;\tau}" title="{\color{DarkOrange} r_\tau \in [-1,1], \tau}" /></a> - лаг автокрреляции

Выборочная автокорреляция:

<a href="https://www.codecogs.com/eqnedit.php?latex={\color{DarkOrange}&space;r_\tau&space;=&space;\frac{&space;\sum_{t=1}^{T-\tau}(&space;(y_t&space;-&space;\overline{y})&space;(y_{t&plus;\tau}&space;-\overline{y})&space;)&space;}{\sum_{t=1}^{T}(y_t&space;-&space;\overline{y})^2}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;r_\tau&space;=&space;\frac{&space;\sum_{t=1}^{T-\tau}(&space;(y_t&space;-&space;\overline{y})&space;(y_{t&plus;\tau}&space;-\overline{y})&space;)&space;}{\sum_{t=1}^{T}(y_t&space;-&space;\overline{y})^2}}" title="{\color{DarkOrange} r_\tau = \frac{ \sum_{t=1}^{T-\tau}( (y_t - \overline{y}) (y_{t+\tau} -\overline{y}) ) }{\sum_{t=1}^{T}(y_t - \overline{y})^2}}" /></a>

## Стационнарность

Ряд <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_1,&space;...&space;y_T&space;}" title="{\color{DarkOrange} y_1, ... y_T }" /> стационарен, если <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;\forall&space;s&space;}" title="{\color{DarkOrange} \forall s }" /> распределение <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t,&space;...&space;y_{t+s};}" title="{\color{DarkOrange} y_t, ... y_{t+s} }" /> не зависит от <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange} t}" title="{\color{DarkOrange} t}" />, т.е. его свойства не зависят от времени.

* __Тренд__ - нестационарен;
* __Сезонность__ - нестационарен;
* __Цикл__ - ?(нельзя предсказать заранее, где будут находиться максимумы и минимумы);

### Проверка стационарности

Осуществляется с помощью критерия Дики-Фулера

### Стабилизация 

* Для рядов с монотонно меняющейся дисперсией можно использовать стабилизирующие преобразования.
* Часто используют логарифмирвоание
* Либо дифференциирование.
* Дифференциирование ряда - переход к попарным разностям соседних значений: <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y'_t=y_t&space;-&space;y_{t-1}&space;}" title="{\color{DarkOrange} y'_t=y_t - y_{t-1} }" />. Это позволяет стабилизировать среднее значение ряда и избавиться от тренда. Может применяться неоднократно.
* Либо сезонной дифференциирование ряда - переход к попарным разностям значений в соседних сезонах: <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y'_t=y_t&space;-&space;y_{t-1}&space;}" title="{\color{DarkOrange} y'_t=y_t - y_{t-s} }" />. Это убирает сезонность.

### Рекомендуемый порядок

* Сезонное и обычное дифференциирования могут применяться к ряду в любом порядке.
* Если ряд имеет выраженный сезонный профиль, рекомендуется начинать с сезонного дифференциирования - после него ряд уже может оказаться стационарным.


## название

## название

## название

## название