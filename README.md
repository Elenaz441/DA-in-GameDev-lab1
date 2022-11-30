# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #5 выполнил(а):
- Засыпкина Елена Юрьевна
- РИ210940
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Осуществить интеграцию экономической системы в проект Unity и обучить ML-Agent.

## Задание 1
### Измените параметры файла. yaml-агента и определить какие параметры и как влияют на обучение модели.

 - Запустила предоставленный проект на Unity. Добавила в проект ml-agents-release_19. Также ознакомилась с работой проекта.
 
 ![image](https://user-images.githubusercontent.com/102030455/204776954-a5b5ee76-a5b7-45fa-8312-506bbef2b838.png)
 
 - Запустила Anaconda Prompt. Активировала виртуальное окружение, которое было создано в лабораторной работе 3. перешла в папку с yaml-файлом. Запустила обучение.
 
 ![image](https://user-images.githubusercontent.com/102030455/204792280-a3832f18-0a62-4258-8365-9401cc8bfc9e.png)
 
 - Осуществилось обучение
 
 ![image](https://user-images.githubusercontent.com/102030455/204792498-a318b127-0e8c-493c-bd01-56680ed57948.png)
 
 - Результат обучения появился в соответствующей папке.
 
 ![image](https://user-images.githubusercontent.com/102030455/204794219-8487be7d-0df5-41df-8cb1-d7954d7f97c6.png)

- Построила графики для оценки результатов обучения в TensorBoard.

![image](https://user-images.githubusercontent.com/102030455/204803803-29ce03b7-07f8-4cf4-99cd-8c2a24dfad1e.png)

- Изменила параметр strength поменяв значение 1 на значение 5

![image](https://user-images.githubusercontent.com/102030455/204806734-d8c35f0c-e557-4b2b-b10d-a12c58c4ba0f.png)

- Изменила параметр gamma поменяв значение 0.99 на значение 0.5

![image](https://user-images.githubusercontent.com/102030455/204810896-f31783c9-b186-4785-9f47-bcb18f970797.png)

- Изменила параметр batch_size поменяв значение 1024 на значение 500

![image](https://user-images.githubusercontent.com/102030455/204814056-59720a09-29b8-469a-8243-98605c800141.png)

- Изменила параметр learning_rate поменяв значение 3.0e-4 на значение 2.0e-4

![image](https://user-images.githubusercontent.com/102030455/204817729-04a18d4d-f667-4670-b23c-16f7ccc1c51c.png)

- Изменила параметр time_horizon поменяв значение 64 на значение 32

![image](https://user-images.githubusercontent.com/102030455/204824555-3958a6d6-dcab-48dc-be2f-2857547cee10.png)


Вывод: при увеличении параметра strength и уменьшении параметра gamma и наблюдалось ухуджение обучения агента. При уменьшении time_horizon модель стала обучаться лучше. При изменении параметров batch_size и learning_rate обучение было либо успешным, либо некорректным (подробнее в задании 2).


## Задание 2
### Опишите результаты, выведенные в TensorBoard.


## Выводы
В ходе данной работы научилась работать с перцептроном. Обучила перцептрон некоторым логическим операциям (OR, AND, NAND). К сожалению, перцептрон способен обучиться не всему (например, модели поведения функции XOR он так и не обучился). Также был создан график зависимости количества эпох от ошибки обучения для каждой логической операции. Ещё была создана визуализация для функции NAND в Unity.


| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
