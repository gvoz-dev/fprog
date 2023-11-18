# §2.8. Итерация, рекурсия

[К началу главы](CHAPTER_2.md)

## Рекурсия

В прошлом разделе мы поближе познакомились со списком, который является рекурсивной структурой данных.

*Рекурсия* - это определение объекта с использованием самого этого объекта.

Запустите следующую программу, которая рисует треугольник Серпинского - пример рекурсии:

```scheme
#lang racket

(require 2htdp/image)

(let sierpinski ([n 8])
  (if (zero? n)
      (triangle 2 'solid 'red)
      (let ([t (sierpinski (- n 1))])
        (freeze (above t (beside t t))))))
```

Функция называется рекурсивной, если она вызывается внутри себя.  
Рекурсию необходимо ограничивать с помощью терминальной операции - специальной ветки алгоритма, которая завершает рекурсию.

Классическим примером рекурсивной функции является функция вычисления факториала:

$$
n! = n \cdot [(n - 1) \cdot (n - 2) \cdots 3 \cdot 2 \cdot 1] = n \cdot (n - 1)!
$$

```scheme
(define (factorial n)
  (if (= n 1)
      1
      (* n (factorial (- n 1)))))

(factorial 5) ; 120
```

Другой способ вычисления факториала - итеративный:

$$
произведение = счётчик \cdot произведение \\
счётчик = счётчик + 1
$$

```scheme
(define (factorial n)
  (fact-iter 1 1 n))

(define (fact-iter product counter n)
  (if (> counter n)
      product
      (fact-iter (* counter product)
                 (+ counter 1)
                 n)))

(factorial 5) ; 120
```

Переменные состояния product и counter называются аккумуляторами, а сам способ определения функции fact-iter - *хвостовой рекурсией*.

Рекурсию можно применять для итерации по списку. Например, в следующем примере подсчитывается сумма элементов списка:

```scheme
(define (list-sum lst)
  (if (empty? lst)
      0
      (+ (car lst)
         (list-sum (cdr lst)))))

(list-sum '(1 2 3 4 5)) ; 15
(list-sum '(1)) ; 1
(list-sum '()) ; 0
```

---
Продолжение следует...