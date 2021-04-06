# Название семестровой работы

[![CMake](https://github.com/Algorithms-and-Data-Structures-2021/semester-work-splay-tree/actions/workflows/cmake.yml/badge.svg)](https://github.com/Algorithms-and-Data-Structures-2021/semester-work-splay-tree/actions/workflows/cmake.yml)

**_Измените status badge сверху для отображения статуса сборки вашего проекта._**

`Actions > CMake > ... > Create status badge`

_Краткое описание семестрового проекта. Следует отразить информацию по следующим пунктам:_

- _Какая структура данных реализуется?_
- _Что она из себя представляет (сбалансированное дерево, линейный список и пр.)?_
- _Где и как она используется (приложения)?_
- _Какие операции над ней можно выполнять (поиск, удаление, добавление, вставка и пр.)?_
- _Какова теоретическая сложность операций (поиск за `O(log(n))`, вставка за `O(n^2)` и т.д.)?_
- _Какая-то другая справочная информация о проекте._

- Структура данных - **Splay Tree**.
- Splay Tree — это самобалансирующееся бинарное дерево поиска. Дереву не нужно хранить никакой дополнительной информации, что делает его эффективным по памяти. После каждого обращения, даже поиска, splay tree меняет свою структуру и, за счет этого, оно позволяет находить быстрее те данные, которые использовались недавно. Splay tree не подходит для данных, которые редко или никогда не меняются, особенно в многопоточной среде. Они наиболее полезны для часто изменяемых структур данных.
- Пример использования - сетевой маршрутизатор. Сетевой маршрутизатор получает сетевые пакеты с высокой скоростью от входящих подключений и должен быстро решить, по какому исходящему проводу отправлять каждый пакет, на основе IP-адреса в пакете. Маршрутизатору нужна большая таблица (карта), которую можно использовать для поиска IP-адреса и определения того, какое исходящее соединение использовать. Если IP-адрес использовался один раз, он, вероятно, будет использоваться снова, возможно, много раз. В этой ситуации Splay-деревья могут обеспечить хорошую производительность.
- Операции:
1) **Splay (расширение)**
Основная операция дерева. Заключается в перемещении вершины в корень при помощи последовательного выполнения трёх операций: Zig, Zig-Zig и Zig-Zag.
-    a)zig
    Если p — корень дерева с сыном x, то совершаем один поворот вокруг ребра (x,p), делая x корнем дерева. Данный случай является крайним и выполняется только один раз в конце,     если изначальная глубина x была нечетной.
-    б)zig-zig
    Если p — не корень дерева, а x и p — оба левые или оба правые дети, то делаем поворот ребра (p,g), где g отец p, а затем поворот ребра (x,p).
-    в)zig-zag
    Если p — не корень дерева и x — левый ребенок, а p — правый, или наоборот, то делаем поворот вокруг ребра (x,p), а затем поворот нового ребра (x,g), где g — бывший родитель     p.
2) **Search (поиск элемента)**
Поиск выполняется как в обычном двоичном дереве поиска. При нахождении элемента запускаем Splay для него.
3) **Split (разделение дерева на две части)**
Для разделения дерева найдем наименьший элемент, больший или равный x, и сделаем для него Splay. После этого отрезаем у корня левого ребёнка и возвращаем 2 получившихся дерева.
4) **Merge (объединение двух деревьев)**
Для слияния деревьев T1 и T2, в которых все ключи T1 меньше ключей в T2, делаем Splay для максимального элемента T1, тогда у корня T1 не будет правого ребенка. После этого делаем T2 правым ребенком T1.
5) **Insert (добавление элемента)**
Вставка происходит как в обычном бинарном дереве поиска, после, запускаем Split() от добавляемого элемента и подвешиваем получившиеся деревья за него.
6) **Delete (удаление элемента)**
Находим элемент в дереве, делаем Splay для него, делаем текущим деревом Merge его детей.
- Сложность операций и требование по памяти:
Затраты по памяти - `O(n)`
Splay - `O(log(n))`
Search - `O(log(n))`
Split - `O(log(n))`
Merge - `O(log(n))`
Insert - `O(log(n))`
Delete - `O(log(n))`
- Splay tree предоставляет самоизменяющуюся структуру — структуру, характеризующуюся тенденцией хранить узлы, к которым часто происходит обращение, вблизи верхушки дерева, в то время как узлы, к которым обращение происходит редко, перемещаются ближе к листьям. Таким образом время обращения к часто посещаемым узлам будет меньше, а время обращения к редко посещаемым узлам — больше среднего. Splay Tree не обладает никакими явными функциями балансировки, но процесс скоса узлов к корню способствует поддержанию дерева в сбалансированном виде.
## Команда "название команды"

_Заполните таблицу с указанием вклада каждого из участников в проект._

**Примечание**. Преподаватель может определить вклад любого из участников команды по истории коммитов.

| Фамилия Имя   | Вклад (%) | Прозвище              |
| :---          |   ---:    |  ---:                 |
| Участник №1   | 50        |  _босс_               |
| Участник №2   | 40        |  _потрошитель памяти_ |
| Участник №3   | 10        |  _самозванец_         |

**Девиз команды**
> _Наши цели ясны. Задачи определены. За работу, товарищи!_

## Структура проекта

_Описание основных частей семестрового проекта._

**Пример**. Проект состоит из следующих частей:

