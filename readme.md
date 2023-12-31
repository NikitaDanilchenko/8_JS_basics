Tемы для ревью:

#1 Хранение чисел, неточные вычисления
В современном JavaScript существует два типа чисел:

---Обычные числа в JavaScript хранятся в 64-битном формате IEEE-754, который также называют «числа с плавающей точкой двойной точности» (double precision floating point numbers). Это числа, которые мы будем использовать чаще всего. Мы поговорим о них в этой главе.

---BigInt числа дают возможность работать с целыми числами произвольной длины. Они нужны достаточно редко и используются в случаях, когда необходимо работать со значениями более чем (2 в 53(ст)-1) или менее чем -(2 в 53(ст)-1).

В JavaScript, чтобы укоротить запись числа, мы можем добавить к нему букву "e" и указать необходимое количество нулей:
let billion = 1e9 //один миллиард

alert(7.3e9) // 7.3 миллиарда 

"e" умножает число на 1 с указанным количеством нулей.

!Шеснадцатеричные числа 0х(число)
!Восьмеричные числа 0о(число)
!Двоичные числа 0b(число)

toString(Base)
Метод num.toString(base) возвращает строковое представление числа num в системе счисления base.
Например:

let num = 255;

alert(num.toString(16)); // ff
alert(num.toString(2)); // 11111111
alert(123456..toString(36) ); // 2n9c
Внимание! Две точки в 123456..toString(36) это не опечатка. Если нам надо вызвать метод непосредственно на числе, как toString в примере выше, то нам надо поставить две точки .. после числа.

base16
base2
base36


Округление
Math.floor
    Округление в меньшую сторону: 3.1 становится 3, а -1.1 — -2.
Math.ceil
    Округление в большую сторону: 3.1 становится 4, а -1.1 — -1.

Math.round
    Округление до ближайшего целого: 3.1 становится 3, 3.6 — 4, а -1.1 — -1.
Math.trunc(не поддерживается в Internet Explorer)
    Производит удаление дробной части без округления: 3.1 становится 3, а -1.1 — -1.
см.таблицу


!!!Неточные вычисления.
Внутри JavaScript число представлено в виде 64-битного формата IEEE-754. Для хранения числа используется 64 бита: 52 из них используется для хранения цифр, 11 для хранения положения десятичной точки и один бит отведён на хранение знака.

Если число слишком большое, оно переполнит 64-битное хранилище, JavaScript вернёт бесконечность:
alert(1e500); // infinity

!Наиболее надёжный способ — это округлить результат используя метод toFixed(n):
let sum = 0.1 + 0.3;
alert(sum.toFixed(2)); // 0.40


Проверка isFinite
    isFinite(value) преобразует аргумент в число и возвращает true, если оно является обычным числом, т.е. не NaN/Infinity/-Infinity:
    alert(isFinite("str")); //false
    alert(isFinite(15)); // true
    alert(isFinite(infinity)); //false
Проверка isNaN
    isNaN(value) преобразует значение в число и проверяет является ли оно NaN:
    alert(isNaN("str")); //true
    alert(isNaN(NaN)); //true
    alert(NaN === NaN); // false

Number.isNaN(value) возвращает true только в том случае, если аргумент принадлежит к типу number и является NaN. Во всех остальных случаях возвращает false.

Number.isFinite(value) возвращает true только в том случае, если аргумент принадлежит к типу number и не является NaN/Infinity/-Infinity. Во всех остальных случаях возвращает false.
======================================================================
#Ошибки
#Рекурсия
#Замыкания и область видимости
#Различия var/let/const, hoisting
#Модули / экспорты
#Побочные эффекты, чистота функций
#Guard Expression / ранний возврат
#Значения по умолчанию
#Функции высшего порядка
#Отличия стрелочных функций от обычных
#map / filter / reduce / forEach / find / flat / includes / indexOf / join / slice / splice / sort