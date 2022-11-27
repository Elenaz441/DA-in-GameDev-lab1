# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #4 выполнил(а):
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
Познакомиться с работой перцептрона

## Задание 1
### В проекте Unity реализовать перцепторн, который умеет производить некоторые вычисления.
 - Создала пустой проект на Unity. Там был создан пустой объект, к которому был прикреплён скрипт-файл.

![image](https://user-images.githubusercontent.com/102030455/204128372-0edbfd9c-0c3c-4418-943a-15634c047ed1.png)
.
.

 - Далее присвоила значения так, чтобы перцептрон начал работать как функция OR:

 ![image](https://user-images.githubusercontent.com/102030455/204128564-417f32db-08ba-4e7e-b432-c6652f7c55c3.png)
 .
 .
 
 - Перцептрону хватило 4-х эпох, чтобы обучиться работать как функция OR. Все тесты пройдены:

![image](https://user-images.githubusercontent.com/102030455/204129015-52b95f63-16bc-446b-81b1-187018735ff1.png)
.
.
 - Далее ввела данные для функции AND. Перцептрону потребовалось 3-х эпох для обучения. Тесты пройдены:

![image](https://user-images.githubusercontent.com/102030455/204129242-7a43c86c-2189-47e3-8697-ab728e7f835b.png)
.
.
 - Далее ввела данные для функции NAND. Перцептрону потребовалось 6 эпох для обучения. Тесты пройдены:

![image](https://user-images.githubusercontent.com/102030455/204129390-7423086a-0bbf-45e0-a304-5b0da0d3879c.png)
.
.
 -  Далее ввела данные для функции XOR. Перцептрон не смог обучиться за 100 эпох. Тесты не пройдены:
 
![image](https://user-images.githubusercontent.com/102030455/204129525-d930dc6a-6342-479d-b1bf-557d570dc9a6.png)



## Задание 2
### Построить графики зависимости количества эпох от ошибки обучения. Указать от чего зависит необходимое количество эпох обучения.

![image](https://user-images.githubusercontent.com/102030455/204130402-9f042a16-1932-4ea9-bdf3-58345ef2d69a.png)

Количество эпох обучения зависит от смещения (bias) и веса переменных (weight).


## Задание 3
### Построить визуальную модель работы перцепторна на сцене Unity.

![image](https://user-images.githubusercontent.com/102030455/204132133-e4738037-06b7-4d4f-87ea-c3f5a450020f.png)

![image](https://user-images.githubusercontent.com/102030455/204132155-b0264992-cb0e-427e-83b2-0fef0e7f42cf.png)
![image](https://user-images.githubusercontent.com/102030455/204132156-6d76d417-657b-4e05-99ab-a78d9db886e7.png)
![image](https://user-images.githubusercontent.com/102030455/204132167-4d86e188-9371-4e54-83f6-baad5a357951.png)



## Выводы



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
