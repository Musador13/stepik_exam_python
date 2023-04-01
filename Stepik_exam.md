# [Итоговая работа на кортежи](https://stepik.org/lesson/416759/step/1?unit=406267) 

## Каждый n-ый элемент



```python
s = input().split(' ')
n = int(input())
arr = [[s[i] for i in range(j, len(s), n)] for j in range(n)]
print(arr)
```

     a b c d e f g h i j k l m n
     3
    

    [['a', 'd', 'g', 'j', 'm'], ['b', 'e', 'h', 'k', 'n'], ['c', 'f', 'i', 'l']]
    

## Максимальный в области 2



```python
# i > N-1-j
n = int(input())
arr = [[int(i) for i in input().split()] for _ in range(n)]
s = [arr[i][j] for i in range(n) for j in range(n) if i >= n-1-j]
print(max(s))

```

     3
     1 4 5
     6 7 8
     1 1 6
    

    8
    

## Транспонирование матрицы



```python
def print_matrix(matrix, rows, cols=None, width=1):
    if cols is None:
        cols = rows
        
    for r in range(rows):
        for c in range(cols):
            print(str(matrix[c][r]).ljust(width), end=' ')
        print()

n = int(input())
arr = [[int(i) for i in input().split()] for _ in range(n)]

print_matrix(arr, n)
```

     3
     1 2 3
     4 5 6
     7 8 9
    

    1   4   7   
    2   5   8   
    3   6   9   
    

## Снежинка


```python
def print_matrix(matrix, rows, cols=None, width=1):
    if cols is None:
        cols = rows
        
    for r in range(rows):
        for c in range(cols):
            print(str(matrix[r][c]).ljust(width), end=' ')
        print()

n = int(input())
arr = [['*' if (i == n//2 or j==n//2 or i == j or i == n-1-j)
        else '.'  for i in range(n)] for j in range(n)]

print_matrix(arr, n)
```

     11
    

    * . . . . * . . . . * 
    . * . . . * . . . * . 
    . . * . . * . . * . . 
    . . . * . * . * . . . 
    . . . . * * * . . . . 
    * * * * * * * * * * * 
    . . . . * * * . . . . 
    . . . * . * . * . . . 
    . . * . . * . . * . . 
    . * . . . * . . . * . 
    * . . . . * . . . . * 
    

## Симметричная матрица



```python
n = int(input())
matrix = [[int(i) for i in input().split()] for j in range(n)]
flag = True

for i in range(n):
    for j in range(n):
        if i + j + 1 < n:
            if matrix[i][j] != matrix[n - 1 - j][n - 1 - i]: 
                flag = False
    if flag == False:
        print('NO')
        break
else:
    print('YES')
```

     3
     0 3 10
     4 9 3
     7 4 0
    

    YES
    

## Латинский квадрат 🌶️



```python
n = int(input())
matrix = [[int(i) for i in input().split()] for j in range(n)]
t_matrix = [[matrix[i][j] for i in range(n)] for j in range(n)]
chk = list(range(1, n+1))
flag = True

for i in range(n):
    if sorted(matrix[i]) == chk and sorted(t_matrix[i]) == chk:
        continue
    else:
        flag = False
        break

if flag:
    print('YES')
else:
    print('NO')
```

     3
     1 2 3
     2 3 1
     3 1 2
    

    YES
    

## Ходы ферзя



```python
def print_matrix(matrix, rows, cols=None, width=1):
    if cols is None:
        cols = rows
        
    for r in range(rows):
        for c in range(cols):
            print(str(matrix[r][c]).ljust(width), end=' ')
        print()
        
matrix = [['.' for _ in range(8)] for h in range(8)]
j, i = input()
j = (ord(j) - 97)
i = 8 - int(i)

for a in range(8):
    for b in range(8):
        if abs(a - i) == abs(b - j) or a == i or b == j:
            matrix[a][b] = '*'
        else:
            continue
matrix[i][j] = 'Q'

            
print_matrix(matrix, 8)
```

     a1
    

    * . . . . . . * 
    * . . . . . * . 
    * . . . . * . . 
    * . . . * . . . 
    * . . * . . . . 
    * . * . . . . . 
    * * . . . . . . 
    Q * * * * * * * 
    

