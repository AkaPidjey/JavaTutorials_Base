[Java Tutorials](README.md)

# Класс Object
+ [Что такое класс `Object`? Какие в нем есть методы?](#Что-такое-класс-object-Какие-в-нем-есть-методы)
+ [Зачем нужен `equals()`. Чем он отличается от операции `==`?](#Зачем-нужен-equals-Чем-он-отличается-от-операции-)
+ [Если вы хотите переопределить `equals()`, какие условия должны выполняться?](#Если-вы-хотите-переопределить-equals-какие-условия-должны-выполняться)
+ [Какими свойствами обладает порождаемое `equals()` отношение эквивалентности?](#Какими-свойствами-обладает-порождаемое-equals-отношение-эквивалентности)
+ [Правила переопределения метода `Object.equals()`.](#Правила-переопределения-метода-objectequals)
+ [Какая связь между `hashCode()` и `equals()`?](#Какая-связь-между-hashcode-и-equals)
+ [Если `equals()` переопределен, есть ли какие-либо другие методы, которые следует переопределить?](#Если-equals-переопределен-есть-ли-какие-либо-другие-методы-которые-следует-переопределить)
+ [Что будет, если переопределить `equals()` не переопределяя `hashCode()`? Какие могут возникнуть проблемы?](#Что-будет-если-переопределить-equals-не-переопределяя-hashcode-Какие-могут-возникнуть-проблемы)
+ [Каким образом реализованы методы `hashCode()` и `equals()` в классе `Object`?](#Каким-образом-реализованы-методы-hashcode-и-equals-в-классе-object)
+ [Для чего нужен метод `hashCode()`?](#Для-чего-нужен-метод-hashcode)
+ [Каковы правила переопределения метода `Object.hashCode()`?](#Каковы-правила-переопределения-метода-objecthashcode)
+ [Есть ли какие-либо рекомендации о том, какие поля следует использовать при подсчете `hashCode()`?](#Есть-ли-какие-либо-рекомендации-о-том-какие-поля-следует-использовать-при-подсчете-hashcode)
+ [Могут ли у разных объектов быть одинаковые `hashCode()`?](#Могут-ли-у-разных-объектов-быть-одинаковые-hashcode)
+ [Если у класса `Point{int x, y;}` реализовать метод `equals(Object that) {(return this.x == that.x && this.y == that.y)}`, но сделать хэш код в виде `int hashCode() {return x;}`, то будут ли корректно такие точки помещаться и извлекаться из `HashSet`?](#Если-у-класса-pointint-x-y-реализовать-метод-equalsobject-that-return-thisx--thatx--thisy--thaty-но-сделать-хэш-код-в-виде-int-hashcode-return-x-то-будут-ли-корректно-такие-точки-помещаться-и-извлекаться-из-hashset)
+ [Могут ли у разных объектов `(ref0 != ref1)` быть `ref0.equals(ref1) == true`?](#Могут-ли-у-разных-объектов-ref0--ref1-быть-ref0equalsref1--true)
+ [Могут ли у разных ссылок на один объект `(ref0 == ref1)` быть `ref0.equals(ref1) == false`?](#Могут-ли-у-разных-ссылок-на-один-объект-ref0--ref1-быть-ref0equalsref1--false)
+ [Можно ли так реализовать метод `equals(Object that) {return this.hashCode() == that.hashCode()}`?](#Можно-ли-так-реализовать-метод-equalsobject-that-return-thishashcode--thathashcode)
+ [В `equals()` требуется проверять, что аргумент `equals(Object that)` такого же типа что и сам объект. В чем разница между `this.getClass() == that.getClass()` и `that instanceof MyClass`?](#В-equals-требуется-проверять-что-аргумент-equalsobject-that-такого-же-типа-что-и-сам-объект-В-чем-разница-между-thisgetclass--thatgetclass-и-that-instanceof-myclass)
+ [Можно ли реализовать метод `equals()` класса `MyClass` вот так: `class MyClass {public boolean equals(MyClass that) {return this == that;}}`?](#Можно-ли-реализовать-метод-equals-класса-myclass-вот-так-class-myclass-public-boolean-equalsmyclass-that-return-this--that)
+ [Есть класс `Point{int x, y;}`. Почему хэш код в виде `31 * x + y` предпочтительнее чем `x + y`?](#Есть-класс-pointint-x-y-Почему-хэш-код-в-виде-31--x--y-предпочтительнее-чем-x--y)
+ [Расскажите про клонирование объектов.](#Расскажите-про-клонирование-объектов)
+ [В чем отличие между _поверхностным_ и _глубоким_ клонированием?](#В-чем-отличие-между-поверхностным-и-глубоким-клонированием)
+ [Какой способ клонирования предпочтительней?](#Какой-способ-клонирования-предпочтительней)
+ [Почему метод `clone()` объявлен в классе `Object`, а не в интерфейсе `Cloneable`?](#Почему-метод-clone-объявлен-в-классе-object-а-не-в-интерфейсе-cloneable)
+ [ССЫЛКИ НА ДОПОЛНИТЕЛЬНУЮ ИНФУ](#ССЫЛКИ-НА-ДОПОЛНИТЕЛЬНУЮ-ИНФУ)



## Что такое класс `Object`? Какие в нем есть методы?
`Object` это базовый класс для всех остальных объектов в Java. Любой класс наследуется от `Object` и, соответственно, наследуют его методы:
+ `public boolean equals(Object obj)` – служит для сравнения объектов по значению;
+ `int hashCode()` – возвращает hash код для объекта;
+ `String toString()` – возвращает строковое представление объекта;
+ `Class getClass()` – возвращает класс объекта во время выполнения;
+ `protected Object clone()` – создает и возвращает копию объекта;
+ `void notify()` – возобновляет поток, ожидающий монитор;
+ `void notifyAll()` – возобновляет все потоки, ожидающие монитор;
+ `void wait()` – остановка вызвавшего метод потока до момента пока другой поток не вызовет метод `notify()` или `notifyAll()` для этого объекта;
+ `void wait(long timeout)` – остановка вызвавшего метод потока на определённое время или пока другой поток не вызовет метод `notify()` или `notifyAll()` для этого объекта;
+ `void wait(long timeout, int nanos)` – остановка вызвавшего метод потока на определённое время или пока другой поток не вызовет метод `notify()` или `notifyAll()` для этого объекта;
+ `protected void finalize()` – может вызываться сборщиком мусора в момент удаления объекта при сборке мусора.

[к оглавлению](#Класс-object)

## Зачем нужен `equals()`. Чем он отличается от операции `==`?
Метод `equals()` - определяет отношение эквивалентности объектов.

При сравнении объектов с помощью `==` сравнение происходит лишь между ссылками. При сравнении по переопределённому разработчиком `equals()` - по внутреннему состоянию объектов.

[к оглавлению](#Класс-object)

## Если вы хотите переопределить `equals()`, какие условия должны выполняться?
## Какими свойствами обладает порождаемое `equals()` отношение эквивалентности?
+ _Рефлексивность_: для любой ссылки на значение `x`, `x.equals(x)` вернет `true`;
+ _Симметричность_: для любых ссылок на значения `x` и `y`, `x.equals(y)` должно вернуть `true`, тогда и только тогда, когда `y.equals(x)` возвращает `true`.
+ _Транзитивность_: для любых ссылок на значения `x`, `y` и `z`, если `x.equals(y)` и `y.equals(z)` возвращают `true`, тогда и `x.equals(z)` вернёт `true`;
+ _Непротиворечивость_: для любых ссылок на значения `х` и `у`, если несколько раз вызвать `х.equals(y)`, постоянно будет возвращаться значение `true` либо постоянно будет возвращаться значение `false` при условии, что никакая информация, используемая при сравнении объектов, не поменялась.

Для любой ненулевой ссылки на значение `х` выражение `х.equals(null)` должно возвращать `false`.

[к оглавлению](#Класс-object)

## Правила переопределения метода `Object.equals()`.
1. Использование оператора `==` для проверки, является ли аргумент ссылкой на указанный объект. Если является, возвращается `true`. Если сравниваемый объект `== null`, должно вернуться `false`.
2. Использование оператор `instanceof` и вызова метода `getClass()` для проверки, имеет ли аргумент правильный тип. Если не имеет, возвращается `false`.
3. Приведение аргумента к правильному типу. Поскольку эта операция следует за проверкой `instanceof` она гарантированно будет выполнена.
4. Обход всех значимых полей класса и проверка того, что значение поля в текущем объекте и значение того же поля в проверяемом на эквивалентность аргументе соответствуют друг другу. Если проверки для всех полей прошли успешно, возвращается результат `true`, в противном случае - `false`.

По окончанию переопределения метода `equals()` следует проверить: является ли порождаемое отношение эквивалентности рефлексивным, симметричным, транзитивным и непротиворечивым? Если ответ отрицательный, метод подлежит соответствующей правке.

[к оглавлению](#Класс-object)

## Какая связь между `hashCode()` и `equals()`?
## Если `equals()` переопределен, есть ли какие-либо другие методы, которые следует переопределить?
Равные объекты должны возвращать одинаковые хэш коды. При переопределении `equals()` нужно обязательно переопределять и метод `hashCode()`.

[к оглавлению](#Класс-object)

## Что будет, если переопределить `equals()` не переопределяя `hashCode()`? Какие могут возникнуть проблемы?
Классы и методы, которые используют правила этого контракта могут работать некорректно. Так для `HashMap` это может привести к тому, что пара «ключ-значение», которая была в неё помещена при использовании нового экземпляра ключа не будет в ней найдена.

[к оглавлению](#Класс-object)

## Каким образом реализованы методы `hashCode()` и `equals()` в классе `Object`?
Реализация метода `Object.equals()` сводится к проверке на равенство двух ссылок:

```java
public boolean equals(Object obj) {
  return (this == obj);
}
```

Реализация метода `Object.hashCode()` описана как `native`, т.е. определенной не с помощью Java кода и обычно возвращает адрес объекта в памяти:

```java 
public native int hashCode();
```

[к оглавлению](#Класс-object)

## Для чего нужен метод `hashCode()`?
Метод `hashCode()` необходим для вычисления хэш кода переданного в качестве входного параметра объекта. В Java это целое число, в более широком смыле - битовая строка фиксированной длины, полученная из массива произвольной длины. Этот метод реализован таким образом, что для одного и того же входного объекта, хэш код всегда будет одинаковым. Следует понимать, что в Java множество возможных хэш кодов ограничено типом `int`, а множество объектов ничем не ограничено. Из-за этого, вполне возможна ситуация, что хэш коды разных объектов могут совпасть:

+ если хэш коды разные, то и объекты гарантированно разные;
+ если хэш коды равны, то объекты могут не обязательно равны.

[к оглавлению](#Класс-object)

## Каковы правила переопределения метода `Object.hashCode()`?
## Есть ли какие-либо рекомендации о том, какие поля следует использовать при подсчете `hashCode()`?
Общий совет: выбирать поля, которые с большой долью вероятности будут различаться. Для этого необходимо использовать уникальные, лучше всего примитивные поля, например, такие как `id`, `uuid`. При этом нужно следовать правилу, если поля задействованы при вычислении `hashCode()`, то они должны быть задействованы и при выполнении `equals()`.

[к оглавлению](#Класс-object)

## Могут ли у разных объектов быть одинаковые `hashCode()`?
Да, могут. Метод `hashCode()` не гарантирует уникальность возвращаемого значения. Ситуация, когда у разных объектов одинаковые хэш коды называется _коллизией_. Вероятность возникновения коллизии зависит от используемого алгоритма генерации хэш кода.

[к оглавлению](#Класс-object)

## Если у класса `Point{int x, y;}` реализовать метод `equals(Object that) {(return this.x == that.x && this.y == that.y)}`, но сделать хэш код в виде `int hashCode() {return x;}`, то будут ли корректно такие точки помещаться и извлекаться из `HashSet`?
`HashSet` использует `HashMap` для хранения элементов. При добавлении элемента в `HashMap` вычисляется хэш код, по которому определяется позиция в массиве, куда будет вставлен новый элемент. У всех экземпляров класса `Point` хэш код будет одинаковым для всех объектов с одинаковым `x`, что приведёт к вырождению хэш таблицы в список. 

При возникновении коллизии в `HashMap` осуществляется проверка на наличие элемента в списке: `e.hash == hash && ((k = e.key) == key || key.equals(k))`. Если элемент найден, то его значение перезаписывается. В нашем случае для разных объектов метод `equals()` будет возвращать `false`. Соответственно новый элемент будет успешно добавлен в `HashSet`. Извлечение элемента также будет осуществляться успешно. Но производительность такого кода будет невысокой и преимущества хэш таблиц использоваться не будут.

[к оглавлению](#Класс-object)

## Могут ли у разных объектов `(ref0 != ref1)` быть `ref0.equals(ref1) == true`?
Да, могут. Для этого в классе этих объектов должен быть переопределен метод `equals()`.

Если используется метод `Object.equals()`, то для двух ссылок `x` и `y` метод вернет `true` тогда и только тогда, когда обе ссылки указывают на один и тот же объект (т.е. `x == y` возвращает `true`).

[к оглавлению](#Класс-object)

## Могут ли у разных ссылок на один объект `(ref0 == ref1)` быть `ref0.equals(ref1) == false`?
В общем случае - могут, если метод `equals()` реализован некорректно и не выполняет свойство рефлексивности: для любых ненулевых ссылок `x` метод `x.equals(x)` должен возвращать `true`.

[к оглавлению](#Класс-object)

## Можно ли так реализовать метод `equals(Object that) {return this.hashCode() == that.hashCode()}`?
Строго говоря нельзя, поскольку метод `hashCode()` не гарантирует уникальность значения для каждого объекта. Однако для сравнения экземпляров класса `Object` такой код допустим, т.к. метод `hashCode()` в классе `Object` возвращает уникальные значения для разных объектов (его вычисление основано на использовании адреса объекта в памяти).

[к оглавлению](#Класс-object)

## В `equals()` требуется проверять, что аргумент `equals(Object that)` такого же типа что и сам объект. В чем разница между `this.getClass() == that.getClass()` и `that instanceof MyClass`?
Оператор `instanceof` сравнивает объект и указанный тип. Его можно использовать для проверки является ли данный объект экземпляром некоторого класса, либо экземпляром его дочернего класса, либо экземпляром класса, который реализует указанный интерфейс.

`this.getClass() == that.getClass()` проверяет два класса на идентичность, поэтому для корректной реализации контракта метода `equals()` необходимо использовать точное сравнение с помощью метода `getClass()`.

[к оглавлению](#Класс-object)

## Можно ли реализовать метод `equals()` класса `MyClass` вот так: `class MyClass {public boolean equals(MyClass that) {return this == that;}}`?
Реализовать можно, но данный метод не переопределяет метод `equals()` класса `Object`, а перегружает его.

[к оглавлению](#Класс-object)

## Есть класс `Point{int x, y;}`. Почему хэш код в виде `31 * x + y` предпочтительнее чем `x + y`?
Множитель создает зависимость значения хэш кода от очередности обработки полей, что в итоге порождает лучшую хэш функцию.

[к оглавлению](#Класс-object)

## Расскажите про клонирование объектов.
Использование оператора присваивания не создает нового объекта, а лишь копирует ссылку на объект. Таким образом, две ссылки указывают на одну и ту же область памяти, на один и тот же объект. Для создания нового объекта с таким же состоянием используется клонирование объекта. 

Класс `Object` содержит `protected` метод `clone()`, осуществляющий побитовое копирование объекта производного класса. Однако сначала необходимо переопределить метод `clone()` как `public` для обеспечения возможности его вызова. В переопределенном методе следует вызвать базовую версию метода `super.clone()`, которая и выполняет собственно клонирование. 

Чтобы окончательно сделать объект клонируемым, класс должен реализовать интерфейс `Cloneable`. Интерфейс `Cloneable` не содержит методов относится к маркерным интерфейсам, а его реализация гарантирует, что метод `clone()` класса `Object` возвратит точную копию вызвавшего его объекта с воспроизведением значений всех его полей. В противном случае метод генерирует исключение `CloneNotSupportedException`. Следует отметить, что при использовании этого механизма объект создается без вызова конструктора.

Это решение эффективно только в случае, если поля клонируемого объекта представляют собой значения базовых типов и их обёрток или неизменяемых (immutable) объектных типов. Если же поле клонируемого типа является изменяемым ссылочным типом, то для корректного клонирования требуется другой подход. Причина заключается в том, что при создании копии поля оригинал и копия представляют собой ссылку на один и тот же объект. В этой ситуации следует также клонировать и сам объект поля класса.

Такое клонирование возможно только в случае, если тип атрибута класса также реализует интерфейс `Cloneable` и переопределяет метод `clone()`. Так как, если это будет иначе вызов метода невозможен из-за его недоступности. Отсюда следует, что если класс имеет суперкласс, то для реализации механизма клонирования текущего класса-потомка необходимо наличие корректной реализации такого механизма в суперклассе. При этом следует отказаться от использования объявлений `final` для полей объектных типов по причине невозможности изменения их значений при реализации клонирования.

Помимо встроенного механизма клонирования в Java для клонирования объекта можно использовать:

+ __Специализированный конструктор копирования__ - в классе описывается конструктор, который принимает объект этого же класса и инициализирует поля создаваемого объекта значениями полей переданного.
+ __Фабричный метод__ - (Factory method), который представляет собой статический метод, возвращающий экземпляр своего класса.
+ __Механизм сериализации__ - сохранение и последующее восстановление объекта в/из потока байтов.

[к оглавлению](#Класс-object)

## В чем отличие между _поверхностным_ и _глубоким_ клонированием?
__Поверхностное копирование__ копирует настолько малую часть информации об объекте, насколько это возможно. По умолчанию, клонирование в Java является поверхностным, т.е. класс `Object` не знает о структуре класса, которого он копирует. Клонирование такого типа осуществляется JVM по следующим правилам: 

+ Если класс имеет только члены примитивных типов, то будет создана совершенно новая копия объекта и возвращена ссылка на этот объект.
+ Если класс помимо членов примитивных типов содержит члены ссылочных типов, то тогда копируются ссылки на объекты этих классов. Следовательно, оба объекта будут иметь одинаковые ссылки.

__Глубокое копирование__ дублирует абсолютно всю информацию объекта:
+ Нет необходимости копировать отдельно примитивные данные;
+ Все члены ссылочного типа в оригинальном классе должны поддерживать клонирование. Для каждого такого члена при переопределении метода `clone()` должен вызываться `super.clone()`;
+ Если какой-либо член класса не поддерживает клонирование, то в методе клонирования необходимо создать новый экземпляр этого класса и скопировать каждый его член со всеми атрибутами в новый объект класса, по одному.

[к оглавлению](#Класс-object)

## Какой способ клонирования предпочтительней?
Наиболее безопасным и, следовательно, предпочтительным способом клонирования является использование специализированного конструктора копирования: 

+ Отсутствие ошибок наследования (не нужно беспокоиться, что у наследников появятся новые поля, которые не будут склонированы через метод `clone()`);
+ Поля для клонирования указываются явно;
+ Возможность клонировать даже `final` поля.

[к оглавлению](#Класс-object)

## Почему метод `clone()` объявлен в классе `Object`, а не в интерфейсе `Cloneable`?
Метод `clone()` объявлен в классе `Object` с указанием модификатора `native`, чтобы обеспечить доступ к стандартному механизму поверхностного копирования объектов. Одновременно он объявлен и как `protected`, чтобы нельзя было вызвать этот метод у не переопределивших его объектов. Непосредственно интерфейс `Cloneable` является маркерным (не содержит объявлений методов) и нужен только для обозначения самого факта, что данный объект готов к тому, чтобы быть клонированным. Вызов переопределённого метода `clone()` у не `Cloneable` объекта вызовет выбрасывание `CloneNotSupportedException`.

[к оглавлению](#Класс-object)


## ССЫЛКИ НА ДОПОЛНИТЕЛЬНУЮ ИНФУ
#### [Название-->](Ссылка)


[к оглавлению](#Класс-object)