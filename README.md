# Artificial-intelligence-systems-in-robotics
Автор: Бадика Егор Максимович, группа 3021

# Комментарии по ЛР1

## Вопросы от преподавателя:
1) Почему для моделей так критичен параметр "Эта"?

   Ответ:

   Параметр "эта" определяет скорость нахождения глобального минимума и вообще возожности его найти:
   к примеру если параметр "эта" будет слишком велик, то при расчете градиента может произойти такое, что значение веса просто будет перескакивать через точку глобального минимума и никогда в нее не попадет.
   ![image](https://github.com/Embadika/Artificial-intelligence-systems-in-robotics/assets/126278168/48820cfd-c7aa-4035-89b4-7a38fd97c03d)
   На рискунке видно, что при большой параметре "эта" в начале обучения модель двигается к глобальному минимому, но в определенный момент из-за большого шага моедль не может дойти до требуемого значения.

   При маленьком "эта" обучение будет длиться дольше, но из-за маленького шага шанс попасть в глобальный минимум и решить задачу велик.

   Таким образом параметр "эта играет важную роль при разработке модели, так как он влияет на длительность обучения и точность результата.
   
3) Замерьте время обучения при минимальном и максимальном значении "Эта"? (%% Time) как сильно оно зависит от данного параметра. 

   Ответ:

   В ноутбуке написал код для проверки, можно найти его как задание 6 (находится ниже выводов).

   Создал два перцептрона: один с параметром "эта" равным 1.0, другой - 0.0. Также написал цикл, который 100 раз обучает каждый из перцептронов (у перцептрона в процессе обучения 100 итераций).

   Результаты показывают, что в среднем для 100 итераций разница между максимальным и минимальным параметром "эта" во времени обучения составляет 0.0026 секунды, что очень мало. Связанна эта разница во времени исключительно с внутренними операциями питона и распоряжением памятью.

## первую сдал!
   
# Комментарии по ЛР2
1)  Зачем ты масштабировал данные?

Ответ:

Как показывает практика, для получения более точных результатов, целесообразно использовать данные, которые по модулю расположены в значениях [0;1]. Благодаря таким операциям модели машинного обучения сходятся быстрее, так как зависят от скорости обучения (параметр "эта" для моделей машинного обучения или learning_rate для моледей нейронных сетей)

3)  какое скалирование можно применить к данным в которых есть больщое количество выбросов?

Ответ:

Применение масштабирования при борьбе с выборасами не сильно повышает качество данных

Пример: имеется база данных кандидатов на должности ML инженеров и одна из записей содержит в себе Junior разработчика с желаемой зарплатой 300 тысяч рублей. Данная запись, очевидно, является выбросом. Применение масштабирования для таких данных приведет к тому, что эта запись в любом случае будет учтена в модели. Допустим, возьмем MinMaxScaler, который приводит все значения в диапазон [0:1]. После его использование строка с зарплатой 300 000 руб. будет иметь значение, близкое к 1, а остальные ближе к 0.5, а то и 0. Таким образом, если мы будем исследовать такие данные далее, запись будет также выбросом, только с новым значением, переведённым в диапазон от 0 до 1.

Поэтому, при наличии большого количества выбросов, перед применением масштабирования, необходимо аномальные данные либо удалить (приведет к уменьшению базы данных, что не совсем хорошо), либо привести к нормальным значениям, заменив выброс на среднее значение для данной категории, либо на медианное. И после полученной базы данных без выбросов уже применять любые методы масштабирования.

Также, для игнорирования выбросов возможен второй вариант, но не могу сказать за его качество:

1) Провести масштабирование данных (любой вид MinMaxScaler, StandardScaler, MaxAbsScaler...)
2) Обучить модель машиного обучения, справляющуюся с выбросами самостоятельно, к примеры IsolationForest. Второй вариант - обучить нейронную сеть "автокодировщик", а точнее encoder, который сможет разбить данные на классы (кластеризовать), а далее, игнорировать выбросы настраивая параметр отклонения от стандартного распределения класса.

  ## Вторую сдал 

# Комментарии по ЛР3
1) зачем при делении указывать -stratify=y?

Ответ:

Параметр stratify позволяет разделить выборку таким образом, чтобы каждый из классов был равномерно распределен и в обучающей и в тестовой выборке. В значение параметра записывается матрица, по которой нужно сделать равномерное распределение между обучающей и тестовой выборкой. Конкретно в данной работе в качестве аргумента параметра stratify были использованы целевые метки. Таким образом в обучающей и в тестовой выборке процентное соотношение каждого из классов было примерно одинаковым.

2) как можно проверить баланс классов ?

Ответ:

- Проверка числа примернов на каждый класс, написав собственный код для анализа
- вывести классы графически в виде распределения на плоскости как в задании, либо столбчатая диаграмма, которая сама посчитает количество примеров на каждый класс и выведет это графически. Данный вариант будет нагляднее в плане картинки, а не сухих чисел
- анализ отношения классов относительно друг друга
- анализ разности между наибольшим и наименьшим классом по количеству примеров
- коэффициент Джини ![image](https://github.com/Embadika/Artificial-intelligence-systems-in-robotics/assets/126278168/50be31e1-00c2-40e8-825c-a9653b37a401) - значине расположено в пределах от 0 до 1. Чем ближе к 1,, тем более несбаллансированы классы.



3) random_state=2 - зачем указывать данный параметр? 

Ответ:

Данный параметр позволяет генерировать псевдослучайные данные всегда одинаковыми. Если параметр random_state=None, то при каждом запуске кода у нас будут генерироваться разные данные, а при значении random_state отличном от None, значение будет генерироваться всегда одно и то же. Это позволяет проводить эксперименты с уменьшением случайной ошибки, так как для каждой моледи данные будут одинаковые. Сам параметр random_state может быть любым целым числом

# Комментарии по ЛР4
