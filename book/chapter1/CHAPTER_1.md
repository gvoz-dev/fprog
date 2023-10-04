# Введение в функциональное программирование

[К содержанию](../../README.md)

## Краткое описание парадигмы

[Функциональное программирование](https://ru.wikipedia.org/wiki/%D0%A4%D1%83%D0%BD%D0%BA%D1%86%D0%B8%D0%BE%D0%BD%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%B5_%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5) - это парадигма программирования, в которой особое значение придаётся использованию чистых функций и неизменяемых данных.

$$
f : X \rightarrow Y
$$

Чистые функции - это такие функции, которые, во-первых, не имеют побочных эффектов, а во-вторых, являются детерминированными.

Другими важными свойствами функций в функциональном программировании являются ленивость и возможность производить частичные вычисления.

Кроме этого функции сами по себе могут быть объектами вычислений, т.е. передаваться в качестве параметров другим функциям и быть возвращаемыми в качестве результатов. Функция, принимающая на вход или возвращающая функцию называется функцией высшего порядка (оператором, функционалом).

## Некоторые вехи из истории функционального программирования

Теоретической базой для появления функционального программирования является λ-исчисление, которое разработал американский математик [Алонзо Чёрч](https://ru.wikipedia.org/wiki/%D0%A7%D1%91%D1%80%D1%87,_%D0%90%D0%BB%D0%BE%D0%BD%D0%B7%D0%BE) в 30-х годах прошлого века для формализации и анализа понятия вычислимости.

Первым функциональным языком является LISP, созданный [Джоном Маккарти](https://ru.wikipedia.org/wiki/%D0%9C%D0%B0%D0%BA%D0%BA%D0%B0%D1%80%D1%82%D0%B8,_%D0%94%D0%B6%D0%BE%D0%BD) в конце 1950-х годов.

В 1970-х годах [Робином Милнером](https://ru.wikipedia.org/wiki/%D0%9C%D0%B8%D0%BB%D0%BD%D0%B5%D1%80,_%D0%A0%D0%BE%D0%B1%D0%B8%D0%BD) был создан язык ML, на основе которого впоследствии были разработаны Standard ML и OCaml.

В середине 1980-х годов в компании Ericsson для разработки телекоммуникационных систем [Джо Армстронгом](https://ru.wikipedia.org/wiki/%D0%90%D1%80%D0%BC%D1%81%D1%82%D1%80%D0%BE%D0%BD%D0%B3,_%D0%94%D0%B6%D0%BE_(%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%81%D1%82)) был создан язык Erlang.

В конце 1980-х годов был создан Haskell - чистый функциональный язык, вобравший в себя множество идей, полученных в ходе исследования функциональной парадигмы.

В начале 2000-х появились современные функциональные языки для виртуальной машины Java: Scala ([Мартин Одерски](https://ru.wikipedia.org/wiki/%D0%9E%D0%B4%D0%B5%D1%80%D1%81%D0%BA%D0%B8,_%D0%9C%D0%B0%D1%80%D1%82%D0%B8%D0%BD)) и Clojure ([Рич Хикки](https://ru.wikipedia.org/wiki/%D0%A5%D0%B8%D0%BA%D0%BA%D0%B8,_%D0%A0%D0%B8%D1%87%D0%B0%D1%80%D0%B4)).

## Языки функционального программирования

Наиболее известными функциональными языками являются:
- [LISP](https://ru.wikipedia.org/wiki/%D0%9B%D0%B8%D1%81%D0%BF)
  - [Common Lisp](https://ru.wikipedia.org/wiki/Common_Lisp)
  - [Scheme](https://ru.wikipedia.org/wiki/Scheme)
  - [Clojure](https://ru.wikipedia.org/wiki/Clojure)
- [ML](https://ru.wikipedia.org/wiki/ML)
  - [Standard ML](https://ru.wikipedia.org/wiki/Standard_ML)
  - [OCaml](https://ru.wikipedia.org/wiki/OCaml)
  - [F#](https://ru.wikipedia.org/wiki/F_Sharp)
- [Haskell](https://ru.wikipedia.org/wiki/Haskell)
- [Erlang](https://ru.wikipedia.org/wiki/Erlang)
- [Scala](https://ru.wikipedia.org/wiki/Scala_(%D1%8F%D0%B7%D1%8B%D0%BA_%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F))

## Мотивация

Функциональная парадигма программирования после долгих лет развития исключительно в академической среде легитимизируется и входит в мейнстрим. Современные языки программирования часто используют идеи и идиомы, пришедшие из функционального программирования.

Например, отказ от ручного управления памятью и *сборка мусора* впервые появилась в LISP - первом функциональном языке программирования.

На обобщённое программирование (*generic programming*) повлияла система типов языков семейства ML.

*Лямбда-выражения*, которые появились в Java (и во многих других языках), также пришли из LISP:

```java
BinaryOperator<Double> addition = (a, b) -> a + b;
System.out.println("40 + 2 = " + addition.apply(40.0, 2.0));

UnaryOperator<Double> square = x -> Math.pow(x, 2);
System.out.println("5.7 ^ 2 = " + square.apply(5.7));
```

Stream API из Java позволяет обрабатывать наборы данных в функциональном стиле:

```java
double weightSum = items.stream()
                        .filter(item -> item.color() == RED)
                        .mapToDouble(Item::weight)
                        .sum();
```

LINQ из C# предоставляет возможности для написания выразительного декларативного кода запросов ко многим источникам данных:

```cs
var filteredItems = from item in items
                    where item.Color == RED
                    select item;
```

Тот же пример, использующий API IEnumerable:

```cs
var filteredItems = items.Where(item => item.Color == RED);
```

И Stream API из Java и LINQ из C# к тому же позволяют без проблем использовать преимущества параллельной обработки данных.

Генераторы списков из Python пришли из функциональных языков (Haskell, Miranda):

```python
squares = [(lambda i: i * i)(i) for i in range(0, 10)]
```

Сопоставление с образцом (*pattern matching*) - новое веяние в современных языках промышленной разработки, которое тоже пришло из функционального программирования.

```java
public static double getPerimeter(Shape s) throws IllegalArgumentException {
    return switch (s) {
        case Rectangle r -> 2 * r.length() + 2 * r.width();
        case Circle c    -> 2 * c.radius() * Math.PI;
        default          -> throw new IllegalArgumentException("Unrecognized shape");
    };
}
```

[И многое-многое другое...](https://habr.com/ru/companies/typeable/articles/589257/)  
К тому же многие шаблоны в объектно-ориентированном проектировании можно рассматривать как идиоматическое воспроизведение элементов функциональных языков.

## Резюме

Функциональное программирование предоставляет средства для упорядочения побочных эффектов, чтобы они не возникали где угодно. Большую часть действий, изменяющих состояние, можно превратить в чистые функции, чтобы код стал проще и логичнее.

Владение функциональной парадигмой в её "чистом" виде позволяет эффективно применять новые функциональные элементы современных языков для управления сложностью разрабатываемых систем.