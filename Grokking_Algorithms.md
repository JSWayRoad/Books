# Grokking_Algorithms
Grokking Algorithms by Aditya Bhargava 

### Содержание

[Бинарный поиск](#binarySearch)  
[Сортировка выбором](#selectionSort)  
[Рекурсия](#recursion)  
[Быстрая сортировка](#quickSort)  
[Алгоритм Дейкстры](#dijkstraAlgorithm)  
[Жадные Алгоритмы](#greedyAlgorithms)  
[Динамическое программирование](#dynamicProgramming)  
[Алгоритм k ближайших соседей](#algoritm)




### 1. ЗНАКОМСТВО С АЛГОРИТМАМИ

**Алгоритм** - набор инструкций для выполнения некоторой задачи.

## <a name="binarySearch"></a>Бинарный поиск

Это алгоритм; на входе он получает отсортированный список элементов.Если элемент, который вы ищете,
присутствует в списке, то бинарный поиск возвращает ту позицию, в которой он был найден. В про-
тивном случае БП возвращает  null.

С БП мы каждый раз загадываем число в середине диапазона исключаем половину оставшихся чисел (50 и 75(63))  
100-50-25-13-7-4-2-1

**Логарифмы** - операция, обратная возведению в ступень.  
**Массив** - это непрерывная последовательность ячеек
(нумерация начинается с 0)

### Время выполнения

**Линейное время** - это, когда кол-во попыток совпадает с размером списка.
O(n)  
БП вып-ся за **логарифмическое время**.
0(log n)  
Спец-ая нотация **'О-большое'** описывает(выражает) скорость(время) работы алгоритмы.(в худшем случае)

### Шпаргалка

- Скорость алгоритмов измеряется не в секундах, а в темпе роста кол-ва операций
- По сути формула описывает, насколько быстро возрастает время вып. алгоритма(А) с увеличением размера
входных данных.
- Время вып А выр как 'О-большое'
- Время вып 0(log n) быстрее O(n), а с увеличением размера списка в котором ищется значение,оно становится намного быстрее.


## <a name="selectionSort"></a>Сортировка выбором

Индекс - позиция элемента.

**Массивы** чтение O(1) вставка O(n) удаление O(n)  
**Списки** чтение O(n) вставка O(1) удаление O(1)

Вставка и удаление вып за время O(1) только в том случае, если можно мгновенно получить  доступ  искомому элементу
Виды доступа:последовательный и произвольный(чтение массива).


Его суть — за каждый проход по массиву выбрать минимальный элемент (для сортировки по возрастанию) и поменять его местами с 
первым элементом в еще не отсортированном участке массива, тем самым уменьшив длину этого участка на один, и так до тех
 пор пока не будут отсортированы все элементы.
 
 ```
const selectionSort = arr => {
    for (let i = 0, l = arr.length, k = l - 1; i < k; i++) {
        let indexMin = i;
        for (let j = i + 1; j < l; j++) {
            if (arr[indexMin] > arr[j]) {
                indexMin = j;
            }
        }
        if (indexMin !== i) {
            [arr[i], arr[indexMin]] = [arr[indexMin], arr[i]];
        }
    }
    return arr;
};

```
## <a name="recursion"></a>Рекурсия

**Рекурсия** - элегантный метод решения задач.  
Коробки  
1.Сложить все коробки к кучу  
2. Пока в куче остаются коробки  
3. взять коробку и открыть  
4. если внутри лежит коробка,добавить её в кучу  
4.если внутриключ, поиск закончен!  
5. Вернуться к куче((2.)

Альтернативное решение
1. проверить каждый предмет в коробке  
2.если мы найдём коробку…(1.)   
2.если найдём ключ, поиск законче

### СТЕК

 ```
const namePerson = "RA";
const greet = (namePerson) => {
  console.log(`"Hello," + ${namePerson} + "!"`);
  greet2(namePerson);
  bye(namePerson);
};
const greet2 = (namePerson) => {
  console.log(`"Привет" + ${namePerson} + "!"`);
};
const bye = (namePerson) => {
  console.log(`"Bye" + ${namePerson} + "!"`);
};
greet(namePerson);


```


Пример работы стека вызова:  

- В коде происходит вызов greet(“RA”)  
- Компьютер выделяет блок памяти для вызова функции  
- затем эта память исп.. Пер. name присваивается значение  
“RA”; оно должно быть сохранено в памяти.

greet  
name:RA

- каждый раз, когда мы вызываем Ф, комп. save в памяти value все  
пер-ых для этого вызова. Далее выводится приветствие hello,RA!,  
после чего следует второй вызов greet2(namePerson). И снова  
компьютер выделяет блок памяти для вызова функции.

Текущий вызов функции:  
greet2  
name:RA  
greet  
name:RA

Комп. объединяет эти блоки в стек.2-ой блок создаётся над первым.  
Мы выводим сообщение Привет,RA!,  после чего возвращаем управление  
из вызова функции.Когда это происходит, блок на вершине стека извлекается из него.

уходит greet2  
name:RA  
greet  
name:RA

- Теперь верхний блок в стеке отн. к функции greet; это означает, что  
мы вернулись к Ф greet.При вызове  Ф greet2  Ф greet еще не была завершена.  
Здесь-то и скрывается истинный смысл этого раздела: когда мы вызываем Ф из др.Ф,  
вызывающая Ф приостанавливается в частично завершенном состоянии.  
Все значения переменных этой Ф остаются в памяти. А когда вып. Ф greet2 будет завершено, мы вернёмся  
к Ф greet  и продолжим её вып. с того места, где оно прервалось. Сначала выводится сообщение Привет,RA!, после чего вызывается Ф bye.

Bye  
greet  
name:RA

- Блок для этой Ф добавляется на вершину стека. Далее выводится сообщение  
- Bye,RA! с выходом из Ф

уходит  Bye  
greet  
name:RA

Управление снова возвращает Ф greet. Делать больше нечего, так что управление возвращает Ф greet. Этот стек, в котором сохранялись переменные разных Ф,  
называется стеком вызовов.

## Шпаргалка
- Когда Ф вызывает саму себя, это называется рекурсией 
- В каждой рекурсивной Ф должно быть два случая: базовый и рекурсивный.
- Стек поддерживает две операции: внесение и извлечение элементов.
- Все вызовы 	Ф сохраняются в стеке вызовов
- Если стек вызовов станет очень большим, он займёт слишком много памяти.

## <a name="quickSort"></a>Быстрая сортировка

**РАЗДЕЛЯЙ И ВЛАСТВУЙ**

- Определяем базовый случай. Это должен быть простейший случай из всех возможных.  
- Задача делится или сокращается до тех пор, пока не будет сведена к базовому случаю.

Мы хотим разделить землю( 1680м  на 640м) на одинакомые квадратные участки.  
Участки должны быть настолько большими, насколько это возможно.

Базовый случай будет, если одна сторона кратна другой.  
640 * 640  и ещё останется нераспределённый участок 240  
640 * 400 если мы найдём самый большой участок, подходящий для этого размера, это будет самый  
большой участок, подходящий для всей фермы(**Алгоритм Евклида**)  
400 * 400 и остаётся 240  
240 * 240 и остаётся 160  
160 * 160 и остаётся 80  
80 * 80 Базовый случай

 ```
const sum = (array) =>
  array.length === 0 ? 0 : array[0] + sum(array.slice(1));
console.log(sum([1, 2, 3]));

```

Рассуждение:
sum([1,2,3])  
-> 1 + sum([2,3])  
-> 1 + 2 + sum([3])  
-> 1 + 2 + 3 + sum([])  
-> 1 + 2 + 3 + 0  
-> 6

[рекурсия](http://code.mu/ru/javascript/book/prime/functions/recursion/intro/)

 ```
Сумма элементов массива
Давайте теперь не будем выводить элементы массива на экран, а найдем сумму элементов этого массива.

Приведу сразу код, выполняющий описанное (далее будет подробный разбор):

function getSum(arr) {
	let sum = arr.shift();
	
	if (arr.length != 0) {
		sum += getSum(arr);
	}
	
	return sum;
}

console.log(getSum([1, 2, 3]));
Давайте пошагово разберемся с тем, что происходит в этом коде.

Итак, вот расписан первый вызов функции:

function getSum(arr) {
	// здесь массив arr = [1, 2, 3]
	
	let sum = arr.shift(); // в sum запишется первый элемент массива, то есть 1
	
	// здесь массив arr = [2, 3]
	
	// длина массива больше нуля, значит попадем в иф
	if (arr.length != 0) {
		// здесь в sum лежит число 1
		
		sum += getSum(arr); // параметром рекурсии передается массив [2, 3]
		// далее код не выполняется, так как
		// мы опять попадаем в функцию getSum на следующий шаг рекурсии
		// смотрите пример кода ниже
	}
	
	// сюда мы пока не попадаем, так как ушли в рекурсию
	return sum;
}

console.log(getSum([1, 2, 3]));
Вот мы первый раз попадаем в рекурсию, то есть функция getSum первый раз вызывается внутри себя:

function getSum(arr) {
	// здесь массив arr = [2, 3]
	
	let sum = arr.shift(); // в sum запишется первый элемент массива, то есть 2
	
	// здесь массив arr = [3]
	
	// длина массива больше нуля, значит попадем в иф
	if (arr.length != 0) {
		// здесь в sum лежит число 2
		
		sum += getSum(arr); // параметром рекурсии передается массив [3]
		// далее код не выполняется, так как
		// мы опять попадаем в функцию getSum на следующий шаг рекурсии
		// смотрите пример кода ниже
	}
	
	// сюда мы пока не попадаем, так как ушли в рекурсию
	return sum;
}

console.log(getSum([1, 2, 3]));
Вот мы второй раз попадаем в рекурсию, то есть функция getSum второй раз вызывается внутри себя:

function getSum(arr) {
	// здесь массив arr = [3]
	
	let sum = arr.shift(); // в sum запишется первый элемент массива, то есть 3
	
	// здесь массив arr = []
	
	// длина массива равна нулю, значит не попадем в иф
	if (arr.length != 0) {
		// сюда мы уже не попадаем
		sum += getSum(arr);
	}
	
	// возвращаем в родительский вызов содержимое sum, то есть число 3:
	return sum;
}

console.log(getSum([1, 2, 3]));
Как вы видите, это последний вызов функции внутри себя, так как в этом вызове массив закончился.

Именно сейчас срабатывает первый return и выполнение кода перескакивает обратно на первый шаг рекурсии и продолжается с 13 строки:

function getSum(arr) {
	// здесь массив arr = [2, 3]
	
	let sum = arr.shift(); // в sum запишется первый элемент массива, то есть 2
	
	// здесь массив arr = [3]
	
	// длина массива больше нуля, значит попадем в иф
	if (arr.length != 0) {
		// здесь в sum лежит число 2
		
		// ВЫПОЛНЕНИЕ ПРОДОЛЖАЕТСЯ ОТСЮДА
		sum += getSum(arr); // функция вернула 3, в sum лежит 2, итого в sum запишется 5
	}
	
	// возвращаем в родительский вызов содержимое sum, то есть число 5:
	return sum;
}

console.log(getSum([1, 2, 3]));
Теперь выполнение кода перескакивает обратно на первый шаг рекурсии и продолжается с 13 строки:

function getSum(arr) {
	// здесь массив arr = [1, 2, 3]
	
	let sum = arr.shift(); // в sum запишется первый элемент массива, то есть 1
	
	// здесь массив arr = [2, 3]
	
	// длина массива больше нуля, значит попадем в иф
	if (arr.length != 0) {
		// здесь в sum лежит число 1
		
		// ВЫПОЛНЕНИЕ ПРОДОЛЖАЕТСЯ ОТСЮДА
		sum += getSum(arr); // функция вернула 5, в sum лежит 1, итого в sum запишется 6
	}
	
	// возвращаем во внешний мир содержимое sum, то есть число 6:
	return sum;
}

// вот здесь выведется результат последнего return:
console.log(getSum([1, 2, 3])); // выведет 6

``` 
СТЕК(В Сокращении,без того, что приостановилось)

ARR                      
1,2,3    
  2,3                    
    3                     
  2,3                    
1,2,3  

В соответсвие sum будет

SUM  
1  
2  
3  
2  
1

Мы осуществляем вызовы 

### Быстрая сортировка

Она относится к алгоритмам сортировки. Она работает намного быстрее сортировки выбором и часто применяется в реальных программах.
Она основана на методе 'Разделяй и властвуй'.

def quicksort(array):
 if len(array) < 2
   return array

33 15 10

Алгоритм быстрой сортировки работает так: сначала в массиве выбирается элемент, который наз. **опорный** (33)
Теперь мы находим эл., меньше опорного, и эл., больше опорного.  
числа меньше 15,10  
числа больше []

Этот процесс наз. **разделением**. Мы имеем:  
- подмассив всех эл., меньше опорного;
- опорный эл.;
- подмассив всех эл., больше опорного.

Два подмассива не отсортированы - они просто выделены из исходного массива. Но если бы они были отсортированы, то провести  
сортировку всего массива было бы несложно.

Если бы подмассивы  были отсортированы их можно было соединить  
левый подмассив + опорный элемент + правый подмассив  
quicksort([15,10]) + [33] + quicksort([])

[Быстрая сортировка 1](https://medium.com/devschacht/nicholas-c-zakas-computer-science-in-javascript-quicksort-afa07c0a47f0)
[Быстрая сортировка 2](https://dev-gang.ru/article/bystraja-sortirovka-v-javascript-964jzhnwc1/)

###Алгоритм
Быстрая сортировка, сортировка Хоара (англ. quicksort), часто называемая qsort (по имени в стандартной библиотеке языка Си) — широко известный алгоритм сортировки, разработанный английским информатиком Чарльзом Хоаром во время его работы в МГУ в 1960 году.

Общая идея алгоритма состоит в следующем:

Выбрать из списка элемент, называемый опорным. Это может быть любой из элементов списка или же число, вычисленное на основе значений элементов.  
Сравнить все остальные элементы с опорным и переставить их в списке так, чтобы разбить список на три непрерывных отрезка, следующих друг за другом: «меньшие опорного», «равные» и «большие».  
Для отрезков «меньших» и «больших» значений выполнить рекурсивно ту же последовательность операций, если длина отрезка больше единицы.  
На практике список обычно делят не на три, а на две части: например, «меньшие опорного» и «равные и большие»; такой подход в общем случае эффективнее, так как упрощает алгоритм разделения.

###Доказательство по Индукции

Мы только что познакомились с методом доказательства по индукции! Это один из способов, доказывающих, что наш алгоритм работает.  
Каждое индуктивное доказательство состоит из двух частей: базы и индукционного перехода.Звучит знакомо? Допустим, я хочу доказать,  
что могу подняться на самый верх стремянки. Если мои ноги стоят на ступеньке, то я могу переставить их на следующую ступеньку, -  
это индукционный переход. Если я стою на ступеньке 2, то могу подняться на ступеньку 3. Что касается базового случая, я сейчас  
стою на ступеньке 1. Из этого следует, что я могу подняться на самых верх стремянки, каждый раз поднимаясь на одну ступеньку.

Алгоритм быстрой сортировки уникален тем, что его скорость зависит от выбора опорного элемента

стр 93 - 98 не рассмотренны

### Шпаргалка

- Стратегия 'Разделяй и властвуй' основана на разбиении задачи на уменьщающиеся  
фрагменты. Если вы исп. это стратегию со списком, то базовым случаем скорее всего будет  
пустой массив или массив из одного эл..  
- Если вы реализуете алгоритм быстрой сортировки, выберите в качестве опорного случ. эл..  
Среднее время вып. быстрой сортировки составляет О(n log n)!  
- Константы в 'О-большом' иногда могут иметь значение. Именно по этой причине быстрая сортировка  
быстрее сортировки слиянем.  
- При сравнении простой сортировки с бинарной константа почти никогда роли не играет, потому что  
О(log n) слишком сильно превосходит О(n) по скорости при большом размере списка.

### Хеш-таблица

**Хеш-функция** - функция, которая получает строку и возвращает число.  
Требования:  
Она должна быть последовательной. Допустим, вы передали ей строку "апальсины" и  
Получили 4. Это значит, что каждый раз в будущем, передавая ей строку "апельсины",  
вы будете получать 4. Без этого хеш-таблица бесполезна.  
- Разным словам должны соответствовать разные числа.  

- Хеш-функция неизменно связывает название с одним индексом. При 1-ом вызове Ф вы  
узнаете, где хранить цену, а при последующих вызовах она сообщает, где взять эту цену.  
- Хеш-функция связывает разные строки с разными индексами.  
- Хеш функция знает размер массива и return только действительные индексы.  

**Хеш-таблица**(структура данных) - Хеш-функция + массив

Массивы и списки напрямую отображаются на адреса памяти, а хеш-таблица определяет место  
хранения элементов при помощи функции.  

Ассоциативные массивы,хеши,хеш-карты

**Преобразование DNS** - связывания имени с IP-адресом.
**хеш** - это данные, которые запомнились.  

### Шпаргалка  

Хеши хорошо подходят для:  
- моделирования отн. между объектами;
- устранение дубликатов;  
- кэширование/запоминание данных вместо выполнения  работы на сервере.  

### Коллизии  

**Коллизия** - это, когда двум ключами назначается 1 эл. массива.(создаём  
Связанный список.  

- В идеале хеш-функция должна распределять ключи равномерно по всему хешу;  
- Если связанные списки слишком длинными, работа Ф сильно замедляется.

Хеш-таблица  
Средний случай:поиск, вставка и удаление O(1)  
Худший случай: O(n). 

Время О(n) наз. **постоянным**(время ост. пост. Независимо от размера хеш-таблица.  
Получение эл. массива работает по этому времени.  
Но в худшем случае всё обстоит хуже(избегайте коллизей)  
Для избежания:  
-низкий коэффициент заполнения;  
- хорошая хеш-функция.  

Стр 121 - 125 не рассмотрены.

### Шпаргалка  

- Хеш-таблица создается объединением хеш-функции с массивом.  
- Хеш-функция должна сводить число **коллизей** к минимуму.  
- Хеш-таблицы обеспечивают очень быстрое выполнение поиска, вставки и удаления.  
- Хеш-таблица хорошо подходит для моделирования отношений между объектами.  
- Если коэффициент заполнения больше 0,7 пора изм. размер Хеш-таблицы.  
- Хеш-таблица исп. для кэширования данных.  
- Хеш-таблица хорошо подходит для обнаружения дубликатов.



### Поиск в ширину

**Поиск в ширину** - это алгоритм для решения задачи поиска кратчайшего пути.  
**Граф** - моделирует набор связей. Он состоит из узлов и рёбер.  
Узел м.б. соединён напрямую с несколькими др. узлами. Эти узлы наз. **соседями**.  
Графы исп. для моделирования связей между разными объектами.  

Поиск в ширину - это алгоритм поиска и он работает с графами. 

Алгоритм поиска в ширину отвечает на следующие вопросы:  
- существует ли путь от узла А к узлу В?( есть ли продавец манго в вашей сети)  
- как выглядит кратчайший путь от узла А к узлу В. ( кто из продавцов манго находится ближе)  

Связи 1-ого уровня предпочтительнее связей 2-ого и т.д.(чтобы это реализовать исп. **очередь**)  
Очередь похожа на стек: мы не можем обращаться к произвольным эл. очереди. Вместо этого поддерживается  
всего 2 операции: постановка в очередь и извлечение из неё.  

Хеш-таблица способна выражать отношения.( ключ и значения)  
**Граф** - это всего лишь набор узлов и рёбер.  

Хеш-таблица не упорядочена, поэтому пары "ключ-значения" можно добавлять в любом порядке.  
 
**Ребро** - соед. линия или линия со стрелкой, ведущая от одного эл. к др..(Время вып(О(кол. рёбер))  

Любое дерево явл. графом, но не наоборот.  


### Шпаргалки  
- В направленном графе есть стрелки, а отн. действуют в направлении стрелки.  
- В ненаправленном графах стрелки нет, а отн. идёт в обе стороны.  
- FIFO (очередь) LIFO(стек) 
- Позаботьтесь о том, чтобы уже проверенный чел. не проверяется заново, иначе цикл будет бесконечный. 
- Эл. проверяем в порядке очереди.

## <a name="dijkstraAlgorithm"></a>Алгоритм Дейкстры

**Алгоритм Дейкстры** исп. для поиска пути от начальной точки к конечной за кратчайшее возможное время.
(у каждого ребра графа имеется вес)  
(не рабоатет с графами, содержащими ребра с отр. весом(Беллман-Форд))

Алгоритм Дейкстры состоит из 4 шагов:
- Найти узел с наименьшей стоимостью.
- Обновить стоимости соседей этого узла.
- Повторять, пока это не будет сделано для всех узлов графа.
- Вычислить итоговый путь.

Граф с весами наз. **взвешенным графом**(Алгоритм Дейкстры)
Граф без весов наз. **невзвешенный графом**(поиск в ширину)

Ненаправленный граф(цикл)

Ключевая идея Алгоритма Дейкстры;: в графе ищется пусть с наименьшей стоимостью. Пути к этому узлу с меньшими затратами  
не существует.

## <a name="greedyAlgorithms"></a>Жадные Алгоритмы

Множества не содержат дубликатов.

С двумя множествами можно вып. ряд интересных операций:
- объединение множеств означает слияние элементов обоих множеств
- под операцией пересечения понимается поиск элементов, входящих в оба можества
- под разностью множест понимается исключение из одного множества элементов, присутствующих в другом множестве.

### NP-полные задачи
(это задачи о Коммивояжере и покрытие множеств)

Для решения задачи о покрытии множества необходимо вычислить каждое возможное подмножество.

### Шпаргалка

- Жадные алгоритмы стремятся к локальной оптимизации в расчете на то, что в итое будет достигнут глобальный оптимум.
- У NP-полных не существует известных быстрых решений.
- Если у вас имеется NP-полная задача, лучше всего воспользоватиься птиближенным алгоритмом.
- Жадные алгоритмы легко реализуются и быстро выпоняются, so из них получаются хорошие приближенные алгоритмы.

## <a name="dynamicProgramming"></a>Динамическое программирование

Каждый алгоритм динамического программирования начинается с таблицы и решения малых задач.

Пример: задача о вместимости рюкзака.

**Динамическое программирование** работает только в том случае, если каждая подзадача автономна, то есть не зависит от др.  
подзадач.(максимизируем некоторую характеристику)  
Значения в ячейках таблицы обычно представляет ту характеристику, которую мы хотим оптимизировать.

**Динамическое программирование** прим. для оптимизации какой-либо характеристики при заданных ограничениях. В задаче о рюкзаке  
требуется максимизировать стоимость отобранных предметов с ограничениями по емкости рюкзака.  
**Динамическое программирование** работает только в ситуациях, в которых задача может быть разбита на автономные подзадачи, не  
зависящие друг от друга.

**Рекомендации**:  
- строить таблицу;
- значения ячеек таблицы обычно соотвествует оптимизируемой характеристике. Для задачи о рюкзаке значения представляли общую стоимость товара;  
- каждая ячейка представляет подзадачу.

### Шпаргалка  
- **Динамическое программирование** применяется при оптимизации некоторой характеристики
- **Динамическое программирование** рабоатет только в ситуациях, в которых задача может быть разбита на автономные подзадачи  
- В каждом решениии из области **Динамическое программирование** строится таблица  
- значения ячеек обычно соответствует оптимизируемой характеристике  
- каждая ячейка представляет подзадачу  
- не существует единой формулы для вычисления решений методом **Динамическое программирование** 

## <a name="algoritm"></a>Алгоритм k ближайших соседей

У нас есть элемент и мы проверяем 3 ближайших соседа(формула Пифагора)

У этого алгоритма есть два основных применения: классификация и регрессия:  
- классификация(распределение по категориям);
- регресия(прогнозирование ответа)(в числовом выражении)

**Извлечение признаков** наз. преобразование эл. в список чисел, которые могут спользоваться для  сравнения  
Качественный выбор признаков - важная часть успешного алгоритма k ближайших соседей.
