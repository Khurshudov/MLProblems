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

Ряд <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_1,&space;...&space;y_T&space;}" title="{\color{DarkOrange} y_1, ... y_T }" /> стационарен, если <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;\forall&space;s&space;}" title="{\color{DarkOrange} \forall s }" /> распределение <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t,&space;...&space;y_{t+s};}" title="{\color{DarkOrange} y_t, ... y_{t+s} }" /> не зависит от <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;t&space;}" title="{\color{DarkOrange} t }" />, т.е. его свойства не зависят от времени.

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


## ARMA

### Авторегрессия

Что если делать регрессию ряда на собственные значения в прошлом 

<img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\alpha&space;&plus;&space;\phi_1&space;y_{t-1}&space;&plus;&space;\phi_2&space;y_{t-2}&space;&plus;...&plus;&space;\phi_p&space;y_{t-p}&space;&plus;&space;\varepsilon_t}" title="{\color{DarkOrange} y_t=\alpha + \phi_1 y_{t-1} + \phi_2 y_{t-2} +...+ \phi_p y_{t-p} + \varepsilon_t}" />

Модель авторегрессии порядка <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;p,&space;(AR(p)):&space;y_p}" title="{\color{DarkOrange} p, (AR(p)): y_p}" /> - линейная комбинация <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;p}" title="{\color{DarkOrange} p}" /> предыдущих значений ряда и шумовой компоненты.

### Скользящее среднее

<img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\alpha&space;&plus;&space;\varepsilon_t&space;&plus;&space;\theta_1&space;\varepsilon_{t-1}&space;&plus;&space;\theta_2&space;\varepsilon_{t-2}&space;&plus;...&plus;&space;\theta_q&space;\varepsilon_{t-q}&space;}" title="{\color{DarkOrange} y_t=\alpha + \varepsilon_t + \theta_1 \varepsilon_{t-1} + \theta_2 \varepsilon_{t-2} +...+ \theta_q \varepsilon_{t-q} }" />

Модель скользящего среднего порядка <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;q,&space;(MA(q)):&space;y_t}" title="{\color{DarkOrange} q, (MA(q)): y_t}" /> - линейная комбинация <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;q}" title="{\color{DarkOrange} q}" /> последних значений шумовой компоненты

### ARMA

Модель ARMA(p,q): 

<img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\alpha&space;&plus;&space;\phi_1&space;y_{t-1}&space;&plus;...&plus;&space;\phi_p&space;y_{t-p}&space;&plus;&space;\varepsilon_t&space;&plus;&space;\theta_1&space;\varepsilon_{t-1}&space;&plus;&space;\theta_2&space;\varepsilon_{t-2}&space;&plus;...&plus;&space;\theta_q&space;\varepsilon_{t-q}&space;}" title="{\color{DarkOrange} y_t=\alpha + \phi_1 y_{t-1} +...+ \phi_p y_{t-p} + \varepsilon_t + \theta_1 \varepsilon_{t-1} + \theta_2 \varepsilon_{t-2} +...+ \theta_q \varepsilon_{t-q} }" />

__Теорема Вольда__: Любой стационарный ряд может быть описан моделью ARMA(p,q) с правильно подобранными параметра p и q;



## ARIMA

Модель ARIMA(p,d,q) - модель ARMA(p,q) для d раз продифференцированного ряда

### SARMA(p,q) x (P,Q) - сезонность