## Диагонали параллельные главной




```python
def print_matrix(matrix, rows, cols=None, width=1):
    if cols is None:
        cols = rows
        
    for r in range(rows):
        for c in range(cols):
            print(str(matrix[r][c]).ljust(width), end=' ')
        print()
        
n = int(input())
matrix = [[0 if j == i else abs(i-j) for i in range(n)] for j in range(n)]
print_matrix(matrix, n)
```

     5
    

    0 1 2 3 4 
    1 0 1 2 3 
    2 1 0 1 2 
    3 2 1 0 1 
    4 3 2 1 0 
    

# [Итоговая работа на множества](https://stepik.org/lesson/479453/step/1?unit=470428)

## Домашнее задание
Учитель проверяет домашнее задание в классе и получил следующие ответы: из n школьников у m домашнее задание съела собака, у k отключили свет, а p учеников постигли оба несчастья. Напишите программу, которая определяет сколько человек выполнило домашнее задание.


```python
n, m, k, p = [int(input()) for _ in range(4)]
res = n - (m - p) - (k - p) - p
print(res)
```

     81
     25
     16
     9
    

    49
    

## Восход
На спутнике «Восход» установлен прибор для измерения солнечной активности. Каждую минуту он передаёт в обсерваторию по каналу связи положительное целое число — количество энергии солнечного излучения. Для правильного анализа результатов нет необходимости держать повторяющиеся данные. Напишите программу, которая выводит максимальное количество показаний спутника, при удалении которых результат будет правильно проанализирован.



```python
s = list(map(int, input().split()))
print(len(s) - len(set(s)))
```

     100 100 100 100 100 100 100
    

    6
    

## Города
Тимур и Руслан играют в игру города. Они очень любят эту игру и знают много городов, особенно Тимур, однако к концу игры ввиду своего возраста забывают, какие города уже называли.

Напишите программу, считывающую информацию об игре и сообщающую ребятам, что очередной город назван повторно.


```python
s = {input() for _ in range(int(input()))}

if input() in s:
    print('REPEAT')
else:
    print('OK')

```

     3
     Каир
     Рим
     Москва
     Агра
    

    OK
    

## Книги на прочтение
Руслан получил в конце учебного года список литературы на лето. Теперь ему надо выяснить, какие книги из этого списка у него есть. У Руслана на компьютере в текстовом файле записаны все книги из его домашней библиотеки в случайном порядке.

Напишите программу, определяющую для каждой книги из списка на прочтение, есть она у Руслана или нет.


```python
m, n = [int(input()) for _ in range(2)] 

home_lib = [input() for _ in range(m)]
arr_book = [input() for _ in range(n)]

[print('YES') if arr_book[i] in home_lib else print('NO') for i in range(n)]

```

     4
     4
     Хоббит
     Алиса в стране чудес
     Том Сойер
     Остров сокровищ
     Буратино
     Хоббит
     Остров сокровищ
     Война и мир
    

    NO
    YES
    YES
    NO
    




    {None}



## Странное увлечение
Напишите программу, которая находит общие числа двух листочков или сообщает, что день не удался


```python
a, b = [list(map(int, input().split())) for _ in range(2)]
if len(set(a).intersection(set(b))) != 0:
    print(*sorted(set(a).intersection(set(b)), reverse=True))
else:
    print('BAD DAY')
```

    6 7
    


```python
a, b = [list(map(int, input().split())) for _ in range(2)]
z = set(a).issubset(set(b))
print(z)
# if :
#     print('YES')
# else:
#     print('NO')
```

     8 7
     6 7 7 8
    

    True
    


```python
a, b = [list(map(int, input().split())) for _ in range(2)]
x = (set(a).difference(b))
# print(x)
if len(x) == 0 and len(set(a)) == len(set(b)):
    print('YES')
else:
    print('NO')
```

     8 7
     6 7 7 8
    

    NO
    


```python
m, n = [int(input()) for _ in range(2)] 

arr1 = [input() for _ in range(m)]
arr2 = [input() for _ in range(n)]

res = m - len(set(arr1).intersection(set(arr2)))
print(res)
```

     2
     3
     Хохлов
     Фадеев
     Ушаков
     Ершов
     Хохлов
    

    1
    ['Хохлов', 'Фадеев'] ['Ушаков', 'Ершов', 'Хохлов']
    


