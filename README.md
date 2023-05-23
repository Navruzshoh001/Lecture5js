# Lecture5js

## Объекты

>Как мы знаем из главы Типы данных, в JavaScript существует 8 типов данных. Семь из них называются «примитивными», так как содержат только одно значение (будь то строка, число или что-то другое).

Объекты же используются для хранения коллекций различных значений и более сложных сущностей. В JavaScript объекты используются очень часто, это одна из основ языка. Поэтому мы должны понять их, прежде чем углубляться куда-либо ещё.

Объект может быть создан с помощью фигурных скобок {…} с необязательным списком свойств. Свойство – это пара «ключ: значение», где ключ – это строка (также называемая «именем свойства»), а значение может быть чем угодно.

Мы можем представить объект в виде ящика с подписанными папками. Каждый элемент данных хранится в своей папке, на которой написан ключ. По ключу папку легко найти, удалить или добавить в неё что-либо.

>let user = new Object(); // синтаксис "конструктор объекта" let user = {}; // синтаксис "литерал объекта" Объект, объявленный через const, может быть изменён.

Например:

const user = { name: "John" };

user.name = "Pete"; // (*)

alert(user.name); // Pete Может показаться, что строка (*) должна вызвать ошибку, но нет, здесь всё в порядке. Дело в том, что объявление const защищает от изменений только саму переменную user, а не её содержимое.

Определение const выдаст ошибку только если мы присвоим переменной другое значение: user=....

Есть ещё один способ сделать константами свойства объекта, который мы рассмотрим в главе

>let user = { name: "John", age: 30 };

let key = prompt("Что вы хотите узнать о пользователе?", "name");

// доступ к свойству через переменную alert( user[key] ); // John (если ввели "name")

## Metodh object js

>keys для ключей показивает ключей values - для элемнтов показивает элементов entries - сделает из обекта массив каждое ключ и элемент один масив this у вай он Усулҳо ба монанди call(), application() ва bind() метавонанд инро ба ягон объект ишора кунанд Explicit Function Binding The call() and apply() methods are predefined JavaScript methods. They can both be used to call an object method with another object as argument. Ҳатмӣ будани функсияи ошкор Усулҳои call() ва application() усулҳои пешакӣ муайяншудаи JavaScript мебошанд. Ҳардуи онҳоро метавон истифода бурд, ки усули объектро бо объекти дигар ҳамчун далел даъват кунад.

## undefind

>Запись «через точку» такого не позволяет:

let user = { name: "John", age: 30 };

let key = "name"; alert( user.key ); // undefined

## Свойство из переменной

>В реальном коде часто нам необходимо использовать существующие переменные как значения для свойств с тем же именем.

Например:

function makeUser(name, age) { return { name: name, age: age // ...другие свойства }; }

let user = makeUser("John", 30); alert(user.name); // John

## Ограничения на имена свойств

>Как мы уже знаем, имя переменной не может совпадать с зарезервированными словами, такими как «for», «let», «return» и т.д.

Но для свойств объекта такого ограничения нет:

// эти имена свойств допустимы let obj = { for: 1, let: 2, return: 3 };

alert( obj.for + obj.let + obj.return ); // 6

## Проверка существования свойства, оператор «in»

>В отличие от многих других языков, особенность JavaScript-объектов в том, что можно получить доступ к любому свойству. Даже если свойства не существует – ошибки не будет!

При обращении к свойству, которого нет, возвращается undefined. Это позволяет просто проверить существование свойства:

let user = {};

alert( user.noSuchProperty === undefined ); // true означает "свойства нет" Также существует специальный оператор "in" для проверки существования свойства в объекте.

Синтаксис оператора:

"key" in object Пример:

let user = { name: "John", age: 30 };

alert( "age" in user ); // true, user.age существует alert( "blabla" in user ); // false, user.blabla не существует Обратите внимание, что слева от оператора in должно быть имя свойства. Обычно это строка в кавычках.

Если мы опускаем кавычки, это значит, что мы указываем переменную, в которой находится имя свойства. Например:

let user = { age: 30 };

let key = "age"; alert( key in user ); // true, имя свойства было взято из переменной key Для чего вообще нужен оператор in? Разве недостаточно сравнения с undefined?

В большинстве случаев прекрасно сработает сравнение с undefined. Но есть особый случай, когда оно не подходит, и нужно использовать "in".

Это когда свойство существует, но содержит значение undefined:

let obj = { test: undefined };

alert( obj.test ); // выведет undefined, значит свойство не существует? alert( "test" in obj ); // true, свойство существует! В примере выше свойство obj.test технически существует в объекте. Оператор in сработал правильно.

Подобные ситуации случаются очень редко, так как undefined обычно явно не присваивается. Для «неизвестных» или «пустых» свойств мы используем значение null. Таким образом, оператор in является экзотическим гостем в коде.

[](data:image/png;base64,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)