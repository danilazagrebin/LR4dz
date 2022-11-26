# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #4 выполнил:
- Загребин Данила Павлович
- РИ212702
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | # | 20 |

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
Познакомиться с работой перцептрона на практике, научиться настраивать его работу

## Задание 1
### В проекте Unity реализовать перцептрон, который умеет производить вычисления:
-OR
-AND
-NAND
-XOR
Ход работы:
- Создал проект Unity добавил скрипт-файл с перцептроном как компонент на GameObject. 
Для каждого из логических операторов настраивал массив ts (training set)

Результаты:

Для логического оператора OR достаточно 4 эпох обучения для корректной работы (Total Error: 0)
 
![image](https://user-images.githubusercontent.com/114522298/204098084-edaf9cc7-3362-4d00-9bb3-21a6fb6bc96c.png)

Для логического оператора AND достаточно 7 эпох обучения для корректной работы (Total Error: 0)

![image](https://user-images.githubusercontent.com/114522298/204098155-d88c15fc-5c44-44d9-8136-866a5f3a52cf.png)

Для логического оператора NAND достаточно 7 эпох обучения для корректной работы (Total Error: 0).

![image](https://user-images.githubusercontent.com/114522298/204098199-b9278142-0919-436c-9e5a-6c99e5fa14c0.png)

Для логического оператора XOR недостаточно даже 100 эпох обучения для корректной работы (Total Error: 4). Следовательно перцептрон не способен решить эту задачу.

![image](https://user-images.githubusercontent.com/114522298/204098168-4fd04fa2-ac0d-4540-891d-5496772c4fbb.png)

## Задание 2
### Реализовать запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы № 1. 
![image](https://user-images.githubusercontent.com/114522298/195174429-63e5768e-6ae2-48a0-a3c6-73f9652ec571.png)
![image](https://user-images.githubusercontent.com/114522298/195174459-35bd70f5-149e-498e-8258-06496ffbc93a.png)
#Import the required modules, numpy for calculation, and Matplotlib for drawing

Взял код из первой лабораторной и преобразовал его, чтобы связать с google таблицей.
```
import numpy as np
import gspread
gc = gspread.service_account(filename='lr-2-2-60c96be9dd05.json')
sh = gc.open("LR-2-2")
# define data, and change list to array
x = [3,21,22,34,54,34,55,67,89,99]
x = np.array(x)
y = [2,22,24,65,79,82,55,130,150,199]
y = np.array(y)


# define data, and change list to array
x = [3,21,22,34,54,34,55,67,89,99]
x = np.array(x)
y = [2,22,24,65,79,82,55,130,150,199]
y = np.array(y)

#The basic linear regression model is wx+ b, and since this is a two-dimensional space, the model is ax+ b

def model(a, b, x):
    return a*x + b

#Tahe most commonly used loss function of linear regression model is the loss function of mean variance difference
def loss_function(a, b, x, y):
    num = len(x)
    prediction=model(a,b,x)
    return (0.5/num) * (np.square(prediction-y)).sum()

#The optimization function mainly USES partial derivatives to update two parameters a and b
def optimize(a,b,x,y):
    num = len(x)
    prediction = model(a,b,x)
    #Update the values of A and B by finding the partial derivatives of the loss function on a and b
    da = (1.0/num) * ((prediction -y)*x).sum()
    db = (1.0/num) * ((prediction -y).sum())
    a = a - Lr*da
    b = b - Lr*db
    return a, b

#iterated function, return a and b
def iterate(a,b,x,y,times):
    for i in range(times):
        a,b = optimize(a,b,x,y)
    return a,b

#Initialize parameters and display
a = np.random.rand(1)
print(a)
b = np.random.rand(1)
print(b)
Lr = 0.000001

a,b = iterate(a,b,x,y,100)
prediction=model(a,b,x)
loss = loss_function(a, b, x, y)
print(a,b,loss)

mon = list(range(1,20))
i = 0
while i <= len(mon):
    i += 1
    if i == 0:
        continue
    else:
        a, b = iterate(a, b, x, y, 100)
        prediction = model(a, b, x)
        loss = loss_function(a, b, x, y)
        tempInf = str(loss)
        tempInf = tempInf.replace('.', ',')
        sh.sheet1.update(('A' + str(i)), str(i))
        sh.sheet1.update(('B' + str(i)), str(tempInf))
        print(tempInf)
```

## Выводы

В лабораторной работе я познакомился с такими сервисами, как Google Cloud, Google sheets. Также я научился связывать программу написанную на языке Python с таблицей google Sheets, еще я научился реализовывать совместную работу и передачу данных в связке Python - Google-Sheets – Unity.

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