```python
m, n = [int(input()) for _ in range(2)] 

arr1 = [input() for _ in range(m)]
arr2 = [input() for _ in range(n)]
res = (m + n) - 2 * len(set(arr1).intersection(set(arr2))) 

if res != 0:
    print(res)
else:
    print('NO')
```


```python
a, b = [set(input().split()) for _ in range(2)]
print(*sorted(a.union(b)))
```

     Рыбаков
     Сафонов Игнатов
    

    Игнатов Рыбаков Сафонов
    

## [Онлайн-школа BEEGEEK 5 🌶️](https://stepik.org/lesson/445985/step/11?unit=470426)


```python
m, n = [int(input()) for _ in range(2)] 
arr = [input() for _ in range(m + n)]

res = len(set(arr)) - ((m + n) - len(set(arr))) 

if res != 0:
    print(res)
else:
    print('NO')
```

     3
     3
     Иванов
     Петров
     Васечкин
     Иванов
     Петров
     Васечкин
    

    NO
    

## [Онлайн-школа BEEGEEK 6 🌶️](https://stepik.org/lesson/445985/step/12?unit=470426)
Руководителю онлайн-школы BEEGEEK захотелось узнать, кто из его учеников присутствовал на всех уроках с начала учебного года. Для каждого урока есть листок со списком присутствовавших учеников.

Напишите программу, определяющую фамилии учеников, которые присутствовали на всех уроках.


```python
from functools import reduce

m = int(input())

arr = [set(input() for i in range(int(input())))
       for _ in range(m)]

res = reduce((lambda x, y: set(x).intersection(y)), arr)
print(*sorted(res), sep='\n')
```

     3
     3
     Князев
     Сафонов
     Майоров
     2
     Князев
     Майоров
     1
     Майоров
    

    [{'Сафонов', 'Майоров', 'Князев'}, {'Майоров', 'Князев'}, {'Майоров'}]
    {'Сафонов', 'Майоров', 'Князев'}
    <class 'list'>
    

# [Итоговая работа на словари](https://stepik.org/lesson/491382/step/1?unit=482676)



```python
d = dict([('foo', 100), ('bar', 200), ('baz', 300)])
```


```python
data = ['a','b',{'foo': 1,'bar':{'x' : 10,'y' : 20,'z' : 30},'baz': 3},'c','d']
```


```python
my_dict = {'C1': [10, 20, 30, 7, 6, 23, 90], 'C2': [20, 30, 40, 1, 2, 3, 90, 12], 'C3': [12, 34, 20, 21], 'C4': [22, 54, 209, 21, 7], 'C5': [2, 4, 29, 21, 19], 'C6': [4, 6, 7, 10, 55], 'C7': [4, 8, 12, 23, 42], 'C8': [3, 14, 15, 26, 48], 'C9': [2, 7, 18, 28, 18, 28]}
my_dict = {k: [i for i in v if i <= 20] for k, v in my_dict.items()}
print(my_dict)
```

    {'C1': [10, 20, 7, 6], 'C2': [20, 1, 2, 3, 12], 'C3': [12, 20], 'C4': [7], 'C5': [2, 4, 19], 'C6': [4, 6, 7, 10], 'C7': [4, 8, 12], 'C8': [3, 14, 15], 'C9': [2, 7, 18, 18]}
    


```python
emails = {'nosu.edu': ['timyr', 'joseph', 'svetlana.gaeva', 'larisa.mamuk'], 
          'gmail.com': ['ruslan.chaika', 'rustam.mini', 'stepik-best'], 
          'msu.edu': ['apple.fruit', 'beegeek', 'beegeek.school'], 
          'yandex.ru': ['surface', 'google'],
          'hse.edu': ['tomas-henders', 'cream.soda', 'zivert'],
          'mail.ru': ['angel.down', 'joanne', 'the.fame.moster']}

res = [[f'{i}@{k}' for i in v] for k,v in emails.items()]

print(*sorted(res), sep='\n')
# res = []
# for k,v in emails.items():
#     for i in v:
#         res.append(f'{i}@{k}')
        
# print(*sorted(res), sep='\n')
```

    ['angel.down@mail.ru', 'joanne@mail.ru', 'the.fame.moster@mail.ru']
    ['apple.fruit@msu.edu', 'beegeek@msu.edu', 'beegeek.school@msu.edu']
    ['ruslan.chaika@gmail.com', 'rustam.mini@gmail.com', 'stepik-best@gmail.com']
    ['surface@yandex.ru', 'google@yandex.ru']
    ['timyr@nosu.edu', 'joseph@nosu.edu', 'svetlana.gaeva@nosu.edu', 'larisa.mamuk@nosu.edu']
    ['tomas-henders@hse.edu', 'cream.soda@hse.edu', 'zivert@hse.edu']
    