* Пусть ряд имеет сезонный период длины S
* Возммем модель ARMA(p,q) <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\alpha&space;&plus;&space;\phi_1&space;y_{t-1}&space;&plus;...&plus;&space;\phi_p&space;y_{t-p}&space;&plus;&space;\varepsilon_t&space;&plus;&space;\theta_1&space;\varepsilon_{t-1}&space;&plus;&space;\theta_2&space;\varepsilon_{t-2}&space;&plus;...&plus;&space;\theta_q&space;\varepsilon_{t-q}&space;}" title="{\color{DarkOrange} y_t=\alpha + \phi_1 y_{t-1} +...+ \phi_p y_{t-p} + \varepsilon_t + \theta_1 \varepsilon_{t-1} + \theta_2 \varepsilon_{t-2} +...+ \theta_q \varepsilon_{t-q} }" />
* и добавим в нее P авторегрессионных компонент: <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\phi_S&space;y_{t-S}&space;&plus;&space;\phi_{2S}&space;y_{t-2S}&space;&plus;...&plus;&space;\phi_{PS}&space;y_{t-PS}&space;}" title="{\color{DarkOrange} y_t=\phi_S y_{t-S} + \phi_{2S} y_{t-2S} +...+ \phi_{PS} y_{t-PS} }" />
* и Q компонент скользящего среднего: <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\theta_S&space;\varepsilon_{t-S}&space;&plus;&space;\theta_{2S}&space;\varepsilon_{t-2S}&space;&plus;...&plus;&space;\theta_{QS}&space;\varepsilon_{t-QS}&space;}" title="{\color{DarkOrange} y_t=\theta_S \varepsilon_{t-S} + \theta_{2S} \varepsilon_{t-2S} +...+ \theta_{QS} \varepsilon_{t-QS} }" />

### SARIMA

Модель SARIMA(p,d,q) x (P,D,Q) - модель SARMA(p,q) x (P,Q) для ряда, к которому d раз было применено обычное дифференцирование и D раз - сезонное


## Выбор параметров ARIMA

### Подбор параметров

* <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;\alpha,&space;\phi,&space;\theta&space;}" title="{\color{DarkOrange} \alpha, \phi, \theta }" />

  * Если все остальные параметры фиксированы, коэффициенты регрессии подбираются методом наименьших квадратов

  * Чтобы найти коэффициенты <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;\theta&space;}" title="{\color{DarkOrange} \theta }" />, шумовая компонента предварительно оценивается с помощью остатков авторегрессии
  * Если шум белый (независимый одинаково распределенный гауссовский), то МНК дает оценки максимального правдободобия

* <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;d,&space;D&space;}" title="{\color{DarkOrange} d, D }" />
  
  * Порядки дефференцирования подбираются так, чтобы ряд стал стационарынм
  * Ещё раз: если ряд сезонный, рекомендуется начинать с сезонного дифференцирования
  * Чем меньше раз мы продифференцируем, тем меньше будет дисперсия итогового прогноза

* <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;q,&space;Q,&space;p,&space;P&space;}" title="{\color{DarkOrange} q, Q, p, P }" />

  * Гиперпараметры нельзя выбирать из принципа максимума правдободобия, т.к. он будет всегда увеличиваться с их ростом.
  * Для сравнения моделей с разными <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;q,&space;Q,&space;p,&space;P&space;}" title="{\color{DarkOrange} q, Q, p, P }" /> можно использовать критерий Акаике: <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;AIC=-2\ln&space;L&space;&plus;&space;2k,&space;k&space;=&space;P&plus;Q&plus;p&plus;q&plus;1&space;}" title="{\color{DarkOrange} AIC=-2\ln L + 2k, k = P+Q+p+q+1 }" /> - число параметров модели
  * Начальные приближения можно выбрать с помощью автокорреляций


### Выбор начального приближения 

* <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;Q}" title="{\color{DarkOrange} Q}" /> - номер последнего сезонного лага, при котором автокорреляция значима

* <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;q}" title="{\color{DarkOrange} q}" /> - номер последнего несезонного лага, при котором автокорреляция значима

Частичная автокорреляци - автокорреляция после снятия авторегрессии предыдущего порядка

* <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;P}" title="{\color{DarkOrange} P}" /> - номер последнего сезонного лага, при котором частичная автокорреляция значима

* <img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;p}" title="{\color{DarkOrange} p}" /> - номер последнего несезонного лага, при котором частичная автокорреляция значима

### Подбор ARIMA

