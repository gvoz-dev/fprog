# §2.9. Макросы

[К началу главы](CHAPTER_2.md)

## Макросы

Макросы - это специальные функции, которые генерируют код вместо результата. Это мощное средство, потому что они позволяют определять совершенно новые абстракции внутри самого языка.

> Выполнение макросов происходит на этапе компиляции.

Макрос можно создать, используя специальную форму **define-syntax-rule**:

```scheme
(define-syntax-rule pattern template)
```

Template подставляется вместо формы, которая соответствует pattern.

### Пример макроса - swap

```scheme
(define-syntax-rule (swap x y)
  (let ([tmp x])
    (set! x y)
    (set! y tmp)))
```

### Пример макроса - цикл for

```scheme
(define-syntax-rule (for-loop [sym init check change] steps)
  (let loop ([sym init]
             [value #f])
    (if check
        (let ([new-value (let () steps)])
          (loop change new-value))
        value)))

(for-loop [i 0 (< i 10) (add1 i)]
          (println i))
```