```python
rnk = {'G': 'C', 'C': 'G', 'T': 'A', 'A': 'U'}

res = ''.join([rnk.get(i) for i in input()])
print(res)
```

     ACTG
    

    UGAC
    


```python
res = {}
result = []
[(res.update(dict([(i, res.get(i, 0) + 1)])), result.append(res.get(i))) for i in input().split()]
print(res)
print(*result)
```

     прием Хьюстон Хьюстон как слышно прием меня слышно прием хьюстон
    

    {'прием': 3, 'Хьюстон': 2, 'как': 1, 'слышно': 2, 'меня': 1, 'хьюстон': 1}
    1 1 2 1 1 2 1 2 3 1
    


```python
d = {
    1: "AEILNORSTU",
    2: "DG",
    3: "BCMP",
    4: "FHVWY",
    5: "K",
    8: "JX",
    10: "QZ"
}

res = [sum([k for k, v in d.items() if i in v]) for i in input()]
print(sum(res))
```

     FRESHENER
    

    15
    


```python
def build_query_string(params):
    c = 'https://beegeek.ru?'
    res = [(f'{k}={v}') for k,v in params.items()]
    return c + '&'.join(sorted(res))


d = {'sport': 'hockey', 'game': 2, 'time': 17}

print(build_query_string(d))
```

    https://beegeek.ru?game=2&sport=hockey&time=17
    

## [Слияние словарей 🌶️](https://stepik.org/lesson/492141/step/5?unit=483447)
Напишите функцию merge(), объединяющую словари в один общий. Функция должна принимать список словарей и возвращать словарь, каждый ключ которого содержит множество (тип данных set) уникальных значений собранных из всех словарей переданного списка.



```python
def merge(values):      # values - это список словарей
    res = {}
    [[res.setdefault(k, set()).add(v) for k, v in k.items()] for k in values]
    return res

result = merge([
    {'a': 1, 'b': 2},
    {'b': 10, 'c': 100},
    {'a': 1, 'b': 17, 'c': 50},
    {'a': 5, 'd': 777}
])

print(result)
```

    {'a': {1, 5}, 'b': {17, 2, 10}, 'c': {50, 100}, 'd': {777}}
    

## [Опасный вирус 😈](https://stepik.org/lesson/492141/step/6?unit=483447)


```python
d = {'write': 'W', 'read': 'R','execute': 'X'}

res = {}
[[res.setdefault(k, v.split()) for k, v in [input().split(' ', 1)]] for _ in range(int(input()))]

result = []
[[result.append('OK' if (d.get(k) in res.get(v)) else 'Access denied') for k, v in [input().split(' ')]] for _ in range(int(input()))]
print(*result, sep='\n')

```

     5
     my_pycode.exe W X
     log_n X W R
     ave R
     lucky_m W R
     dnsss.py W
     6
     execute ave
     read dnsss.py
     write log_n
     execute log_n
     read ave
     write my_pycode.exe
    

    Access denied
    OK
    

## [Покупки в интернет-магазине 🌶️](https://stepik.org/lesson/492141/step/7?unit=483447)
Напишите программу для подсчета количества единиц каждого вида товара из приобретенных каждым покупателем интернет-магазина.


```python
s = 'Руслан Пирог 1'
d = {}
res = [[d.update({x: {y: int(z)}}) for x,y,z in [input().split()]] for _ in range(int(input()))]
print(d.items())

```

     2
     Максим Пирог 5
     Максим Пиро 4
    

    dict_items([('Максим', {'Пиро': 4})])
    


