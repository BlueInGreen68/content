Ответ очень простой – нужно воспользоваться специальной функцией `Number.isNaN()`. В качестве аргумента нужно передать проверяемую переменную.

Вас может запутать формулировка вопроса: `typeof possiblyWrongNumber === 'number'`. Это же **not** a number, подумаете вы. Дело в том, что `NaN` используется для обозначения результатов вычислений, в которых «что-то пошло не так». Можете думать о `NaN` так: «Тут должно быть число, но вычисление сломалось». Это может произойти, если захотите вычислить квадратный корень из `-1`. В результате получится комплексное число, с которым наш браузер из коробки работать не умеет.

Неправильным ответом на этот вопрос будет вот такая проверка:

```js
possiblyWrongNumber === NaN
```

Однако в ней уже содержится ответ на более хитрый дополнительный вопрос:

❓ Представим себе, что функции `Number.isNaN()` не существует. Как в таком случае проверить, что значение переменной `possiblyWrongNumber` не является `NaN`? Условие `typeof possiblyWrongNumber === 'number'` по-прежнему выполняется.

Ответ такой: просто нужно сравнить значение переменной `possiblyWrongNumber` с самим собой. Если они равны, значит в переменной не `NaN`:

```js
possiblyWrongNumber === possiblyWrongNumber
```
