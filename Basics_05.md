# 5. Стурктурные типы данных


## List (список)

### Создание списков

В python отсутствуют массивы в традиционном понимании этого термина. Вместо них для хранения однородных (и не только) объектов используются списки. Они задаются многими способами:

```python
# пустой список
>>>empty_list = []
# Простое перечисление:
>>> a = [2, 2.25, "Python"]
>>> a
[2, 2.25, 'Python']

# Преобразуем строку в список
>>> b = list("help")
>>> b
['h', 'e', 'l', 'p']

>>> b = 'welcome to the hell'.split()
>>> b
['welcome', 'to', 'the', 'hell']

```

### Операции срезов и вставок со списками

К спискам применимы все те срезы, что применимы к строкам. Более того, в списки таким образом можно еще и добавлять новые элементы.

```python
L = [1, 2, 's']
>>> L
[1, 2, 's']
>>> L[1:3]
[2, 's']
>>> L[2] = '17'
>>> L
[1, 2, '17']
>>> L[1:2]
[2]
>>> L[1:2] = ['new', 'list']
>>> L
[1, 'new', 'list', '17']
```

### Некоторые функции работы со списками

Ниже представлены примеры работы некоторых функций работы со списками:

```python
>>> L = list(range(1, 11))
>>> L
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> L.append(12) # Добавляет элемент в конец списка
>>> L
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12]
>>> L.extend([13, 14]) # Добавляет элементы второго списка в конец первого
>>> L
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 13, 14]
>>> L.insert(2, 5) # Вставляет на второе место цифру 5
>>> L
[1, 2, 5, 3, 4, 5, 6, 7, 8, 9, 10, 12, 13, 14]
>>> L.remove(5) # Удаляет первую встретившуюся пятерку
>>> L
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 13, 14]

# функция map применяет переданную ей функцию к списку
>>> L = list(map(str, range(1, 11)))
>>> L # В данном случае мы преобразовали в число все цифры
['1', '2', '3', '4', '5', '6', '7', '8', '9', '10']
>>> S = ': '.join(L) # склеивает строки в списке в одну, вызывается от разделителя
>>> S
'1: 2: 3: 4: 5: 6: 7: 8: 9: 10'
```

## Tuple (кортеж...)

Кортежи (англ. tuple) используется для представления неизменяемой последовательности разнородных объектов. Они обычно записываются в круглых скобках, но если неоднозначности не возникает, то скобки можно опустить.


```python
# Создаем tuple из разнородных элементов
>>> t = (2, 2.05, "Hello")
>>> t
(2, 2.05, 'Hello')
# Присваиваем трем переменным элементы tuple со скобками и без
>>> (a, b, c) = t
>>> print(a, b, c)
2 2.05 Hello
>>> z, y, x = t
>>> print(z, y, x)
2 2.05 Hello
# Создаем tuple из одного элемента
>>> x = 12,
>>> x
(12,)
# Создаем tuple без скобок
>>> tup = 1, 2, 'qwerty'
>>> tup
(1, 2, 'qwerty')
```

К кортежам применимы многие функции из тех, что применимы к спискам: получение длинны кортежа, конкатенация (склеивание) кортежа, срезы, методы **index** и **count**:

```python
>>> t = 1, 2, 3
>>> t = t + (4, 5)
>>> t
(1, 2, 3, 4, 5)
>>> t[:-1]
(1, 2, 3, 4)
>>> t[2:-1]
(3, 4)
>>> len(t)
5
>>> t.index(2)
1
>>> t.count(3)
1
```

Как видно из примера, кортеж может быть использован и в левой части оператора присваивания. Значения из кортежа в левой части оператора присваивания связываются с аналогичными элементами правой части. Этот факт как раз и дает нам такие замечательные возможности как массовая инициализация переменных и возврат множества значений из функции одновременно.

Чаще всего кортежи использую для получения данных из функции, хранения каких-то не меняющихся данных и т.п.
Чем привлекательна работа с ними:

- работа с ними быстрее(по сравнению со списками);
- занимают в памяти меньше места;
- могут выступать в качестве ключей для словаря;
- не имеют методов;
- используются для массовой инициализации переменных и возврата сразу нескольких значений из функции;


## Set (Множество)

Сеты — от математического 'множества' - неотсортированная коллекция уникальных элементов. В этом определении упомянуты две основные особенности сетов - **уникальность** и **отсутствие сортировки**.

Уникальность -  сет содержит только уникальные элементы, если добавлять в него дубликаты - они не добавляются, если перевести лист в сет - дублирующие элементы будут удалены.

Отсутствие сортировки - элементы в сете находятся в неком хаотичном порядке.

Множества поддерживают перебор всех элементов (итерацию), добавление и удаление элементов, но в силу отсутствия сортировки не поддерживают индексацию и срезы. Создание множеств:

```python
>>> a = {1, 2, 3, 4, 5, 4, 3, 4, 5, 6, 5, 4, 3}
>>> a
{1, 2, 3, 4, 5, 6}

>>> b = {1, 2, 3, 'a', 'c', 0.34}
>>> b
{0.34, 1, 2, 3, 'a', 'c'}
```

Множества поддерживают некоторые операции:

```python
>>> set1 = {1, 2, 3, 4, 5, 6}
>>> set2 = {5, 6, 7, 8, 9}
>>> set1 - set2 # Разность множеств
{1, 2, 3, 4}

>>> set1 | set2 # Объединение множеств
{1, 2, 3, 4, 5, 6, 7, 8, 9}

>>> set1 & set2 # Пересечение множеств
{5, 6}
```

