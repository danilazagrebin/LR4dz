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
Для каждого из логических операторов настраивал массив ts (training set) и подбирал необходимое количество эпох обучения.

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
### Построить графики зависимости количества эпох от ошибки обучения

![image](https://user-images.githubusercontent.com/114522298/204098701-8a099f8d-a076-4b9a-963a-972603aca33f.png)

Количество эпох обучения зависит от сложности логической операции, то есть чем сложнее задача, тем дольше нужно обучать модель, чтобы обработать как можнно больше вариантов решения. 

## Выводы

В лабораторной работе я познакомился с такой математической моделью как перцептрон, также я научился реализвывать его работу в среде Unity
на примере логических операторов: OR, AND, NAND, XOR.
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