- [`src`](src)/[`include`](include) - реализация структуры данных (исходный код и заголовочные файлы);
- [`benchmark`](benchmark) - контрольные тесты производительности структуры данных (операции добавления, удаления,
  поиска и пр.);
- [`examples`](examples) - примеры работы со структурой данных;
- [`dataset`](dataset) - наборы данных для запуска контрольных тестов и их генерация;

## Требования (Prerequisites)

_В этом разделе задаются основые требования к программному и аппаратному обеспечению для успешной работы с проектом._

**Пример**. Рекомендуемые требования:

1. С++ компилятор c поддержкой стандарта C++17 (например, _GNU GCC 8.1.x_ и выше).
2. Система автоматизации сборки _CMake_ (версия _3.12.x_ и выше).
3. Интерпретатор _Python_ (версия _3.7.x_ и выше).
4. Рекомендуемый объем оперативной памяти - не менее 4 ГБ.
5. Свободное дисковое пространство объемом ~ 3 ГБ (набор данных для контрольных тестов).

## Сборка и запуск

_Инструкция по сборке проекта, генерации тестовых данных, запуска контрольных тестов и примеров работы._

_Постарайтесь написать инструкцию так, чтобы незнакомый с проектом человек смог самостоятельно всё запустить._

### Пример (Windows)

#### Сборка проекта

_Опишите процесс сборки проекта._

Склонируйте проект к себе на устройство через [Git for Windows](https://gitforwindows.org/) (либо используйте
возможности IDE):

```shell
git clone https://github.com/Algorithms-and-Data-Structures-2021/semester-work-template.git
```

Для ручной сборки проекта в терминале введите:

```shell
# переход в папку с проектом
cd C:\Users\username\asd-projects\semester-work-template

# создание папки для файлов сборки (чтобы не засорять папку с проектом) 
mkdir -p build && cd build 

# сборка проекта
cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo && cmake --config RelWithDebInfo --build . 
```

#### Генерация тестовых данных

_Опишите формат хранения (JSON, XML, CSV, YAML и т.д.) и процесс генерации тестовых данных._

_Разрешается использовать собственный формат хранения данных._

Генерация тестового набора данных в
формате [comma-seperated values (CSV)](https://en.wikipedia.org/wiki/Comma-separated_values):

```shell
# переход в папку генерации набора данных
cd dataset

# запуск Python-скрипта
python generate_csv_bench_dataset.py --samples 1000 <output> [args ...]
```

- `--samples` - количество генерируемых элементов;
- `<output>` - выходной файл и т.д.

Тестовые данные представлены в CSV формате (см.
[`dataset/data/dataset-example.csv`](dataset/data/dataset-example.csv)):

```csv
id, full_name
0, "Ramil Safin"
1, "Bulat Abbyasov"
...
```

**Примечание**. Для удобства запуска контрольных тестов рекомендуется организовывать данные в директориях, например:

```shell
dataset/data/
  add/
    01/
      100.csv
      ...
      5000000.csv
    02/ ...
    03/ ...
    ...
    10/ ...
  search/
    01/
      100.csv
      ...
      5000000.csv
    ...
    10/ ...
  ...
```

По названию директории `/dataset/data/add` можно понять, что здесь хранятся наборы данных для контрольных тестов по
**добавлению** элементов в структуру данных. Названия файлов `100.csv`. `5000000.csv` и т.д. хранят информацию о размере набора данных (т.е. количество элементов). 

#### Контрольные тесты (benchmarks)

_Опишите, как запустить контрольные тесты, что они из себя представляют, какие метрики замеряют (время работы,
потребление памяти и пр.)._

Для запуска контрольных тестов необходимо предварительно сгенерировать или скачать готовый набор тестовых данных.

**Примечание**. Во избежание "захламления" репозитория большим объёмом данных рекомендуется указать ссылку на архив с
набором данных, который при необходимости можно скачать по ссылке. Наборы данных должны находиться в папке семестровой
работы на [Google Drive](https://drive.google.com/drive/folders/17-qridbMXFnz3E-6UjOj0WD1H0jWtpz3?usp=sharing).

##### Список контрольных тестов

| Название                  | Описание                                | Метрики         |
| :---                      | ---                                     | :---            |
| `random_search_benchmark` | поиск элементов по случайному индексу   | _время_         |
| `add_benchmark`           | добавление элементов в структуру данных | _время, память_ |
| ...                       | ...                                     | ...             |

##### Примеры запуска

```shell
./benchmark <input> <output> --trials 50
```

- `<input>` - входной файл с набором данных в формате CSV;
- `<output>` - выходной файл с результатами контрольного теста;
- `--trials` - количество прогонов на наборе данных и т.д.

Добавление 10000 случайных элементов в структуру данных (повторить операцию 50 раз и вычислить среднее время работы и
потребляемую память):

```
./add_benchmark.exe ../dataset/data/add/10000.csv metrics.txt --trials 50
``` 

где `<input> = ../dataset/data/add/10000.csv` и `<output> = metrics.txt`.

**Примечание**. Файл с метриками не обязателен, можете выводить данные в стандартный поток вывода (т.е. консоль).

## Источники

_Список использованных при реализации структуры данных источников._

_**Это не плагиат, это уважение чужого труда и помощь своим сокурсникам более подробно разобраться в теме.**_
