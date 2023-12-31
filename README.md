# project_teacher
<h1 align="center">Hi there, I'm <a href="https://daniilshat.ru/" target="_blank">Ahmetova Aliya</a> 
<img src="https://github.com/blackcater/blackcater/raw/main/images/Hi.gif" height="32"/></h1>
<h3 align="center">Computer science student from Russia 🇷🇺</h3>

## Задача: "Отток клиентов"
Из «Бета-Банка» стали уходить клиенты. Каждый месяц. Немного, но заметно. Банковские маркетологи посчитали: сохранять текущих клиентов дешевле, чем привлекать новых.

Нужно спрогнозировать, уйдёт клиент из банка в ближайшее время или нет. Предоставлены исторические данные о поведении клиентов и расторжении договоров с банком.

Необходимо построить модель с предельно большим значением F1-меры, не менее 0.59. Необходимо проверить F1-меру на тестовой выборке.

Дополнительно необходимо измерить AUC-ROC, сравнивая её значение с F1-мерой.

Источник данных: https://www.kaggle.com/barelydedicated/bank-customer-churn-modeling

## Этапы проделанной работы:
1. Предобработка данных:

- поиск пропущеннх значений и борьба с ними;
- поиск дубликатов и их устранение;
- построение графики и изучение корреляции в данных. 

Данные были разделены на признаки и целевой признак. Исxодные данные не сбалансированы, так как в целевом признаке значений про клиентов не покинувших банк больше (20 %), чем с ушедших (80 %).

2. Обучение моделей без учета дисбаланса.

- данные были разделены на три выборки: обучающую, валидационную и тестовую, в соотношении 3:1:1.
- были исследованы три модели:
    - модель "решающее дерево": подобран гиперпараметр `max_depth`
    - модель "случайный лес": подобраны гиперпараметры `max_depth` и `n_estimators`
    - модель "логистическая регрессия".
    
Наилучший результат показывали модели решающего дерева и случайного леса. 

3. Обучение моделей с учетом борьбы с дисбалансом.

Были исследованы те же три модели. Для борьбы с дисбалансом использовались следующие методы:

- взвешивание классов;
- увеличение выборки;
- уменьшение выборки;
- изменение порога классификации.

Сравнив полученные результаты для всех моделей и метолов борьбы с дисбалансом, было принято решение использовать метод случайного леса с предварительной борьбой с дисбалансом путем увеличения выборки, так как данное сочетание методов приводит к наибольшему значению метрик.

4. Тестирование модели

Было произведено тестирование выбранной модели, по итогу которго получено значение F1-меры равное ~0.61, что является хорошим результатом.

Была проведена проверка модели на адекватность. Для сравнеиня значений метрики была взята модель `DummyClassifier`. Значение ее метрики оказалось ниже, чем для выбранной нами модели случайного леса. Таким образом, модель случайног леса прошла проверку на адекватность.