1. Смотрим на ряд.
2. При необходимости стабилизируем дисперсию (Преобразование Бокса-Кокса)
3. Если ряд нестационарен, подбираем порядок дифференцирвоания.
4. Анализируем ACF/PACF, определяем примерные p, q, P, Q
5. Обучаем модели-кандидаты, сравниваем их по AIC, выбираем победителя
6. Смотрим на остатки полученной модели, если они плохие, пробуем что-то поменять

### Прогнохирование

1. Пусть у нас есть модель с побобранными параметрами: 

<img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\hat{\alpha}&space;&plus;&space;\hat{\phi}_1&space;y_{t-1}&space;&plus;...&plus;&space;\hat{\phi}_p&space;y_{t-p}&space;&plus;&space;\varepsilon_t&space;&plus;&space;\hat{\theta}_1&space;\varepsilon_{t-1}&space;&plus;&space;...&space;&plus;&space;\hat{\theta}_q&space;\varepsilon_{t-q}}" title="{\color{DarkOrange} y_t=\hat{\alpha} + \hat{\phi}_1 y_{t-1} +...+ \hat{\phi}_p y_{t-p} + \varepsilon_t + \hat{\theta}_1 \varepsilon_{t-1} + ... + \hat{\theta}_q \varepsilon_{t-q}}" /> 

2. Для того чтобы построить прогноз на момент времени T+1, нужно просто в этом уравнении для начала заменить все индексы t на T+1: 

<img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\hat{\alpha}&space;&plus;&space;\hat{\phi}_1&space;y_{T}&space;&plus;...&plus;&space;\hat{\phi}_p&space;y_{T&plus;1-p}&space;&plus;&space;\varepsilon_{T&plus;1}&space;&plus;&space;\hat{\theta}_1&space;\varepsilon_{T}&space;&plus;&space;...&space;&plus;&space;\hat{\theta}_q&space;\varepsilon_{T&plus;1-q}}" title="{\color{DarkOrange} y_t=\hat{\alpha} + \hat{\phi}_1 y_{T} +...+ \hat{\phi}_p y_{T+1-p} + \varepsilon_{T+1} + \hat{\theta}_1 \varepsilon_{T} + ... + \hat{\theta}_q \varepsilon_{T+1-q}}" />

3. Заменяем будущие ошибки на нули: 

<img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\hat{\alpha}&space;&plus;&space;\hat{\phi}_1&space;y_{T}&space;&plus;...&plus;&space;\hat{\phi}_p&space;y_{T&plus;1-p}&space;&plus;&space;\hat{\theta}_1&space;\varepsilon_{T}&space;&plus;&space;...&space;&plus;&space;\hat{\theta}_q&space;\varepsilon_{T&plus;1-q}}" title="{\color{DarkOrange} y_t=\hat{\alpha} + \hat{\phi}_1 y_{T} +...+ \hat{\phi}_p y_{T+1-p} + \hat{\theta}_1 \varepsilon_{T} + ... + \hat{\theta}_q \varepsilon_{T+1-q}}" />

4. Заменяем прошлые ошибки на остатки:

<img src="https://latex.codecogs.com/gif.latex?{\color{DarkOrange}&space;y_t=\hat{\alpha}&space;&plus;&space;\hat{\phi}_1&space;y_{T}&space;&plus;...&plus;&space;\hat{\phi}_p&space;y_{T&plus;1-p}&space;&plus;&space;\hat{\theta}_1&space;\hat{\varepsilon}_{T}&space;&plus;&space;...&space;&plus;&space;\hat{\theta}_q&space;\hat{\varepsilon}_{T&plus;1-q}}" title="{\color{DarkOrange} y_t=\hat{\alpha} + \hat{\phi}_1 y_{T} +...+ \hat{\phi}_p y_{T+1-p} + \hat{\theta}_1 \hat{\varepsilon}_{T} + ... + \hat{\theta}_q \hat{\varepsilon}_{T+1-q}}" />


## название