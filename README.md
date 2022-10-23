# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил(а):
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
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.
## Задание 1
### Реализовать систему машинного обучения в связке Python - Google-Sheets - Unity.
Ход работы:
- Создала новый пустой 3D проект на Unity.
- Скачала папку с ML агентом. В созданный проект добавила ML Agent, выбрав Window - Package
Manager - Add Package from disk. Последовательно добавила .json–файлы.

![13](https://user-images.githubusercontent.com/102030455/197362885-194a58f7-375f-4d4d-8f24-c2d2b4e993d7.JPG)


- Во вкладке с компонентами (Components) внутри Unity вы появилась строка ML Agent.
- Далее запустила Anaconda Prompt для возможности запуска команд  через консоль.
- Далее написала серию необходимых команд для создания и активации нового ML-агента, а также для скачивания необходимых библиотек.

![1](https://user-images.githubusercontent.com/102030455/197362943-8b44642c-a5f3-48c6-9051-c63b28841520.JPG)

![2](https://user-images.githubusercontent.com/102030455/197362944-0cad7fc1-5ce6-48cb-9234-6096e3d0f98a.JPG)

![3](https://user-images.githubusercontent.com/102030455/197362948-9c43acac-2fc5-43b7-809e-d6771a893d51.JPG)


- Создала на сцене плоскость, куб и сферу так. Потом создала C# скрипт-файл и подключите его к сфере. В скрипт-файл был загружен код, который представлен ниже:

![4](https://user-images.githubusercontent.com/102030455/197363022-18418c86-c54e-448b-924a-609b90898e1c.JPG)

```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    // Start is called before the first frame update
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }

    public Transform Target;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }

        Target.localPosition = new Vector3(Random.value * 8 - 4, 0.5f, Random.value * 8 - 4);
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);

        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition);

        if (distanceToTarget < 1.42f)
        {
            SetReward(1.0f);
            EndEpisode();
        }
        else if (this.transform.localPosition.y < 0)
        {
            EndEpisode();
        }
    }
}
```
- Объекту «сфера» добавила компоненты Rigidbody, Decision Requester, Behavior Parameters и настроила их.

![5](https://user-images.githubusercontent.com/102030455/197363218-6bd3f0fb-55f2-478c-ad58-355bfeb9ff85.JPG)

- В корень проекта добавила файл конфигурации нейронной сети, доступный в папке с файлами проекта.
```yaml
behaviors:
  RollerBall:
    trainer_type: ppo
    hyperparameters:
      batch_size: 10
      buffer_size: 100
      learning_rate: 3.0e-4
      beta: 5.0e-4
      epsilon: 0.2
      lambd: 0.99
      num_epoch: 3
      learning_rate_schedule: linear
    network_settings:
      normalize: false
      hidden_units: 128
      num_layers: 2
    reward_signals:
      extrinsic:
        gamma: 0.99
        strength: 1.0
    max_steps: 500000
    time_horizon: 64
    summary_freq: 10000
```

- Запустила работу ml-агента

![6](https://user-images.githubusercontent.com/102030455/197363327-20a9fe7f-5429-48bd-8f18-f956b50eb343.JPG)

![7](https://user-images.githubusercontent.com/102030455/197363342-ccdc1d28-f465-4bbd-bfa9-5629fd0d848e.JPG)

- Далее сделала 3, 9, 27 копий модели «Плоскость-Сфера-Куб» и запустила симуляцию сцены.

![8](https://user-images.githubusercontent.com/102030455/197363430-e56a4864-e65f-452f-8d2b-7e79b1d8e332.JPG)

![9](https://user-images.githubusercontent.com/102030455/197363433-91ee88ac-aa08-4900-a270-68f36c27734e.JPG)

![10](https://user-images.githubusercontent.com/102030455/197363437-bc228fd4-420d-42fa-b9ba-ee11441a195a.JPG)

- После завершения обучения проверила работу модели.

![12](https://user-images.githubusercontent.com/102030455/197363496-ab56fcf1-067f-4e5a-b995-5141cdea24f2.JPG)

- Выводы: после обучения модель начала катиться к кубику. Шарик начал быстрее находить кубик. Также шарик научился не падать за границы арены и иногда подпрыгивать при резкой смене направления.

## Задание 2
### Подробно описать каждую строку файла конфигурации нейронной сети, доступного в папке с файлами проекта. Самостоятельно найти информацию о компонентах Decision Requester, Behavior Parameters, добавленных на сфере.
- Фрагмент кода, представленный ниже, задает поведение шара (RollerBall):
```
behaviors:
  RollerBall:
```

- Эта строчка задает тип используемого тренажера:
```
    trainer_type: ppo
```

- Задаем гиперпараметры:
```
    hyperparameters:
```

- Количество опытов в каждой итерации градиентного спуска:
```
      batch_size: 10
```

- Количество опытов, которые необходимо собрать перед обновлением модели политики. Соответствует тому, сколько опыта должно быть собрано, прежде чем мы будем изучать или обновлять модель.
```
      buffer_size: 100
```

- Начальная скорость обучения для градиентного спуска. Соответствует силе каждого шага обновления градиентного спуска.
```
      learning_rate: 3.0e-4
```

- Сила регуляризации энтропии, которая делает политику «более случайной». Это гарантирует, что агенты должным образом исследуют пространство действия во время обучения.
```
      beta: 5.0e-4
```

- Эпсилан влияет на скорость изменения политики во время обучения. Соответствует допустимому порогу расхождения между старой и новой политикой при обновлении градиентного спуска.
```
      epsilon: 0.2
```

- Параметр регуляризации (лямбда), используемый при расчете обобщенной оценки преимущества (GAE). Это можно рассматривать как то, насколько агент полагается на свою текущую оценку стоимости при вычислении обновленной оценки стоимости.
```
      lambd: 0.99
```

- Количество проходов через буфер опыта при выполнении оптимизации градиентного спуска. Чем больше размер партии, тем больше это допустимо.
```
      num_epoch: 3
```

- Следующий параметр определяет, как скорость обучения изменяется с течением времени.
```
      learning_rate_schedule: linear
```

- Далее определяем сетевые настройки
```
    network_settings:
```

- Следующий параметр определяет применяется ли нормализация к входным данным векторных наблюдений. В нашем случае нет.
```
      normalize: false
```

- Количество единиц в скрытых слоях нейронной сети. Соответствуют количеству единиц в каждом полносвязном слое нейронной сети.
```
      hidden_units: 128
```

- Количество скрытых слоев в нейронной сети. Соответствует количеству скрытых слоев после ввода наблюдения или после кодирования CNN визуального наблюдения.
```
      num_layers: 2
```

- Далее задаем сигналы о вознаграждении:
```
    reward_signals:
```

- Задаем внешние награды:
```
      extrinsic:
```

- Фактор скидки для будущих вознаграждений, поступающих из окружающей среды. Это можно рассматривать как то, насколько далеко в будущем агент должен заботиться о возможных вознаграждениях.
```
        gamma: 0.99
```

- Коэффициент, на который умножается вознаграждение, данное средой.
```
        strength: 1.0
```

- Общее количество шагов (т. е. собранных наблюдений и предпринятых действий), которые необходимо выполнить в среде перед завершением процесса обучения.
```
    max_steps: 500000
```

- Этот параметр задает количество шагов опыта, которое необходимо собрать для каждого агента, прежде чем добавить его в буфер опыта. Когда этот предел достигается конца эпизода, оценка значения используется для прогнозирования общего ожидаемого вознаграждения из текущего состояния агента.
```
    time_horizon: 64
```

- Количество опытов, которое необходимо собрать перед созданием и отображением статистики обучения.
```
    summary_freq: 10000
```

#### Decision Requester: 
Компонент DecisionRequester автоматически запрашивает решения для экземпляра агента через регулярные промежутки времени.

#### Behavior Parameters: 
Компонент для настройки поведения экземпляра агента и свойств мозга.


## Задание 3
### Доработать сцену и обучите ML-Agent таким образом, чтобы шар перемещался между двумя кубами разного цвета. Кубы должны, как и в первом задании, случайно изменять координаты на плоскости.
Ход работы:
- В сцену был добавлен кубик другого цвет (фиолетовый), который стал второй целью шара:


![15](https://user-images.githubusercontent.com/102030455/197402183-e0565dad-c838-42fb-bb33-048004e05fbb.JPG)


- В скрипте была добалена новая цель (новый кубик). Для этой цели был написан необходимый код:
```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    // Start is called before the first frame update
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }

    public Transform Target;
    public Transform Target1;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }

        Target.localPosition = new Vector3(Random.value * 8 - 4, 0.5f, Random.value * 8 - 4);
        Target1.localPosition = new Vector3(Random.value * 8 - 4, 0.5f, Random.value * 8 - 4);
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);

        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition);
        float distanceToTarget1 = Vector3.Distance(this.transform.localPosition, Target1.localPosition);

        if (distanceToTarget < 1.42f || distanceToTarget1 < 1.42f)
        {
            SetReward(1.0f);
            EndEpisode();
        }
        else if (this.transform.localPosition.y < 0)
        {
            EndEpisode();
        }
    }
}
```

- После этого было запущено повторное обучение шарика. Теперь он должен научиться преследовать две цели.
- После обучения к RlloerAgent была привязана новая модель поведения. Теперь шарик умеет следовать за двумя целями.

## Выводы
Игровой баланс — субъективное «равновесие» между персонажами, командами, тактиками игры и другими игровыми объектами. Игровой баланс — одно из требований к «честности» правил. Существуют следующие парадигмы баланса: метода от образа; метода от характеристик. Выделают следующие виды баланса: сила, время, пространство, сложность. Системы машинного обучения могут использоваться для того, чтобы выявить дисбаланс в игре.
В этой лабораторной работе я научилась создавать систему машинного обучения и интегрировать её в Unity. 

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