Добавить элемент в множество можно при помощи функции **add**, а удалить из множества элемент - при помощи функции **remove**. В качестве параметра выступает сам элемент, поскольку индексов в множестве нет.

```python
>>> set1.add(7)
>>> set1
{1, 2, 3, 4, 5, 6, 7}
>>> set1.remove(1)
>>> set1
{2, 3, 4, 5, 6, 7, 8}
```

Сеты можно использовать для фильтрации дублей в коллекциях. Для этого коллекцию нужно сконвертировать в сет, а потом обратно:

```python
>>> L = [1, 2, 3, 4, 3, 2, 5, 6, 7, 5, 3, 2]
>>> L
[1, 2, 3, 4, 3, 2, 5, 6, 7, 5, 3, 2]
>>> L = list(set(L))
>>> L
[1, 2, 3, 4, 5, 6, 7]
```


Сеты можно использовать для работы с большими наборами данных:
допустим, у нас имеются базы данных программистов и менеджеров:

```python
>>> programmers = {'ivanov','petrov','sidorov'}
>>> managers = {'ivanov','moxov','goroxov'}
# И программист, и менеджер:
>>> programmers & managers
{'ivanov'}
# Все программисты и менеджеры:
>>> programmers | managers
{'ivanov', 'petrov', 'sidorov', 'goroxov', 'moxov'}
# Программисты, которые не менеджеры:
>>> programmers - managers
{'petrov', 'sidorov'}
```

## Dict (Словарь)

Словарь (хэш, ассоциативный массив) – **изменяемая и неупорядоченная** структура данных, предназначенная для хранения элементов вида **ключ: значение**. 

Значением элемента словаря может быть любой тип данных, ключем элемента - любой неизменяемый (immutable) тип данных, т.е. str, int, float, tuple и пр.

### Создание словаря

Есть несколько способов создать словарь: Прямое создание, создание при помощи преобразования в тип (используя функцию **dict**) и используя функцию **fromkeys**:

Рассмотрим все эти способы на примере:

```python
>>> d = {} # Создание пустого словаря напрямую
>>> d
{}
>>> d1 = {'a':1, 'b': 2} # Создание словаря напрямую
>>> d1
{'a': 1, 'b': 2}

# создание словаря при помощи функции dict:
>>> d = dict(short='dict', long='dictionary')
>>> d
{'short': 'dict', 'long': 'dictionary'}
>>> d = dict([(1, 1), (2, 4)])
>>> d
{1: 1, 2: 4}

# создание словаря при помощи функции fromkeys:
d = dict.fromkeys(['a', 'b', 1, (1, 2)])
>>> d
{'a': None, 1: None, 'b': None, (1, 2): None}
# с заполнением одним значением
>>> d = dict.fromkeys(['a', 'b', 1, (1, 2)], 4)
>>> d
{'a': 4, 1: 4, 'b': 4, (1, 2): 4}
```


У функции **dict** есть одна особенность, с ее помощью можно быстро создавать словари с ключами-строками, опуская кавычки. Это показано в примере ниже. К сожалению, работает только с явными строками, принцип формирования которых такой же, как и принцип наименования переменных:

```python
>>> dict(a=1, b=2, c=3, d=13)
{'a': 1, 'c': 3, 'b': 2, 'd': 13}
>>> dict(a=1, b=2, c=3, d=13, 1=2)
  File "<stdin>", line 1
SyntaxError: keyword can't be an expression
>>> dict(a=1, b=2, c=3, d=13, '1'=2)
  File "<stdin>", line 1
SyntaxError: keyword can't be an expression
```

### Операции со словарями

Со словарями доступны операции взятия элемента, удаления элемента, добавления элемента и его обновления:

```python
>>> d = dict(a=1, b=2, c=3, d=13)
>>> d
{'a': 1, 'c': 3, 'b': 2, 'd': 13}
>>> d['a']
1
>>> d[1] = 15
>>> d
{'a': 1, 1: 15, 'c': 3, 'b': 2, 'd': 13}
>>> del(d[1])
>>> d
{'a': 1, 'c': 3, 'b': 2, 'd': 13}
>>> d['a'] = 111
>>> d['a']
111
```
Взятие элемента из словаря по ключу лучше осуществлять не через квадратные скобки, а при помощи метода **.get()**. Если элемент отсутствует, обычное взятие по ключу выдаст ошибку, а метод **.get()** позволяет вам этого избежать:

```python
>>> d['a']
1
>>> d['e']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'e'
>>> d.get('e')
>>>
>>> d.get('e', 'No such element')
'No such element'
>>>
```

### Методы и функции для работы со словарями

```python
#Добавление элементов из другого словаря
>>> d
{'a': 1, 'c': 3, 'b': 2, 'd': 13}
>>> d.update({'4': 4, '5': 5})
>>> d
{'a': 1, 'c': 3, 'b': 2, '5': 5, 'd': 13, '4': 4}

#Количество пар в словаре
>>> len(d)
6

>>> d.keys() # Получить список ключей
['a', 'c', 'b', '5', 'd', '4']
>>> d.values() # Получить список значений
[1, 3, 2, 5, 13, 4]
>>> d.items() # Получить список элементов - кортежей
dict_items([('a', 1), ('c', 3), ('b', 2), ('d', 13), ('4', 4), ('5', 5)])
```


## Домашка

[Домашнее задание](hw5.md)
