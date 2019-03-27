[Назад](../README.md)

# TypeScript coding standard

-------

[**Назад**](../README.md)

## <a name="table-of-contents">Съдържание</a>
   1. [Въведение](#intro) 
   1. [Форматиране](#formatting)
      1. [Файлове](#files)
      1. [Отстояния](#spacing)
      1. [Дължина на реда](#line-length)
      1. [Кавички](#quotes)
      1. [Коментари](#comments)
      1. [Декларация на променливи](#variable-declaration)
      1. [Функции](#functions)
      1. [Именуване](#naming-convention)
      1. [Типове](#types)
      1. [Класове](#classes)
      1. [Интерфейси](#interfaces)
      1. [Изрази](#statements)
      1. [Връщане на стойност](#return)
      1. [If изрази](#if)
      1. [For цикли](#for)
      1. [While цикли](#while)
      1. [Do while цикли](#do-while)
      1. [Switch...case](#switch)
      1. [Promise](#promise)
      1. [Try...catch](#try-catch)
      1. [Забранени неща](#forbidden)

## <a name="intro">1. Въведение</a>
Този документ има за цел да наложи базовите правила и да представи добрите практики за 
писане/управляване на **TypeScript** код. При използването на конвенция за писане на код в
целият проект, прави кодът по-лесно четим и по-разбираем за останалите хора в екипа. По този начин
повишаваме производителността на екипа.

[**Нагоре**](#table-of-contents)

## <a name="formatting">2. Форматиране</a>
Следенето на правилата описани по-долу се осъществява от човека правещ код ревюта и от [TSLint](https://palantir.github.io/tslint/).
Файлът с настройки на линтъра може да намерите [**тук**](./tslint.json).

### <a name="files">2.1 Файлове</a>
 * Всички TypeScript файлове трябва да завършваш с разширение `.ts`,
   а ако се ползва JSX Harmony стандарта (React проект) e валидно също така и `.tsx` разширението.
 * Файловете трябва да са с **UTF-8** кодиране, заради съвместимостта му с различни азбуки.
 * За край на реда трябва да се ползва UNIX стил - символ `LF (\n)`. 
 * Имената на файловете трябва да **съдържат единствено:** малки букви, числа, точки и тирета.
 * Думите в имената трябва да се отделят с тирета `-`, а смисловият тип с точки `.` . Примери:
    - `profile-settings.view.ts` - вярно
    - `profileSettings-view.ts` - грешно
    - `http.service.ts` - вярно
    - `httpService.ts` - грешно
    
[**Нагоре**](#table-of-contents)

### <a name="spacing">2.2 Отстояния</a>
  * Едно стандартно странично отстояние трябва да е 4 интервала.
  * **Никога не използвайте табове**, това може да доведе до нееднороден изглед в различните среди/редактори. 
    Повечето редактори имат настройка да обръщат табовете в интервали.
  * Винаги слагайте интервал след ключови думи.
 
    ```typescript
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
  
    ```typescript
    // грешно
    let x=2;
    let message = 'hello, '+name+'!';
     
    // правилно
    let x = 2;
    let message = 'hello, ' + name + '!';
    ```
    
    
  * Запетайките `,` трябва да имат разстояние след тях.
    
    ```typescript
    // грешно
    let list: number[] = [1,2,3,4];
    function greet (name: string,options: {[key: string]: any}): void { ... }
     
    // правилно
    let list: number[] = [1, 2, 3, 4];
    function greet (name: string, options: {[key: string]: any}): void { ... }
    ```
    
    
  * Отстояният при импортите трябва да са в следният формат:
  
    ```typescript
    import { Something } from 'somewhere';
    import * as Somewhere from 'somewhere';
    ```
    
  * При повече от 2 импорта трябва да се подредят по следният начин:
  
    ```typescript
    import { 
        Something,
        Something2,
        Something3
    } from 'somewhere';
    ```
  
 
[**Нагоре**](#table-of-contents)
  
### <a name="line-length">2.3 Дължина на реда</a>
  * Един ред не трябва да бъде по-дълъг от 120 символа.
  * Когато един израз надхвърли лимитът от 120 символа, трябва да бъде разделен. 
    За предпочитане това да стане след запетайка или оператор.
 
[**Нагоре**](#table-of-contents)
 
### <a name="quotes">2.4 Кавички</a>

  * Използват се единични кавички `''` за всички низове, а двойни кавички `""` се използват само за низове в низовете.
  * Ударени кавички се ползват само и единствено когато имаме ES6 низ с шаблон в него.
  * Не трябва да се оставят разстояния между променливите изписани в низа с шаблона и къдравите скоби които го маркират.
 
```typescript
    // грешно
    let greeting = "Hello World!";
    
    // правилно
    let greeting = 'Hello World!';
    
    // грешно
    let greeting = `Hello World!`;
    
    // грешно
    let name = 'Pesho';
    let greeting = `Hello, ${ name }!`;
    
    // правилно
    let name = 'Pesho';
    let greeting = `Hello, ${name}!`;
    
    // грешно
    let html = "<div class='bold'>Hello World</div>";
    
    // грешно
    let html = '<div class=\'bold\'>Hello World</div>';
    
    // правилно
    let html = '<div class="bold">Hello World</div>';
```

[**Нагоре**](#table-of-contents)

### <a name="comments">2.5 Коментари</a>
  * Писането на коментари в кода е силно препоръчително. То помага за повишаването на четимостта на вашият код.
  * Коментарите трябва да бъдат ясни, точно като кодът, който описват.
  * Коментарите трябва да бъдат на английски език.
  * Коментарите трябва да бъдат смислени.
 
     Неправомерно използване на коментар:
    ```typescript
    // Set index to zero.
    let index = 0;
    ```
    

  * Всички методи и функции трябва да имат [JSDoc](http://usejsdoc.org/) документация
 
    JSDoc може да бъде разчетена от средите за разработка за по-добри подсказки. Примерна документация:
    
    ```typescript
     /**
      * Takes in a name and returns a greeting string.
      *
      * @param {string} name - The name of the greeted person.
      * @returns {string} - Greeting string. 
      */
     function getGreeting(name: string): string {
         return 'Hello ' + name + '!';
     }
    ```
    
    #### Клас
     - Всички класове трябва да имат [JSDoc](http://usejsdoc.org/) документация за всички член данни и методи.
     - Методите трябва да имат коментар описващ какво прави метода, а всички параметри на метода трябва 
       да бъдат отбелязани с `@param {<тип>} <име>`. Ако един метод връща резултат, то това трябва да бъде описано
       чрез `@returns`.
    
    ```typescript
    /**
     * Contains properties of a Person.
     */
    class Person {
        /**
         * Returns a new Person with the specified name.
         *
         * @param {string} name - The name of the new Person.
         * @returns {Person} 
         */
        static GetPerson(name: string): Person {
            return new Person(name);
        }
        
        /**
         * @param {string} name - The name of the new Person.
         */
        constructor(public name: string) { }
        
        /**
         * Instructs this Person to walk for a certain amount
         * of time.
         *
         * @param {number} millis - The number of milliseconds the Person
         * should walk.
         */
        public walkFor(millis: number): void {
            console.log(this.name + ' is now walking.');
    
            setTimeout(() => {
                console.log(this.name + ' has stopped walking.');
            }, millis);
        }
    }
    ```
    
    #### Вътрешни
    - Вътрешните коментари се използват вътре в сложни изрази (цикли, функции и т.н.).
    - Използвайте `//` за всички вътрешни коментари.
    - Започвайте коментарът с един интервал в началото. - `// Comment`
    - Коментарите трябва да бъдат кратки и ясни.
    - Сложете вътрешните коментари на нов ред над реда, който поясняват.
    - Сложете празен ред над коментара.
    ```typescript
    // грешно
    let lines: string[]; // Holds all the lines in the file.
       
    // правилно
    // Holds all the lines in the file.
    let lines: string[];
      
    // грешно
    function walkFor(name: string, millis: number): void {
        console.log(name + ' is now walking.');
        // Wait for millis milliseconds to stop walking
        setTimeout(() => {
            console.log(name + ' has stopped walking.');
        }, millis);
    }
      
    // правилно
    function walkFor(name: string, millis: number): void {
        console.log(name + ' is now walking.');
        
        // Wait for millis milliseconds to stop walking
        setTimeout(() => {
            console.log(name + ' has stopped walking.');
        }, millis);
    }
    ```
    
    #### TODO и XXX
    Подсказки като `TODO` и `XXX`, могат да ви помогнат да намерите неща които трябва да бъдат добавени/отстранени.
    - Използвайте `// TODO: ` за да отбележете функционалности, които трябва да се добавят.
    - Използвайте `// XXX: ` за да отбележете проблеми, които трябва да се отстранят.
    - Старайте се да пишете код, който не изисква писането на `TODO:` и `XXX:`, но за съжаление това
      не винаги е възможно.
      
[**Нагоре**](#table-of-contents)
    
### <a name="variable-declaration">2.6 Декларация на променливи</a>
  * Всички променливи трябва да бъдат декларирани преди да бъдат използвани.
  
      ```typescript
      // грешно
      console.log(a + b);
      
      let a = 2;
      let b = 4;
       
       
      // правилно
      let a = 2;
      let b = 4;
      
      console.log(a + b);
      ```
      
      
  * Глобални променливи, декларирани без `var`, `let` или `const` не трябва да се ползват.
  * Не трябва да се декларират променливи с едни и същи имена в един и същи обхват `scope`.
  * Не трябва да се създават глобални променливи от места с не глобален обхват.
    ```typescript
    // Грешно
    function add(a: number, b: number): number {
        // „c“ става глобална променлива
        c = 6;
    
        return a + b + c;
    }
    ```
    
    
  * Когато декларирате множество от променливи всеки път използвайте ключовите думи `var`, `let` и `const`.
    По този начин лесно се добавят нови променливи и/или им се сменя реда на декларация.
    ```typescript
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
    
    
  * Десетичните числа в интервалът (-1, 1) трябва да започват `0` т.е. `0.5` вместо `.5`.
  * **Не трябва** да се ползват конструкторите на `String`, `Number` и `Boolean`. Използването им води до създаване
    на обект който съдържа в себе си една от тези примитиви, което носи със себе си други странични ефекти.
    
    ```typescript
    // При използване тройно равенство:
    new Boolean("true") === true; // false
    Boolean("true") === true; // true
     
    // Така се създават обекти вместо примитиви.
    typeof new Boolean("true"); // "object"
    typeof Boolean("true"); // "boolean"
    ```
    
    
  * Всяка декларирана променлива или константа трябва да бъде използвана някъде иначе няма смисъл от нея.
  * За да се провери дали дадена променлива е `NaN` трябва да се ползва функцията `isNaN`, защото `NaN !== NaN`.
  
    ```typescript
    // грешно
    a === NaN
     
    // правилно
    isNaN(a)
    ```
    
    
  * При сравняване използвайте `===` и `!==`. Разрешена е употребата на `==` и `!=` само когато сравнявате с `null`.
    
**Употреба на `var`, `let` и `const`**
  * Използвайте `const`, когато трябва да декларирате константи, чиито стойности няма да се променят.
  * Използвайте `let` във всички останали случаи.
  * Избягвайте употребата на `var`.
    
[**Нагоре**](#table-of-contents)
    
### <a name="functions">2.7 Функции</a>
#### Декларация на функции
  * Всички функции трябва да бъдат декларирани преди да бъдат използвани.
  
    ```typescript
    // грешно
    function createGreeting(name: string): string {
        let message = 'Hello ';
        
        return greet;
        
        function greet(): string {
            return message + name + '!';
        }
    }
      
    // правилно
    function createGreeting(name: string): string {
        let message = 'Hello ';
        
        function greet(): string {
            return message + name + '!';
        }
       
        return greet;
    }
    ```
    
     
  * Не трябва да има интервал между името на фунцията и отварящата скоба на параметрите `(`.
  * Трябва да има един интервал между затварящата скоба на параметрите `)` и отварящата къдрава скоба `{`.
   
    ```typescript
    // грешно
    function foo (){
        // ...
    }
     
    // правилно
    function foo() {
        // ...
    }
    ```
    
    
  * Тялото на функцията трябва да е по-навътре с 4 интервала.
  * Затварящата къдрава скоба `}` трябва да бъде на нов ред и да е подравнена с редът,
    на който е отварящата къдрава скоба `{`.
    
    ```typescript
    // грешно
    function foo(): string {
      return 'foo';}
     
    // правилно
    function foo(): string {
        return 'foo';
    }
    ```
    
    
  * За всеки параметър на фунция:
    - Трябва да няма разстояние между името на параметъра и двуеточието `:` отбелязващо декларацията на типа.
    - Трябва да има разстояние между двуеточието `:` и декларацията на типа.
    - Същите правила се прилагат аналогично за типа, който връща функцията.
     
    ```typescript
    // грешно
    function greet(name:string):void {
      // ...
    }
     
    // правилно
    function greet(name: string): void {
      // ...
    }
    ```
    
    
  * Всяка функция или метод трябва да са означени какъв тип данни връщат и този тип трябва да е коректен.
  
    ```typescript
    // грешно
    function greet(name:string) {
      return `Hello, ${name}!`;
    }
     
    // грешно
    function greet(name:string): void {
      return `Hello, ${name}!`;
    }
     
    // правилно
    function greet(name: string): string {
      return `Hello, ${name}!`;
    }
    ```
    
  
  * Не трябва вътрешните променливи да „засенчват“ параметрите.
  
    ```typescript
    // грешно
    function foo(bar: string): void {
        let bar: string = bar || 'Hi';
    }
     
    // правилно
    function foo(bar: string): void {
        let barParsed: string = bar || 'Hi';
    }
    ```
    
    
#### Анонимни функции
  * Всички анонимни функции трябва да бъдат дефинирани като ламбди `() => { }`, освен ако
    не е абсолютно необходимо да се запази оригиналният контекст в тялото на функцията.
  * Всички ламбда изрази трябва да имат скоби `()` около параметрите си.
  
    ```typescript
    // грешно
    let k => k * 2;
     
    // правилно
    let (k) => k * 2;
     
    // грешно
    public clickAlert(): void {
        let element = document.querySelector('div');
    
        this.foo = 'foo';
    
        element.addEventListener('click', function(ev: Event) {
            // „this.foo“ не съществува!
            alert(this.foo);
        });
    }
     
    // правилно
    public clickAlert(): void {
        let element = document.querySelector('div');
    
        this.foo = 'foo';
    
        element.addEventListener('click', (ev: Event) => {
            // TypeScript предава правилният конекст и така „this.foo“ съществува! | (.bind(this))
            alert(this.foo);
        });
    }
    ```
    
    
  * Трябва да има един интервал между затварящата скоба `)` и `=>`.
  * Трябва да има един интервал между `=>` и отварящата къдрава скоба `{` която се явява отварящ блок оператор.
    
    ```typescript
    // грешно
    element.addEventListener('click', (ev: Event)=>{alert('foo');});
     
    // правилно
    element.addEventListener('click', (ev: Event) => {
        alert('foo');
    });
    ```
  
  * Тялото на израза трябва да е с отстояние 4 интервала спрямо предходният ред.
  * Затварящият блок оператор `}` трябва да бъде поставен на нов ред.
  * Затварящият блок оператор `}` трябва да бъде подравнен с редът на който е поставен отварящият
    блок оператор `{`.    
    
[**Нагоре**](#table-of-contents)


### <a name="naming-convention">2.8 Именуване</a>
  * Всички имена на променливи и на функции трябва да съдържат само символите: `A-Z, a-z, 0-9` и долна черта `_`.  
  * Променливите, модулите и функциите трябва да се кръщават чрез `camelCase`.
  * Константите трябва да се именуват чрез `UPPER_UNDERSCORE_CASE` и задължително да се декларират с `const`.
  * При именуване на булева `boolean` променлива трябва задължително името да започва с `is`, `has` или `was`. 

[**Нагоре**](#table-of-contents)

### <a name="types">2.9 Типове</a>
  * Винаги упоменавайте от какъв тип са ви променливите, константите и функциите.
  * Винаги упоменавйте какъв е типа на данните връщан от фунциите.
  * Не използвайте `any` често, а дефинирайте интерфейси. 
  * Масивите трябва да бъдат означавани с `type[]` вместо `Array<type>`.
    - Не трябва да съществуват дупчести (sparse) масиви.
    
    ```typescript
    // грешно
    let numbers: number[] = [1, , 3, 4];
    console.log(numbers.length); // 4
     
    // правилно
    let numbers: number[] = [1, 3, 4];
    console.log(numbers.length); // 3
    ```


[**Нагоре**](#table-of-contents)

### <a name="classes">2.10 Класове</a>
  * Класовете трябва да се кръщават използвайки `PascalCase`.
  * При създаване на нова инстанция на клас винаги трябва да се пишат скобите `()` в края на конструктура.
  
    ```typescript
    // грешно
    let person = new Person;
     
    // правилно
    let person = new Person();
    ```
    
  
  * Модификаторите за достъп - `private`, `public`, `static`, `protected` трябва да се използват за означаване
    на достъпа до член данни и методи.
  * Трябва в един файл да съществува само един клас. По този начин се спазва правилото
    за разделяне на отговорностите при файловете.
  * `this` трябва да се ползва само в класове. 
  
    ```typescript
    // Случва се да се изнесе част от функционалността от метод във функция.
    class Foo {
        private aMethod(): void {
            doWorkOn(this.someState.x);
        }
    }
     
    // грешно
    function someFunction(someState): void {
        doWorkOn(this.someState.x); // Забележете „this“
    }

    // правилно
    function someFunction(someState): void {
        doWorkOn(someState.x);
    }
    ```
  
  
  * Когато се декларират методи трябва да се описват така: `foo(): void`, а не `foo: () => void`.
  * При унаследяване на друг клас първото нещо, което трябва да се направи в конструктура е да се
    извика родителският такъв чрез `super(...);`.
  * Трябва да се спазва следната подредба за описване на клас:
    - Статични данни
    - Член данни
    - Конструктор
    - Статични методи
    - Публични методи
    - Защитени `protected` методи
    - Лични `private` методи

[**Нагоре**](#table-of-contents)


### <a name="interfaces">2.11 Интерфейси</a>
  * Трябва да се наименуват чрез `PascalCase`
  * Винаги започвайте името на един интерфей с главно `I`, за да
    се отличават от класовете по-лесно.
  * Не трябва да съществуват празни интерфейси.
  * Интерфейсите нямат `constructor` и не могат да се ползва `new` оператор с тях.
  * Когато се декларират методи трябва да се описват така: `foo(): void`, а не `foo: () => void`.
  * Само `public` членове трябва да са описани в един интерфейс.
   
    ```typescript
    interface IPerson {
        firstName: string;
        lastName: string;
        toString(): string;
    }
    ```
  

[**Нагоре**](#table-of-contents)


### <a name="statements">2.12 Изрази</a>
#### Прости
  * Всеки ред трябва да съдържа най-много един израз.
  * При бинарни изрази винаги трябва литерала да е от дясната страна.
  
    ```typescript
    // грешно
    let k = 10 + a;
     
    // правилно
    let k = a + 10;
    ```
  
  
  * Трябва да се слага точка и запетая `;` на краят на всеки прост израз.
  * Никога не разчитайте на ASI (Automatic Semicolon Insertion).
  
    ```typescript
    // грешно
    let greeting = 'Hello World'
    
    alert(greeting)
     
    // вярно
    let greeting = 'Hello World';
    
    alert(greeting);
    ```
    
    
#### Сложни
Сложните изрази съдържат набор от изрази заградени от къдрави скоби `{}`.
  * Изразите заобиколени от къдрави скоби `{}` трябва да започнат на нов ред.
  * Изразите заобиколени от къдрави скоби `{}` трябва да бъдат по-навътре с 4 интервала.
  
    ```typescript
    // грешно
    if (condition === true) { alert('Passed!'); }
     
    // вярно
    if (condition === true) {
        alert('Passed!');
    }
    ```
    
    
  * Отварящата къдрава скоба `{` трябва да бъде на края на реда, на който започва сложният израз.
  * Затварящата къдрава скоба `}` трябва да бъде на нов ред и да е подравнена с началото на реда,
    на който е отварящата къдрава скоба `{`.
      
    ```typescript
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
    
    
  * **Къдрави скоби `{}` трябва да се използват за всички сложни изрази,** дори и да са едноредови.
    
    ```typescript
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
    
    Ако не оградите с `{}` сложните изрази, без да искате може да вкарате грешки в програмата.
    
    ```typescript
    if (condition === true)
        alert('Passed!');
        return condition; 
    ```
    
    Написаният код изглежда, че ще върне резултат, ако `condition === true`, но без къдрави скоби `{}`
    изразът, който връща резултат `return condition;` ще бъде изпълнен всеки път 
    без значение от стойността на `condition`.
    
  * Сложните изрази не трябва да завършват с точка и запетайка `;`. Единствено изключение към правилото е
    изразът `do { } while();`.


[**Нагоре**](#table-of-contents)


### <a name="return">2.13 Връщане на стойност</a>
  * Ако `return` израз има стойност, не трябва да се ползват кръгли скоби `()` за обграждане на стойността.
  * Изразът на стойността, която връщаме трбява да започва на същият ред, на който е ключовата дума `return`.
    
    ```typescript
    // грешно
    return
        'Hello World!';
     
    // грешно
    return ('Hello World!');
     
    // правилно
    return 'Hello World!';
    ```
    
  
  * Препоръчително е да вращате стойност възможно най-рано, когато е приложимо.
    
    ```typescript
    // грешно
    function getHighestNumber(a: number, b: number): number {
        let out = b;
     
        if(a >= b) {
            out = a;
        }
     
        return out;
    }
     
    // правилно
    function getHighestNumber(a: number, b: number): number {
        if(a >= b) {
            return a;
        }
     
        return b;
    }
    ```
    
    
  * Винаги дефинирайте какъв тип данни връщат функциите/методите. Това подпомага работата на TypeScript да провери
    дали винаги връщате коректният тип данни.
    
    ```typescript
    // грешно
    function getPerson(name: string) {
        return new Person(name);
    }
     
    // правилно
    function getPerson(name: string): Person {
        return new Person(name);
    }
    ```
  
[**Нагоре**](#table-of-contents)


### <a name="if">2.14 If изрази</a>
  * Винаги бъдете изрични във вашите `if` изрази.
    
    ```typescript
    // грешно
    function isString(str: any) {
        return !!str;
    }
     
    // правилно
    function isString(str: any) {
        return typeof str === 'string';
    }
    ```
    
    Понякога може просто да проверите дали една стойност е лъжа/истина, но общият подход е да бъдете изрични
    в това, какво точно проверявате.
    
    `if` изразите трябва да са в следната форма:
    
    ```typescript
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
    
    
  * При сравняване използвайте `===` и `!==`. Разрешена е употребата на `==` и `!=` само когато сравнявате с `null`.    
  * Вътре в условието не трябва да се извършва присвояване, а сравняване. Това води до по-четим код
    и намалява източниците на грешки.
    
    ```typescript
    // грешно
    if (a = b) {
        // ...
    }
     
    // правилно
    if (a === b) {
        // ...
    }
    ```
    

[**Нагоре**](#table-of-contents)

### <a name="for">2.15 For цикли</a>
  * Стандартните `for` цикли са в следната форма:
    
    ```typescript
    for (/* initialization */; /* condition */; /* update */) {
        // ...
    }
     
    for (let i = 0; i < length; ++i) {
        // ...
    }
    ```
    
    
  * `for...in` циклите обхождат изброимите ключове/свойства на един обект в реда на тяхното деклариране.
    - Задължително правете проверка `hasOwnProperty`, когато ползвате `for...in` цикъл, освен ако не е желано
      да обхождате и унаследени свойства.
    - `for...in` **не трябва** да се ползва за обхождането на масиви, където редът на индексите е важен. - [Препоръка от MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in)
  
    ```typescript
    class Human {
        constructor() {}
    }
     
    class Knight extends Human {
        constructor(
            public name: string,
            public age: number,
            public strength: number
        ) {
             super();
        }
    }
     
    let ivan = new Knight('Ivan', 20, 100);
     
    // грешно
    for (let key in ivan) {
        console.log('All: ', key);   
    }
     
    // правилно
    for (let key in ivan) {
        if (ivan.hasOwnProperty(key)) {
            console.log('Own: ', key);
        }
    }
     
    // All:  name
    // All:  age
    // All:  strength
    // All:  constructor
     
    // Own:  name
    // Own:  age
    // Own:  strength
    ```
    
    
  * `for...of` циклите обхождат обекти, [които могат да се обходят](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#iterable) 
  (включително [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array), [`Map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map), [`Set`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set), [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), [`TypedArray`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray), [`arguments`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/arguments) и т.н.)
  
    ```typescript
    let iterable: number[] = [10, 20, 30];
     
    for (let value: number of iterable) {
      value += 1;
      console.log(value);
    }
    // 11
    // 21
    // 31
    ```

[**Нагоре**](#table-of-contents)


### <a name="while">2.16 While цикли</a>
  * `while` циклите трябва да изглеждат по следният начин:
  
    ```typescript
    while (/* condition */) {
        // ...
    }
    ```


[**Нагоре**](#table-of-contents)


### <a name="do-while">2.17 Do while цикли</a>
  * `do...while` изразите трябва да завършват с точка и запетая `;`.
  
    ```typescript
    do {
        // ...
    } while (/* condition */);
    ```
    

[**Нагоре**](#table-of-contents)


### <a name="switch">2.18 Switch...case</a>
  * Винаги трябва да се пише `break;`, когато един случай има тяло. Изтърването на `break;`
    обикновено е източник на бъгове.
  
    ```typescript
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

[**Нагоре**](#table-of-contents)


### <a name="promise">2.19 Promise</a>
  * Всички `Promise`-и трябва да бъдат обработени.
  
    ```typescript
    // грешно
    Http.get('http://example.com');
     
    // грешно
    Http.get('http://example.com').then((response) => {
        // ...
    });
     
    // правилно
    Http.get('http://example.com').then((response) => {
        // ...
    }).catch((error) => {
        // Обработка на грешката.
    });
    ```
    
    
[**Нагоре**](#table-of-contents)


### <a name="try-catch">2.20 Try...catch</a>
  * Винаги когато ползвате вградени функциналности или писани от нас, които „хвърлят“ грешки 
    трябва да ги обградите с `try...catch` блок.
    
    ```typescript
    // грешно
    const storedJSON: string = 'undefined';
    let parseJSON = JSON.parse(storedJSON);
     
    // правилно
    const storedJSON: string = 'undefined';
    let parsedJSON: {[key: string]: any} = null;

    try {
        parsedJSON = JSON.parse(storedJSON);
    } catch (error) {
        // Обработка на грешката.
    }
    ```
    
    
  * Винаги когато хвърляте грешка ползвайте [`Error`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error) обекта, защото така се създават допълнителни данни - stack trace,
    които подпомагат отстраняването на проблема.
    
    ```typescript
    // грешно
    throw 'An error occurred!';
     
    // правилно
    throw new Error('An error occurred!');
    ```

[**Нагоре**](#table-of-contents)


### <a name="forbidden">2.21 Забранени неща</a>
  * Забранена е употребата на `eval`, защото често такова място може да се ползва като вектор на атака от хакери.
  * Забранено е да се публикува код, който съдържа `debugger;`, в `develop` и `master` клонове.
  * Забранено е да се публикува код, който съдържа логове **различни от** `console.error`, в `develop` и `master` клонове.
  * Забранени са коментари от вида на `/// <reference path=>`. Вместо тях използвайте ES6 `import`-и.

[**Нагоре**](#table-of-contents)