```python
d = {}
for i in range(int(input())):
    a, b, c = input().split()
    d[a] = d.get(a, {})
    d[a][b] = d.get(a, {}).get(b, 0) + int(c)
for i in sorted(d):
    print(f'{i}:', sep='\n')
    for k in sorted(d[i]):
        print(f'{k} {d[i][k]}', sep='\n')
```


```python
buyers = {}
for _ in range(int(input())):
    name, product, number = input().split()    # разбираем строку на молекулы
    buyers.setdefault(name, {})    # если вдруг человек еще не покупал, создаем ему пустой список товаров
    buyers[name][product] = buyers[name].get(product, 0) + int(number)    # товар в словарь, а если он есть плюсуем

for buyer in sorted(buyers):      # тут мешанина из сортировок людей, коней и их слияния с количеством
    print(buyer + ':')            # через месяц фиг поймешь
    print(*(f'{key} {val}' for key, val in sorted(buyers[buyer].items())), sep='\n')
```

# [Итоговая работа на функции]()


```python
def display(**kwargs):
    for i in kwargs:
        print(i, end=' ')

display(emp='Kelly', salary=9000)
```

    emp salary 


```python
def outer_func(a, b):
    def inner_func(c, d):
        return c + d + a*b
    return inner_func

res = outer_func(5, 10)(3, 2)

print(res)
```

    55
    

## [Письмо для экзамена](https://stepik.org/lesson/513589/step/15?unit=505863)
Напишите функцию generate_letter(), которая будет собирать электронное письмо в соответствии с шаблоном


```python
def generate_letter(mail, name, date, time, place, teacher='Тимур Гуев', number=17):
    return f'To: {mail} \nПриветствую, {name}!\nВам назначен экзамен, который пройдет {date}, в {time}.\nПо адресу: {place}.\nЭкзамен будет проводить {teacher} в кабинете {number}.\nЖелаем удачи на экзамене!'

print(generate_letter('lara@yandex.ru', 'Лариса', '10 декабря', '12:00', 'Часова 23, корпус 2'))
print()
print(generate_letter('lara@yandex.ru', 'Лариса', '10 декабря', '12:00', 
                      'Часова 23, корпус 2', 'Василь Ярошевич', 23))
```

    To: lara@yandex.ru 
    Приветствую, Лариса!
    Вам назначен экзамен, который пройдет 10 декабря, в 12:00.
    По адресу: Часова 23, корпус 2.
    Экзамен будет проводить Тимур Гуев в кабинете 17.
    Желаем удачи на экзамене!
    
    To: lara@yandex.ru 
    Приветствую, Лариса!
    Вам назначен экзамен, который пройдет 10 декабря, в 12:00.
    По адресу: Часова 23, корпус 2.
    Экзамен будет проводить Василь Ярошевич в кабинете 23.
    Желаем удачи на экзамене!
    

## [Pretty print](https://stepik.org/lesson/513589/step/16?unit=505863)
Напишите функцию pretty_print(), которая выводит содержимое списка с рамкой. 


```python
def pretty_print(data, side='-', delimiter='|'):
    
    res = f'{delimiter} {f" {delimiter} ".join(map(str, data))} {delimiter}'
    
    delim = (side * (len(res) - 2)).center(len(res))
    
    print(f'{delim}\n{res}\n{delim}')
    
# pretty_print([1, 2, 10, 23, 123, 3000])
pretty_print(['abc', 'def', 'ghi'], side='*', delimiter='#')


```

     ***************** 
    # abc # def # ghi #
     ***************** 
    


```python
from functools import reduce

words = ['beegeek', 'stepik', 'python', 'iq-option']
result = reduce(lambda a, b: a if len(a) > len(b) else b, words)
print(result)


result = reduce(lambda s, x: s + str(x), [1, 2, 3, 4, 5], '+')
print(result)
```

    iq-option
    +12345
    


