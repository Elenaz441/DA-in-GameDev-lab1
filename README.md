# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил(а):
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
Познакомиться с программными средствами для организции передачи данных между инструментами google, Python и Unity
## Задание 1
### Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity.
#### В облачном сервисе google console подключить API для работы с google sheets и google drive.
- Загрузила Google Drive API и Google Sheets API через Google Console:

![2](https://user-images.githubusercontent.com/102030455/194774453-9cef50d5-4553-4c27-ba0e-5645a2aa1700.jpg)


![3](https://user-images.githubusercontent.com/102030455/194774440-228d3793-1e32-4a08-98db-7dc7033c0c38.jpg)
.
.
- Далее создала Service Account, где был создан private key типа JSON, который потом будет использоваться в скрипте Python:

![8](https://user-images.githubusercontent.com/102030455/194774533-3a10072f-f9e6-4947-9711-6daead4c93ce.jpg)
.
.
- Далее я создала таблицу UnitySheets. В Service Account автоматически был создан email, который надо записать в настройках доступа Google-таблицы:

![12](https://user-images.githubusercontent.com/102030455/194774827-7138c906-2267-4cf0-bda3-a6579b8ec809.jpg)
.
.

#### Реализовать запись данных из скрипта на python в google-таблицу.
- В PyCharm был создан скрипт, данные которого описывают изменение темпа инфляции на протяжении 11 отсчётных периодов, с учётом стоимости игрового объекта в каждый период.

![image](https://user-images.githubusercontent.com/102030455/194774989-5f40357b-01b1-4b40-b360-fdf7c74f0e55.png)
.
.
- Привязка к таблице была добавлена через JSON (key) и название таблицы. Данные со скрипта выводятся в таблицу.

![13](https://user-images.githubusercontent.com/102030455/194775234-18e4a3e3-c30e-4093-92e3-227b1af59314.jpg)
.
.
#### Создать новый проект на Unity, который будет получать данные из google-таблицы, в которую были записаны данные в предыдущем пункте.
- В Unity Hub был создан новый проект, куда были загружены два пакета soundPackage и jsonPackage. В проекте был создан новый объект, к которому добавлен Audio Sourse.

![16](https://user-images.githubusercontent.com/102030455/194775502-ebed0714-0e5e-4f21-bbfe-7f8084eddd3f.jpg)
.
.
- Далее был написан скрипт для выгрузки данных из Google-таблицы.
#### Написать функционал на Unity, в котором будет воспризводиться аудио-файл в зависимости от значения данных из таблицы.
- Скрипт воспроизводит один из трёх аудиофйлов в зависимости от значения в таблице.

![17](https://user-images.githubusercontent.com/102030455/194775674-2b5d215a-897a-4dc8-b82a-16233229ecf7.jpg)
.
.
- Далее аудиозаписи были соотнесены с переменными скрипта. После запуска проекта 11 раз воспроизводятся соответствующие аудиозаписи.

![19](https://user-images.githubusercontent.com/102030455/194775799-1f06b805-bcbe-4833-b2e1-df5524fc441f.jpg)

![20](https://user-images.githubusercontent.com/102030455/194775814-b2680154-cf13-44d6-a2a7-5bb5ebeaf277.jpg)
.
.

## Задание 2
### Реализовать запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы № 1.


## Задание 3
### Самостоятельно разработать сценарий воспроизведения звукового сопровождения в Unity в зависимости от изменения считанных данных в задании 2.



## Выводы

Научилась делать вывод в консоль, используя Python и Unity (C#). Также был проведен небольшой анализ кода для ответа на вопросы.

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
