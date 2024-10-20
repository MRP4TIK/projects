# Определение мошенических транзакций  
## Описание проекта  
Компании, выпускающие кредитные карты, могли распознавать мошеннические транзакции по кредитным картам, чтобы с клиентов не взималась плата за товары, которые они не покупали.Набор данных содержит транзакции, совершенные по кредитным картам в сентябре 2013 года европейскими держателями карт.
В этом наборе данных представлены транзакции, произошедшие за два дня, где у нас 492 мошенничества из 284 807 транзакций.
Нужно обучить модель, которая будет выявлять мошенничиские транзакции.  
## Этапы работы  
1. Загрузить и изучить данные на заявленное описание.   
2. Провести предобработку данных, те проверить на пропуски и дубликаты.  
3. Визуализировать признаки и проверить на выбросы.  
4. Проверить данные на мультиколлениарность.  
5. Построить несколько моделей и по результатам на кросс-валидации выбрать лучшую  
6. Обучить нейронную сеть и сравнить с результатом лучшей модели.  
7. Сделать выводы  
## Выводы  
В данной работе мной были получены следующие результаты:  
1. В данных не было пропусков, но содержались дубликаты, которые впоследствии мной были устранены.
2. В данных при помощи изоляционного леса были устранены выбросы для обычных операций, поскольку наша задача стоит в точности предсказания мошенничества, соотвественно выбросы для 0 класса мне будут только мешать.Выбросы для мошеннических операций были не тронуты.  
3. Наблюдается неравенство классов, соотвественно нужно будет использовать балансировку классов при обучении.
4. Интервал между первой и последующей транзакции для мошшенических операций ниже.  
5. Выбросы для класса 1 я оставил, поскольку они могут нести полезную информацию.
6. Признаки V1,V3,V6,V9,V10,V12,V14,V16,V17,V18 для мошеннических операций идут в целом ниже.
7. В данных наблюдается мультиколлениарность, соотвественно при обучение моделей нужно этот фактор учесть.
8. В целом наблюдается определенная граница между классами
9. Catboost является лучшей моделью для предсказания recall (полноты предсказний мошенничества).
10. Нейросеть лучше справляется с классификацией обычных транзакций, но чуть хуже выявляет мошенничество.

Для задачи, в которой приоритетом является максимальная точность выявления реальных мошеннических операций, я рекомендую использовать модель CatBoostClassifier.  
Однако, если в задаче важны как полнота (recall), так и точность (precision) в классификации мошеннических операций, то полносвязная нейронная сеть будет более подходящим выбором.