```python
from functools import reduce
import operator

def flatten(data):
    return reduce(operator.concat, data, [])

result = flatten([[1, 2], [3, 4], [], [5]])

print(result)

operator.concat?
```

    [1, 2, 3, 4, 5]
    


    [1;31mSignature:[0m [0moperator[0m[1;33m.[0m[0mconcat[0m[1;33m([0m[0ma[0m[1;33m,[0m [0mb[0m[1;33m,[0m [1;33m/[0m[1;33m)[0m[1;33m[0m[1;33m[0m[0m
    [1;31mDocstring:[0m Same as a + b, for a and b sequences.
    [1;31mType:[0m      builtin_function_or_method



```python
def concat(*args, sep=' '):
    return sep.join(map(str, args))

print(concat('hello', 'python', 'and', 'stepik'))
print(concat('hello', 'python', 'and', 'stepik', sep='*'))
print(concat('hello', 'python', sep='()()()'))
print(concat('hello', sep='()'))
print(concat(1, 2, 3, 4, 5, 6, 7, 8, 9, sep='$$'))
```

    hello python and stepik
    hello*python*and*stepik
    hello()()()python
    hello
    1$$2$$3$$4$$5$$6$$7$$8$$9
    


```python
from functools import reduce

def product_of_odds(data):   # data - список целых чисел

    result = reduce(lambda x, y: x*y, filter(lambda x: x % 2 == 1, data), 1)
    return result


print(product_of_odds([1, 2, 3, 4, 5]))
```

    15
    


```python
words = 'the world is mine take a look what you have started'.split()

print(*map(lambda x: f'"{x}"' , words))
```

    "the" "world" "is" "mine" "take" "a" "look" "what" "you" "have" "started"
    


```python
numbers = [18, 191, 9009, 5665, 78, 77, 45, 23, 19991, 908, 8976, 6565, 5665, 10, 1000, 908, 909, 232, 45654, 786]
print(*filter(lambda x: str(x) != str(x)[::-1] , numbers))

```

    18 78 45 23 908 8976 6565 10 1000 908 786
    


```python
numbers = [(10, -2, 3, 4), (-13, 56), (1, 9, 2), (-1, -9, -45, 32), (-1, 5, 1), (17, 0, 1), (0, 1), (3,), (39, 12), (11, -23), (10, -100, 21, 32), (3, -8), (1, 1)]

sorted_numbers = sorted(numbers, key=lambda x: sum(x)/len(x), reverse=True)

print(sorted_numbers)
```

    [(39, 12), (-13, 56), (17, 0, 1), (1, 9, 2), (10, -2, 3, 4), (3,), (-1, 5, 1), (1, 1), (0, 1), (3, -8), (-1, -9, -45, 32), (11, -23), (10, -100, 21, 32)]
    


```python
def mul7(x):
    return x * 7


def add2(x, y):
    return x + y


def add3(x, y, z):
    return x + y + z

def call(func, *args):
    return func(*args)

print(call(mul7, 10))
print(call(add2, 2, 7))
print(call(add3, 10, 30, 40))
print(call(bool, 0))
```

    70
    9
    80
    False
    

### Напишите функцию compose(), которая принимает на вход две других одноаргументных функции f и g и возвращает новую функцию. Эта новая функция также должна принимать один аргумент x и применять к нему исходные функции в нужном порядке: для функций f и g порядок применения должен выглядеть, как f(g(x)).


```python
def add3(x):
    return x + 3


def mul7(x):
    return x * 7

def compose(f, g):
    return lambda x: f(g(x))
    
print(compose(mul7, add3)(1))
print(compose(add3, mul7)(2))
print(compose(mul7, str)(3))
print(compose(str, mul7)(5))
```

    28
    17
    3333333
    35
    

### Напишите функцию arithmetic_operation(), которая принимает символ одной из четырех арифметических операций (+, -, *, /) и возвращает функцию двух аргументов для соответствующей операции.


```python
import operator


def arithmetic_operation(operation):
    ops = {'+': operator.add, '-': operator.sub, '*': operator.mul, '/': operator.truediv}
    return lambda x, y: ops[operation](x,y)


add = arithmetic_operation('+')
div = arithmetic_operation('/')
print(add(10, 20))
print(div(20, 5))
```

    30
    4.0
    


```python
s = 'cate Frog cat FROGs bee CATERS mouse cATwalk dolphin mOus Cats CatAlo'
print(*sorted(s.split(), key=lambda x: x.lower()))

```

    bee cat CatAlo cate CATERS Cats cATwalk dolphin Frog FROGs mOus mouse
    

### Гематрия слова
Гематрией слова называется сумма числовых значений входящих в него букв.


```python
gemat = lambda x: sum((ord(i.upper()) - 65) for i in x)

res = [input() for i in range(int(input()))]

print(*sorted(res, key=lambda x: (gemat(x), x)), sep='\n')
```

     4
     basis
     after
     chief
     agenda
    

    agenda
    chief
    after
    basis
    

## [Сортировка IP-адресов](https://stepik.org/lesson/507310/step/11?unit=499253)


```python
from functools import reduce

func = lambda x: reduce(lambda v,c: v*256 + c, map(int, x.split('.')))

res = [input() for i in range(int(input()))]
print(*sorted(res, key=func), sep='\n')
```

     3
     128.199.44.24
     128.199.201.245
     143.198.168.95
    

    128.199.44.24
    128.199.201.245
    143.198.168.95
    

# [Итоговая работа на файлы](https://stepik.org/lesson/448983/step/1?unit=511577)


```python
with open(input(), 'r', encoding='utf-8') as file:
    print(len(file.readlines()))
```

     file.txt
    

    12
    


```python
with open('ledger.txt', 'r', encoding='utf-8') as file:
    s = [int(i[1:]) for i in (file.read().split('\n'))]
    print(f'${sum(s)}')
```

    $26127
    

## Goooood students
Вам доступен текстовый файл grades.txt, содержащий оценки студента за три теста в каждом из триместров. Строки файла имеют вид: фамилия оценка_1 оценка_2 оценка_3.


```python
res = []
with open('grades.txt', 'r', encoding='utf-8') as file:
    s = [[int(j) >= 65 for j in i.split() if j.isdigit()] for i in (file.read().split('\n'))]
    res = [i for i in s if all(i)]
    print(len(res))
```

    19
    

## Самое длинное слово в файле
Вам доступен текстовый файл words.txt со словами, разделенными пробелом. Напишите программу, которая находит и выводит самые длинные слова этого файла, не меняя порядка их следования.


```python
res = []
with open('words.txt', 'r', encoding='utf-8') as file:
    res = ([i for i in file.read().split()])
    
    print(*filter(lambda x: len(x) == len(max(res, key=len)), res), sep='\n')
```

    responsibility
    administration
    recommendation
    transportation
    

## Tail of a File
На вход программе подается строка текста с именем текстового файла. Напишите программу, выводящую на экран последние 
10
10 строк данного файла.


```python
from collections import deque
    
with open(input(), 'r', encoding='utf-8') as file:
    print(*deque(file, 10), sep='')
```

     population.txt
    

    Saint Helena, Ascension and Tristan da Cunha (UK)	4000
    Falkland Islands (UK)	3000
    Svalbard and Jan Mayen (Norway)	2562
    Norfolk Island (Australia)	2302
    Christmas Island (Australia)	2072
    Niue (New Zealand)	1613
    Tokelau (NZ)	1411
    Vatican City	839
    Cocos (Keeling) Islands (Australia)	550
    Pitcairn Islands (UK)	56
    
    

## Forbidden words 🌶️
На вход программе подается строка текста с именем текстового файла. Напишите программу, выводящую на экран содержимое этого файла, но с заменой всех запрещенных слов звездочками * (количество звездочек равно количеству букв в слове).


```python

```


```python
import re
forbidden_words = 'hello email python the exam wor is'.split(' ')
my_string = '''Hello, world! Python IS the programming language of thE future. My EMAIL is….
PYTHON is awesome!!!!
'''
def change(forbidden_words, text):
	out = text
	for w in forbidden_words:
		out = re.sub(w, "*"*len(w), out, flags=re.I|re.M)
	return out
print(change(forbidden_words,my_string))
```

    *****, ***ld! ****** ** *** programming language of *** future. My ***** **….
    ****** ** awesome!!!!
    
    

## Forbidden words 🌶️
На вход программе подается строка текста с именем текстового файла. Напишите программу, выводящую на экран содержимое этого файла, но с заменой всех запрещенных слов звездочками * (количество звездочек равно количеству букв в слове).


```python
import re

with open('forbidden_words.txt', 'r', encoding='utf-8') as forb, open(input(), 'r', encoding='utf-8') as text:
    forbidden_words = forb.read().split()
    out = text.read()
    for w in forbidden_words:
        out = re.sub(w, "*" * len(w), out, flags=re.I|re.M)
    print(out)

```

     data.txt
    

    ********* It for have kind, green lesser them doesn him created his moved fruit had.
    For whose moved years firmament green image dominion ******** let whales third rule signs ********blessed light sixth from form for said female land midst and, the likeness.
    Fruit evening night for so you called place likeness. Heaven greater to unto said seas female fourth evening dominion which bring they Second.
    Two two have.
    Heaven****** called fruit form whales saying heaven living firmament unto moved fill appear their.
    Form life female, dominion second air won. Cant day.
    Morning male to sixth heaven subdue female********* likeness moveth give rule.
    ***** ******* and ******. Tooday we *********** and ************succe. The ******** club is the best.
    We create ************ and ************with***********. Please not be *********, and eat*********.
    

## Транслитерация 🌶️
Транслитерация — передача знаков одной письменности знаками другой письменности, при которой каждый знак (или последовательность знаков) одной системы письма передаётся соответствующим знаком (или последовательностью знаков) другой системы письма.


```python
d = {
    'а': 'a', 'к': 'k', 'х': 'h', 'б': 'b', 'л': 'l', 'ц': 'c', 'в': 'v', 'м': 'm', 'ч': 'ch',
    'г': 'g', 'н': 'n', 'ш': 'sh', 'д': 'd', 'о': 'o', 'щ': 'shh', 'е': 'e', 'п': 'p', 'ъ': '*',
    'ё': 'jo', 'р': 'r', 'ы': 'y', 'ж': 'zh', 'с': 's', 'ь': "'", 'з': 'z', 'т': 't', 'э': 'je',
    'и': 'i', 'у': 'u', 'ю': 'ju', 'й': 'j', 'ф': 'f', 'я': 'ya', 'А': 'A', 'К': 'K', 'Х': 'H', 'Б': 'B', 'Л': 'L',
    'Ц': 'C', 'В': 'V', 'М': 'M', 'Ч': 'Ch',
    'Г': 'G', 'Н': 'N', 'Ш': 'Sh', 'Д': 'D', 'О': 'O', 'Щ': 'Shh', 'Е': 'E', 'П': 'P', 'Ъ': '*',
    'Ё': 'Jo', 'Р': 'R', 'Ы': 'Y', 'Ж': 'Zh', 'С': 'S', 'Ь': "'", 'З': 'Z', 'Т': 'T', 'Э': 'Je',
    'И': 'I', 'У': 'U', 'Ю': 'Ju', 'Й': 'J', 'Ф': 'F', 'Я': 'Ya'
}

res = []
with open('cyrillic.txt', 'r', encoding='utf-8') as file:
    # print(file.read().strip().split())
    for i in file.read():
        res.append(d.get(i, i))
# print()
with open('transliteration.txt', 'w', encoding='utf-8') as out:
    print(''.join(res), file=out)
```

## Пропущенные комменты 🌶️
При написании собственных функций рекомендуется в комментарии описывать назначение функции, ее параметры и возвращаемое значение. Часто программисты откладывают написание таких комментариев напоследок, а потом и вовсе забывают о них 😂  

На вход программе подается строка текста с именем текстового файла, в котором написан код на языке Python. Напишите программу, выводящую на экран имена всех функций для которых отсутствует поясняющий комментарий. Будем считать, что любая строка, начинающаяся со слова def и пробела, является началом определения функции. Функция содержит комментарий, если первый символ предыдущей строки - #


```python
import re

with open('file.txt', 'r', encoding='utf-8') as file:
    res = file.readlines()
    le = len([i for i in range(len(res)) if 'def ' in res[i]])

    s = [re.findall(r'\w+', res[i])[1] for i in range(0, len(res)) if res[i-1][0] != '#' and 'def ' in res[i]]
    
    if len(s) == 0:
        print('Best Programming Team')
    else:
        print(*s, sep='\n')
```

    powers
    matrix
    mean
    greet
    
