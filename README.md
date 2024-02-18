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
2)  какое скалирование можно применить к данным в которых есть больщое количество выбросов?

   Личная просба в конце названия примиши еще номер работы, что б я не вспоминал потом. Спасибо. 
