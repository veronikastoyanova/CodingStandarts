[Назад](../README.md)

1. [Въведение](#introduction)
2. [Форматиране](#formating)  
    2.1. [Файлове](#files)  
    2.2. [Отстояния](#spacing)  
    2.3. [Дължина на реда](#row)  
    2.4. [Кавички](#quotes)  
    2.5. [Коментари](#comments)  
    2.6. [Оператори за сравнение и равенство](#conditions)  
    2.7. [Именуване](#naming)  
    2.8. [Декларация на променливи](#declaration)
    2.9. [Функции](#functions)  
    2.10. [Обекти](#objects)  
    2.11. [Класове и конструктори](#classes)  
    2.12. [Низове](#strings)  
    2.13. [Масиви](#array)  
    2.14. [Изрази](#expression)  
    2.15. [Връщане на стойност](#return)  
    2.16. [If изрази](#if-statements)  
    2.17. [For цикли](#for-loops)  
    2.18. [While, Do...while](#do-while)  
    2.19. [Switch...case](#switch)  
    2.20. [Try...catch](#try-catch)  
3. [jQuery](#jQuery)
4. [Забранени неща](#forbidden)
5. [Препоръчителни неща](#good-to)  
    5.1. [Деструктуриране (Destructuring) ](#destructuring)  
    5.2. [Низове](#good-strings)  
    5.3. [Обекти](#good-objects)  
    5.4. [Класове](#good-classes)  

### <a name="introduction">1. Въведение</a>
Този документ има за цел да наложи базовите правила и представи добрите практики при писане/менажиране на JavaScript код.
Стриктното спазване на посочените по-долу правила  и добри практики ще спомогне в настоящата и бъдеща работа на development екипа.

### <a name="formating">2. Форматиране</a>

#### <a name="files">2.1. Файлове</a>
* Файловете трябва да са с **UTF-8** кодиране, заради съвместимостта му с различни азбуки.
* За край на реда трябва да се ползва UNIX стил - символ `LF (\n)`.
* Имената на файловете трябва да съдържат **единствено**: малки букви, числа, точки и тирета.
* Думите в имената трябва да се отделят с тирета `-`, а смисловият тип с точки `.` .
```text
profile-settings.view.js // вярно
profileSettings-view.js // грешно
http.service.js // вярно
httpService.js // грешно
```
#### <a name="spacing">2.2. Отстояния</a>
* Едно стандартно странично отстояние трябва да е 2 интервала, наричано от тук нататък **една индентация**.
* **Никога не използвайте табове**, това може да доведе до нееднороден изглед в различните среди/редактори. 
Повечето редактори имат настройка да обръщат табовете в интервали.
* Винаги слагайте интервал след ключови думи.
```js
// грешно
if(condition) {
    // ... 
}
  
// правилно
if (condition) {
    // ... 
} 
```
* Операторите като `*`, `/`, `+`, `-`, `=` трябва да бъдат отделени с интервал.
```js
// грешно
let x=2;
let message = 'hello, '+name+'!';
  
// правилно
let x = 2;
let message = 'hello, ' + name + '!';
```
* Запетайките `,` трябва да имат разстояние след тях.
```js
// грешно
let list = [1,2,3,4];
  
// правилно
let list = [1, 2, 3, 4];
```
* Винаги слагайте интервал пред отваряща скоба `{`.
```js
// грешно
function test(){
  console.log('test');
}
  
// правилно
function test() {
  console.log('test');
}
  
// грешно
dog.set('attr',{
  age: '1 year',
  breed: 'Bernese Mountain Dog'
});
  
// правилно
dog.set('attr', {
  age: '1 year',
  breed: 'Bernese Mountain Dog'
});
```
* Не се слагат интервали в кръгли скобите `()`.
```js
// грешно
function bar( foo ) {
  return foo;
}
  
// правилно
function bar(foo) {
  return foo;
}
  
// грешно
if ( foo ) {
  console.log(foo);
}
  
// правилно
if (foo) {
  console.log(foo);
}

//incorrect
console.log( {
    foo: 'bar'
} );

//correct
console.log({
    foo: 'bar'
});

```
* Не се слагат интервали в квадратни скобите `[]`.
```js
// грешно
const FOO = [ 1, 2, 3 ];
console.log(FOO[ 0 ]);
  
// правилно
const FOO = [1, 2, 3];
console.log(FOO[0]);
```
* Добавят се интервали в къдрави скоби `{}`.
```js
// грешно
const FOO = {clark: 'kent'};
  
// правилно
const FOO = { clark: 'kent' };
```

#### <a name="row">2.3 Дължина на реда</a>
* Един ред не трябва да бъде по-дълъг от 120 символа.
* Когато един израз надхвърли лимитът от 120 символа, трябва да бъде разделен. За предпочитане това да стане след запетайка или оператор.

#### <a name="quotes">2.4 Кавички</a>
* Използват се единични кавички `''` за всички низове, а двойни кавички `""` се използват само за низове в низовете.
* Тежко ударение се ползват само и единствено когато имаме ES6 низ с шаблон в него.
```js
// грешно
let greeting = "Hello World!";
  
// правилно
let greeting = 'Hello World!';
  
// грешно
let html = "<div class='bold'>Hello World</div>";
  
// грешно
let html = '<div class=\'bold\'>Hello World</div>';
  
// правилно
let html = '<div class="bold">Hello World</div>';

// правилно
let companyName = 'Upnetix';
let slogan = `${companyName} is the Best!`;
```

#### <a name="comments">2.5 Коментари</a>
* Писането на коментари в кода е задължително. То помага за повишаването на четимостта на вашият код.
* Коментарите трябва да бъдат ясни, точно като кодът, който описват.
* Коментарите трябва да бъдат на английски език.
* Коментарите трябва да бъдат смислени.
Неправомерно използване на коментар:
```js
// Set index to zero.
let index = 0;
```
* Всички методи и функции трябва да имат JSDoc документация
JSDoc може да бъде разчетена от средите за разработка за по-добри подсказки.   
Примерна документация:
 ```js
/**
* Takes in a name and returns a greeting string.
*
* @param {string} name - The name of the greeted person.
* @returns {string} - Greeting string. 
*/
function getGreeting(name) {
    return 'Hello ' + name + '!';
}
```

**Вътрешни**
* Вътрешните коментари се използват вътре в сложни изрази (цикли, функции и т.н.).
* Използвайте `//` за всички вътрешни коментари.
* Започвайте коментарът с един интервал в началото. - // Comment
* **Препоръчително** използвайте `//` дори и за многоредови коментари, `/**/` използваме за документиращи коментари (документации на методи и пр.)
* Коментарите трябва да бъдат кратки и ясни.
* Сложете вътрешните коментари на нов ред над реда, който поясняват.
* Сложете празен ред над коментара.
```js
// грешно
let lines = []; // Holds all the lines in the file.
  
// правилно
// Holds all the lines in the file.
let lines = [];
```

**TODO и XXX**
* Подсказки като `TODO` и `XXX`, могат да ви помогнат да намерите неща които трябва да бъдат добавени/отстранени.
* Използвайте `// TODO`: за да отбележете функционалности, които трябва да се добавят.
* Използвайте `// XXX`: за да отбележете проблеми, които трябва да се отстранят.
* Старайте се да пишете код, който не изисква писането на `TODO:` и `XXX:`, но за съжаление това не винаги е възможно.
* **Задължително** Когато изполвате Подсказки като `TODO` и `XXX` пишете **ясен и описателен** коментар какво точно трябва да се направи.
#### <a name="conditions">2.6. Оператори за сравнение и равенство</a>
* При сравняване използвайте `===` и `!==`. Разрешена е употребата на `==` и `!=` само когато сравнявате с `null`.
* Всички условни твърдения оценяват условията си до булева стойност, затова се следват тези правила:
    - Обектите се оценяват до истина
    - Undefined се оценява до неистина
    - Null се оценява до неистина
    - Булевите се оценяват до стойтостта на булевата
    - Числата се оценяват до неистина ако са `+0`, `-0`, или `NaN`, иначе се оценяват до истина
    - Низовете се озиняват до неистина ако са празни `''`, иначе се оценяват до истина
```js
if ([0] && []) {
    // вярно
    // масивът, дори и празен, е обект, обектите се оценяват до true (вярно)
  }
```
* Използват се кратки оценявания за булеви и ясни сравнения за низове и числа.
```js
// Грешно
if (isValid === true) {
  // ...
}
  
// Правилно
if (isValid) {
  // ...
}

// Да се избягва
if (collection.length) {
  // ...
}
  
// Правилно
if (collection.length > 0) {
  // ...
}
```
* За проверка дали една променлива е декларирана се използва `typeof variable !== 'undefined'`.
* Тернарните изрази трябва да са едноредови и да не бъдат влагани.
```js
// Грешно
let foo = maybe1 > maybe2
  ? "bar"
  : value1 > value2 ? "baz" : null;
  
// Грешно
let maybeNull = value1 > value2 ? 'baz' : null;
let foo = maybe1 > maybe2
  ? 'bar'
  : maybeNull;
  
// Правилно
let maybeNull = value1 > value2 ? 'baz' : null;
let foo = maybe1 > maybe2 ? 'bar' : maybeNull;
```
* Избягват се ненужни тернарни изрази.
```js
// Грешно
let foo = a ? a : b;
let bar = c ? true : false;
let baz = c ? false : true;
  
// Правилно
let foo = a || b;
let bar = !!c;
let baz = !c;
```

#### <a name="naming">2.7. Именуване</a>
* Не се използват еднобуквени имена. Хубаво е имената да са описателни.
```js
// bad
function q() {
  // ...
}
  
// good
function query() {
  // ...
}
```
* Всички имена на променливи и на функции трябва да съдържат само символите: `A-Z`, `a-z`, `0-9` и долна черта `_`.
* Променливите, модулите и функциите трябва да се кръщават чрез `camelCase`.
```js
// грешно
let OBJEcttsssss = {};
let this_is_my_object = {};
function c() {}
  
// правилно
let thisIsMyObject = {};
function thisIsMyFunction() {}
```
* PascalCase се използва единствено за именуване на конструктори и класове.
```js
// Грешно
function user(options) {
  this.name = options.name;
}
  
let bad = new user({
  name: 'nope'
});
  
// Правилно
class User {
  constructor(options) {
    this.name = options.name;
  }
}
  
let good = new User({
  name: 'yup'
});
```
* Константите трябва да се именуват чрез `UPPER_UNDERSCORE_CASE` и задължително да се декларират с `const`.
* **Задължително** Булева променливи трябва да се кръщават с имена с **ясно** въпросително значение.
* **Препоръчително** При именуване на булева boolean променлива името да започва с въпросителна частица. Изключение правят тривиалните success, fail, found etc.

#### <a name="declaration">2.8. Декларация на променливи</a>
* Всички променливи трябва да бъдат декларирани преди да бъдат използвани.
```js
// грешно
console.log(a + b);

var a = 2;
var b = 4;
  
// правилно
var a = 2;
var b = 4;

console.log(a + b);
```
* Глобални променливи, декларирани без `var`, `let` или `const` не трябва да се ползват.
* Не трябва да се декларират променливи с едни и същи имена в един и същи обхват `scope`.
* Не трябва да се създават глобални променливи от места с не глобален обхват.
```js
// Грешно
function add(a, b) {
    // „c“ става глобална променлива
    c = 6;

    return a + b + c;
}
```
* Когато декларирате множество от променливи всеки път използвайте ключовите думи `var`, `let` и `const`. По този начин 
лесно се добавят нови променливи и/или им се сменя реда на декларация.
```js
// грешно
let variable1 = 'Hello World!',
    variable2 = 'Testing...',
    variable3 = 42;
  
// грешно
let variable1 = 'Hello World!'
    variable2 = 'Testing...', // изтървана запетая => променливата става глобална
    variable3 = 42; // променливата също става глобална
  
// грешно
// „b“ ще бъде глобална променлива
let a = b = 2, c = 4;
  
// правилно
let variable1 = 'Hello World!';
let variable2 = 'Testing...';
let variable3 = 42;
```
* Десетичните числа в интервалът `(-1, 1)` трябва да започват `0` т.е. `0.5` вместо `.5`.
* Не трябва да се ползват конструкторите на `String`, `Number` и `Boolean`. Използването им води до създаване на обект който 
съдържа в себе си една от тези примитиви, което носи със себе си други странични ефекти.
```js
// При използване тройно равенство:
new Boolean("true") === true; // false
Boolean("true") === true; // true
  
// Така се създават обекти вместо примитиви.
typeof new Boolean("true"); // "object"
typeof Boolean("true"); // "boolean"
```
* Всяка декларирана променлива или константа трябва да бъде използвана някъде иначе няма смисъл от нея.
* За да се провери дали дадена променлива е NaN, трябва да се ползва функцията isNaN, защото NaN !== NaN.
```js
// грешно
a === NaN
  
// правилно
isNaN(a)
```
**Употреба на `var`, `let` и `const`**
* Използвайте `const` винаги когато логиката го позволява (когато създавате променлива (да `променлива` звучи не на място когато става дума за константи), чиято референция/стойност няма да се променя)
  Защото `const` не е само за THE_CONSTANTS_WRITTEN_IN_CAPS но и за всяка променлива, чиято стойност няма да се променя.
* Използвайте `let` във всички останали случаи.
* Избягвайте употребата на `var`.
```js
// const и let съществуват единствено в блока, в който са дефинирани
{
  let a = 1;
  const B = 1;
}
console.log(a); // ReferenceError
console.log(B); // ReferenceError
```
#### <a name="functions">2.9. Функции</a>
**Декларация на функции**
* Всички функции трябва да бъдат декларирани преди да бъдат използвани.
```js
// грешно
function createGreeting(name) {
    let message = 'Hello ';
  
    return greet;
  
    function greet() {
        return message + name + '!';
    }
}
  
// правилно
function createGreeting(name) {
    let message = 'Hello ';
  
    function greet() {
        return message + name + '!';
    }
  
    return greet;
}
```
* Не трябва да има интервал между името на фунцията и отварящата скоба на параметрите `(`.
* Трябва да има един интервал между затварящата скоба на параметрите `)` и отварящата къдрава скоба `{`.
```js
// грешно
function foo (){
    // ...
}
  
// правилно
function foo() {
    // ...
}
```
* Тялото на функцията трябва да е една индентация по-навътре.
* Затварящата къдрава скоба `}` трябва да бъде на нов ред и да е подравнена с редът, на който е отварящата къдрава скоба `{`.
```js
// грешно
function foo() {
  return 'foo';}
  
// правилно
function foo() {
    return 'foo';
}
```
* Никога не се кръщава параметър `arguments`. Този параметър ще има предимство пред обекта на аргументите (the arguments object),
който същствува във всеки обхват на функция.
```js
// bad
function foo(name, options, arguments) {
    // ...
}
  
// good
function foo(name, options, args) {
    // ...
}
``` 
* Избягвайте странични ефекти с параметри по подразбиране
```js
var b = 1;
// Грешно
function count(a = b++) {
  console.log(a);
}
count();  // 1
count();  // 2
count(3); // 3
count();  // 3
```
* Винаги поставяйте параметрите по подразбиране последни.
```js
// грешно
function handleThings(opts = {}, name) {
  // ...
}
  
// правилно
function handleThings(name, opts = {}) {
  // ...
}
```
* Никога не използвайте функционалният конструктор, за да създадете нова функция

**Анонимни функции** * ECMAScript 6 синтаксис
* Всички анонимни функции трябва да бъдат дефинирани като ламбди `() => { }`, освен ако не е абсолютно необходимо да се 
запази оригиналният контекст в тялото на функцията.
* Трябва да има един интервал между затварящата скоба `)` и `=>`.
* Трябва да има един интервал между `=>` и отварящата къдрава скоба `{` която се явява отварящ блок оператор.
* Тялото на израза трябва да е с една индентация навътре спрямо предходният ред.
* Затварящият блок оператор `}` трябва да бъде поставен на нов ред.
* Затварящият блок оператор `}` трябва да бъде подравнен с редът на който е поставен отварящият блок оператор `{`.
```js
// правилно
foo(bar => bar * 2);
  
// правилно
foo(() => {
  bool = true;
});
  
// правилно
[1, 2, 3].map((number) => {
  const nextNumber = number + 1; 
    
  return `A string containing the ${nextNumber}.`;
});
```
#### <a name="hoisting">2.10. Обекти</a>
* Използвайте литерален синтаксис за създаване на обект.
```js
// грешно
const ITEM = new Object();

// правилно
const ITEM = {};
```
* С кавичики се ограждат само пропъртита, коитото са невалидни идентификатори
```js
// грешно
const BAD = {
  'foo': 3,
  'bar': 4,
  'data-blah': 5
};

// правилно
const GOOD = {
  foo: 3,
  bar: 4,
  'data-blah': 5
};
```
* Не се дублират ключове.
```js
let user = {
  name: 'Jane Doe',
  name: 'John Doe'    // ✗ грешно 
}
```
* **Препоръчително** е да се използва `spread` оператора вместо `Object.assign`, за да се копира обект.
* Използвайте обектния `rest` оператор, за да получите нов обект с пропуснати някои от свойствата.
```js
// грешно
const ORIGINAL = { a: 1, b: 2 };
let copy = Object.assign(ORIGINAL, { c: 3 }); // мутира `ORIGINAL` ಠ_ಠ
delete copy.a; // so does this

// грешно
const ORIGINAL = { a: 1, b: 2 };
let copy = Object.assign({}, ORIGINAL, { c: 3 }); // copy => { a: 1, b: 2, c: 3 }

// правилно
const ORIGINAL = { a: 1, b: 2 };
let copy = { ...ORIGINAL, c: 3 }; // copy => { a: 1, b: 2, c: 3 }

let { a, ...noA } = copy; // noA => { b: 2, c: 3 }
```
#### <a name="classes">2.11. Класове и конструктори</a>
* При създаване на нова инстанция на клас винаги трябва да се пишат скобите `()` в края на конструктура.
```js
// грешно
let person = new Person;
  
// правилно
let person = new Person();
```
* Трябва в един файл да съществува само един клас. По този начин се спазва правилото за разделяне на отговорностите при файловете.
* Без дублирани имена в членовете на класа.
```js
class Dog {
  bark () {}
  bark () {}    // ✗ Грешно
}
```
#### <a name="strings">2.12. Низове</a>
* Използват се единични кавички `''`.
```js
// грешно
const NAME = "Capt. Janeway";
    
// грешно
const NAME = `Capt. Janeway`;
  
// правилно
const NAME = 'Capt. Janeway';
```
* Не се ескейпват ненужно символи.
```js
// грешно
const FOO = '\'this\' \i\s \"quoted\"';
  
// правилно
const FOO = '\'this\' is "quoted"';
const FOO = `my name is '${name}'`;
```

#### <a name="array">2.13. Масиви</a>
* Използвайте литерален синтаксис за създаване на масиви.
```js
// грешно
const ITEMS = new Array();
  
// правилно
const ITEMS = [];
```
* Използвайте `Array#push` вместо директното присвояване, за да добавите елементи към масива.
```js
let someStack = [];
  
// грешно
someStack[someStack.length] = 'abracadabra';
  
// правилно
someStack.push('abracadabra');
```
* Използвайте `Array.isArray`, за да проверите дали променлива е масив.
```js
Array.isArray([1, 2, 3]);  // true
Array.isArray({foo: 123}); // false
Array.isArray('foobar');   // false
Array.isArray(undefined);  // false
```
* Използвайте оператора `spread` `...` или метода `slice()`, за да копирате масив.
```js
// грешно
const LENGTH = items.length;
let itemsCopy = [];
let i;

for (i = 0; i < LENGTH; i += 1) {
  itemsCopy[i] = items[i];
}

// правилно
let itemsCopy = [...items];

// правилно
let itemsCopy = items.slice();
```

#### <a name="expression">2.14. Изрази</a>
**Прости**
* Всеки ред трябва да съдържа най-много един израз.
* При бинарни изрази винаги трябва литерала да е от дясната страна.
```js
// грешно
let k = 10 + a;
  
// правилно
let k = a + 10;
```
* Трябва да се слага точка и запетая `;` на краят на всеки прост израз.
* Никога не разчитайте на ASI (Automatic Semicolon Insertion).
```js
// грешно
let greeting = 'Hello World'
  
alert(greeting)
  
// вярно
let greeting = 'Hello World';
  
alert(greeting);
```
**Сложни**  
Сложните изрази съдържат набор от изрази заградени от къдрави скоби `{}`.
* Изразите заобиколени от къдрави скоби `{}` трябва да започнат на нов ред.
* Изразите заобиколени от къдрави скоби `{}` трябва да бъдат по-навътре с **една индентация**.
```js
// грешно
if (condition === true) { alert('Passed!'); }
  
// вярно
if (condition === true) {
    alert('Passed!');
}
```
* Отварящата къдрава скоба `{` трябва да бъде на края на реда, на който започва сложният израз.
* Затварящата къдрава скоба `}` трябва да бъде на нов ред и да е подравнена с началото на реда, на който е отварящата къдрава скоба `{`.
```js
// грешно
if (condition === true)
{
    alert('Passed!');
}

// вярно
if (condition === true) {
    alert('Passed!');
}
```
* Къдрави скоби `{}` **трябва да се използват за всички сложни изрази**, дори и да са едноредови.
```js
// грешно
if (condition === true) alert('Passed!');
  
// грешно
if (condition === true)
    alert('Passed!');
  
// правилно
if (condition === true) {
    alert('Passed!');
}
```
Ако не оградите с {} сложните изрази, без да искате може да вкарате грешки в програмата.
```js
if (condition === true)
    alert('Passed!');
    return condition; 
```
Написаният код изглежда, че ще върне резултат, ако `condition === true`, но без къдрави скоби `{}` изразът, който връща 
резултат `return condition;` ще бъде изпълнен всеки път без значение от стойността на `condition`.
* Сложните изрази не трябва да завършват с точка и запетайка `;`. Единствено изключение към правилото е изразът `do { } while();`.
 
**Изрази на повече от един ред**

Когато се налага да се използват изрази включващи няколко части, когато редът стане прекалено дълъг се разделят на 
няколко реда, като операторите се поставят **в началото на новият ред**. Това позволява операторите да са подравнени
един под друг и ни помага за по-лесно проследяване.
```js
// грешно
let string = 'string part one' +
    'string part two' +
    'string part three';
  
// правилно
let string = 'string part one'
    + 'string part two'
    + 'string part three';
  
// грешно
let condition = 'condition one' ||
    'condition two' ||
    'condition three';
  
// правилно
let condition = 'condition one'
    || 'condition two'
    || 'condition three';
  
// грешно
let arr = array.
    map(smth).
    filter(smth).
    concat(smth)
  
// правилно
let arr = array
    .map(smth)
    .filter(smth)
    .concat(smth)
  
// Макар и да не е препоръчително да използвате тернарни оператори на няколко реда, понякога се налага.
// Те също следват този принцип
  
// грешно
condition ?
    <render template if conditon is true> :
    <render template if conditon is false>;
  
// правилно
condition
    ? <render template if conditon is true>
    : <render template if conditon is false>;
```

**Специфични конструкции**

`Short-circuit evaluation`

В javasctript конструкции от тип `condition && method();` са синтактично правилни и тъй като според спецификациите на езика
при изчисляване на резултатът от логическата операция `И (&&)` резултатът от този израз се определя в първият момент
в който някое от условията се евалюира до истина - тази конструкция се използва за кратко изписване на условен израз
```
if (condition) {
    method();
}
```
Конструкции от този тип са позволени единствено и само тогава, когато method() връща булева стойност и резултатът от този израз
се използва за присвояване на логическа променлива.
```
// грешно
hasInformation && doSomethingWithTheInformation(information);
  
// правилно
let isCorrect = !hasErrors && isInformationCorrect(information);
```

  
#### <a name="return">2.15. Връщане на стойност</a>
* Ако `return` израз има стойност, не трябва да се ползват кръгли скоби `()` за обграждане на стойността.
* Изразът на стойността, която връщаме трбява да започва на същият ред, на който е ключовата дума `return`.
```js
// грешно
return
    'Hello World!';

// грешно
return ('Hello World!');

// правилно
return 'Hello World!';
```
* Препоръчително е да вращате стойност възможно най-рано, когато е приложимо.
```js
// грешно
function getHighestNumber(a: number, b: number): number {
    let out = b;
  
    if (a >= b) {
        out = a;
    }
  
    return out;
}
  
// правилно
function getHighestNumber(a: number, b: number): number {
    if (a >= b) {
        return a;
    }
  
    return b;
}
```
#### <a name="if-statements">2.16. If изрази</a>
```
Понякога може просто да проверите дали една стойност е лъжа/истина, но общият подход е да бъдете изрични в това, какво точно проверявате.  
`if` изразите трябва да са в следната форма:
```js
if (/* condition */) {
    // ...
}
  
if (/* condition */) {
    // ...
} else {
    // ...
}
  
if (/* condition */) {
    // ...
} else if (/* condition */) {
    // ...
} else {
    // ...
}
```
* Вътре в условието не трябва да се извършва присвояване, а сравняване. Това води до по-четим код и намалява източниците на грешки.
```js
// грешно
if (a = b) {
    // ...
}
  
// правилно
if (a === b) {
    // ...
}
```
* Израза в тялото на условието винаги се огражда с къдрави/блок скоби `{}`.
```js
// грешно
if (a == b) return a;
if (a == b) { return a }
if (a == b)
    return a;
  
// правилно
if (a === b) {
    return a;
}
```ю
* **Препоръчително** Когато условието стане прекалено дълго и сложно е да бъде изнесено и разделено на логически групи.
```js
// грешно
if (this.state.logo === null && nextState.logo
    || !this.props.logo && nextProps.logo
    || this.state.imageSrc !== nextState.imageSrc
) {
    return true;
}

// правилно
let newLogoFromStateProvided = this.state.logo == null && nextState.logo;
let newLogoFromPropsProvided =  !this.props.logo && nextProps.logo;
let newImageProvided =  this.state.imageSrc !== nextState.imageSrc;

return newLogoFromStateProvided || newLogoFromPropsProvided || newImageProvided;
```
#### <a name="for-loops">2.17. For цикли</a>
* Стандартните for цикли са в следната форма:
```js
for (/* initialization */; /* condition */; /* update */) {
    // ...
}
  
for (let i = 0; i < length; ++i) {
    // ...
}
```
* `for...in` циклите обхождат изброимите ключове/свойства на един обект в реда на тяхното деклариране.
    * Задължително правете проверка `hasOwnProperty`, когато ползвате `for...in` цикъл, освен ако не е желано да обхождате и унаследени свойства.
    * `for...in` **не трябва** да се ползва за обхождането на масиви, където редът на индексите е важен. - Препоръка от MDN
```js
var triangle = {a: 1, b: 2, c: 3};

function ColoredTriangle() {
  this.color = 'red';
}

ColoredTriangle.prototype = triangle;

var obj = new ColoredTriangle();

for (var prop in obj) {
  if (obj.hasOwnProperty(prop)) {
    console.log(`obj.${prop} = ${obj[prop]}`);
  } 
}

// Output:
// "obj.color = red"
```
* `for...of` циклите обхождат обекти, които могат да се обходят (включително `Array`, `Map`, `Set`, `String`, `TypedArray`, `arguments` и т.н.)
```js
let iterable = [10, 20, 30];

for (let value of iterable) {
  value += 1;
  console.log(value);
}
// 11
// 21
// 31
```
#### <a name="do-while">2.18. While, Do ... while</a>
* `while` циклите трябва да изглеждат по следният начин:
```js
while (/* condition */) {
    // ...
}
```
* `do...while` изразите трябва да завършват с точка и запетая `;`.
```js
do {
      // ...
  } while (/* condition */);
```

#### <a name="switch">2.19. Switch...case</a>
* Всеки `case` трябва да е позициониран на нов ред с **една индентация** (2 интервала) навътре от `switch`.
* Винаги трябва да се излиза от `switch` конструкцията посредствум `break` или `return`, когато един случай има тяло. Изтърването на `break` или `return` обикновено е източник на бъгове.
```js
// грешно
switch(foo) {
    case 1:
        someFunc(foo);
    case 2:
        someOtherFunc(foo);
        break;
}
  
// правилно
switch(foo) {
    case 1:
    case 2:
        someOtherFunc(foo);
        break;
}
```
* Не се дублират случаи.
```js
switch (id) {
  case 1:
    // ... 
  case 1:     // ✗ грешно 
}
```
#### <a name="try-catch">2.20. Try...catch</a>
* **Препоръчително** Когато ползвате вградени функциналности или писани от нас, които „хвърлят“ грешки трябва да ги обградите с `try...catch` блок.
```js
// грешно
let storedJSON = 'undefined';
let parseJSON = JSON.parse(storedJSON);
  
// правилно
let storedJSON = 'undefined';
let parsedJSON = null;
  
try {
    parsedJSON = JSON.parse(storedJSON);
} catch (error) {
    // Обработка на грешката.
}
```
* Винаги когато хвърляте грешка ползвайте `Error` обекта, защото така се създават допълнителни данни - stack trace,
 които подпомагат отстраняването на проблема.
```js
// грешно
throw 'An error occurred!';
   
// правилно
throw new Error('An error occurred!');
```

### <a name="jQuery"> 3. jQuery</a>
*  Prefix jQuery object variables with a $
```js
// грешно
let sidebar = $('.sidebar');
  
// правилно
let $sidebar = $('.sidebar');
```
* Cache jQuery lookups.
```js
// Грешно
function setSidebar() {
  $('.sidebar').hide();
  
  // ...
  
  $('.sidebar').css({
    'background-color': 'pink',
  });
}
  
// Правилно
function setSidebar() {
  const $SIDEBAR = $('.sidebar');
  $SIDEBAR.hide();
  
  // ...
  
  $SIDEBAR.css({
    'background-color': 'pink',
  });
}
```
* For DOM queries use Cascading `$('.sidebar ul')` or parent > child `$('.sidebar > ul')`. [тест](https://jsperf.com/jquery-find-vs-context-sel/16)
```js
// грешно
$('ul', '.sidebar').hide();

// грешно
$('.sidebar').find('ul').hide();

// правилно
$('.sidebar ul').hide();

// правилно
$('.sidebar > ul').hide();

// правилно
$SIDEBAR.find('ul').hide();
```
### <a name="forbidden">4. Забранени неща</a>
* Забранена е употребата на `eval`, защото често такова място може да се ползва като вектор на атака от хакери.
* Забранено е да се публикува код, който съдържа `debugger;`, в **develop** и **master** клонове.
* Забранено е да се публикува код, който съдържа логове различни от `console.error`, в **develop** и **master** клонове.
* Забранени са коментари от вида на `/// <reference path=>`. Вместо тях използвайте **ES6 import-и**.

### <a name="good-to">5. Препоръчителни неща</a>
* Избягвайте писането на **Javascript** в **HTML** файлове
* Избягвайте писането на **стилове** и **markup** в **JS** файлове
* Избягвайте използването на **статични** ресурси в **JS** файлове
* Избягвайте или използвайте с повишено внимание **stop event propagation**.

#### <a name="destructuring">5.1. Деструктуриране (Destructuring)</a>
Деструктурирането ви спасява от създаването на временна референция за пропъртитата.
* Използвайте деструктурирането, когато достъпвате и използвате множество пропъртита на обект.
```js
// bad
function getFullName(user) {
  let firstName = user.firstName;
  let lastName = user.lastName;
  
  return `${firstName} ${lastName}`;
}
  
// good
function getFullName(user) {
  let { firstName, lastName } = user;
  return `${firstName} ${lastName}`;
}
  
// best
function getFullName({ firstName, lastName }) {
  return `${firstName} ${lastName}`;
}
```
* Използвайте деструктуриране на масиви.
```js
const ARR = [1, 2, 3, 4];
  
// bad
let first = ARR[0];
let second = ARR[1];
  
// good
let [first, second] = ARR;
```
* Използвайте деструктуриране на обекти за много върнати стойности, вместо на масиви.
```js
// bad
function processInput(input) {
      
  // then a miracle occurs
  return [left, right, top, bottom];
}
  
// the caller needs to think about the order of return data
let [left, __, top] = processInput(input);
  
// good
function processInput(input) {
      
  // then a miracle occurs
  return { left, right, top, bottom };
}
  
// the caller selects only the data they need
let { left, top } = processInput(input);
```

#### <a name="good-strings">5.2. Низове</a>
* Когато програмно изграждате низове, използвайте шаблони вместо конкатенация.
```js
// грешно
function sayHi(name) {
  return 'How are you, ' + name + '?';
}

// грешно
function sayHi(name) {
  return ['How are you, ', name, '?'].join();
}

// грешно
function sayHi(name) {
  return `How are you, ${ name }?`;
}

// правилно
function sayHi(name) {
  return `How are you, ${name}?`;
}
```
#### <a name="good-obects">5.3. Обекти </a>
* Използвайта кратко изписване на методите.
```js
// bad
const atom = {
  value: 1,

  addValue: function (value) {
    return atom.value + value;
  }
};

// правилно
const atom = {
  value: 1,

  addValue(value) {
    return atom.value + value;
  }
};
```
* Използвайта кратко изписване на стойностите на пропъртитата.
```js
const lukeSkywalker = 'Luke Skywalker';

// грешно
const obj = {
  lukeSkywalker: lukeSkywalker
};

// правилно
const obj = {
  lukeSkywalker
};
```
* Групирайте всички кратко изписвани пропъртита в началото на декларацията.
```js
const anakinSkywalker = 'Anakin Skywalker';
const lukeSkywalker = 'Luke Skywalker';

// грешно
const obj = {
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  lukeSkywalker,
  episodeThree: 3,
  mayTheFourth: 4,
  anakinSkywalker
};

// правилно
const obj = {
  lukeSkywalker,
  anakinSkywalker,
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  episodeThree: 3,
  mayTheFourth: 4
};
```
#### <a name="good-classes">5.4. Класове и конструктури</a>
* Винаги изполвайте класове. Избягвайте променянето и разширяването на прототипа директно.
Защо? Клас синтаксиса е много чист, кратък но и достатъчно описателен и ясен.
```js
// bad
function Queue(contents = []) {
  this.queue = [...contents];
}
Queue.prototype.pop = function () {
  const value = this.queue[0];
  this.queue.splice(0, 1);
  return value;
};

// good
class Queue {
  constructor(contents = []) {
    this.queue = [...contents];
  }
  pop() {
    const value = this.queue[0];
    this.queue.splice(0, 1);
    return value;
  }
}
```
* Използвайте extends за наследяване.
Защо? Вграден начин за наследяване на прототипната функционалност без чупене на instanceof.

```js
// bad
const inherits = require('inherits');
function PeekableQueue(contents) {
  Queue.apply(this, contents);
}
inherits(PeekableQueue, Queue);
PeekableQueue.prototype.peek = function () {
  return this.queue[0];
};

// good
class PeekableQueue extends Queue {
  peek() {
    return this.queue[0];
  }
}
```
* Няма проблем да напишете собствен toString() метод, но задължително се уверете, че работи правилно и не причинява странични ефекти.
```js
class Jedi {
  constructor(options = {}) {
    this.name = options.name || 'no name';
  }

  getName() {
    return this.name;
  }

  toString() {
    return `Jedi - ${this.getName()}`;
  }
}

```

* Класовете имат конструктор по подразбиране. Празен конструктор, или такъв, който само извиква родителският, са ненужни. eslint: no-useless-constructor
```js
// bad
class Jedi {
  constructor() {}

  getName() {
    return this.name;
  }
}

// bad
class Rey extends Jedi {
  constructor(...args) {
    super(...args);
  }
}

// good
class Rey extends Jedi {
  constructor(...args) {
    super(...args);
    this.name = 'Rey';
  }
}
```
