`null` задаётся переменной явно и означает, что она является объектом, но структура этого объекта ещё не определена. `undefined` присваивается переменной (переменная не декларирует объект), когда она была объявлена, но не было определено её начальное значение. Функция может возвращать `undefined` или `null`. Всё зависит от того, что мы ожидаем в результате работы функции. Если мы ожидаем объект, но по каким-то причинам функция его вернуть не может, то возвращаем `null`. Если функция должна вернуть, например, число (главное, не объект), но не может этого сделать, то она возвращает `undefined`.

Без начального значения можно оставлять только переменную, объявленную через `let` или `var`. Если объявить переменную через `const` и не задать ей начального значения, будет ошибка: `Uncaught SyntaxError: Missing initializer in const declaration`.

Поговорим немного о [приведении типов](/js/typecasting/). Для начала, пример:

```js
console.log(null + null); // 0
console.log(undefined + undefined); // NaN
```

Почему так?

По [спецификации EcmaScript](https://262.ecma-international.org/7.0/#sec-tonumber)

- `null` во время сложения приводится к нулю;
- `undefined` во время сложения приводится к `NaN`. `NaN` это аббревиатура от "not a number" — не число. Результат арифметической операции равен `NaN`, если во время операции произошла ошибка и ожидаемый числовой результат не может быть выражен числом.

Есть ещё один хитрый пример:

```js
console.log(null + []); // "null"
```

Почему так?

Подсказка, почему так, кроется именно в типе результате: "null" — строка. А не примитивное значение `null`.

JavaScript сначала приводит массив к примитивному значению. Для этого вызывается метод `toString()`, который вызывает метод `join()`. Т.к. массив пустой, то `join()` вернёт пустую строку `""`. А сложение чего-то со строкой в JS возвращает строку. Поэтому `null` уже никуда не приводится, а возращается строка `"null"`.

Немного упомяну и про оператор нулевого слияния (`??`). В выражении между двумя операндами он будет возвращать первый операнд, если он не равен `null` или `undefined`. Можно сказать, что `??` приравнивает смысл `undefined` и `null` к «ничего не содержит», и, в этом случае, кладёт в переменную значение второго операнда.
