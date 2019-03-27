[Назад](README.md)

1. [Въведение](#introduction)
2. [Синтаксис](#syntax)
3. [Наименоване](#naming)
4. [Коментари](#coments)
5. [Поставяна на Media query](#media-query)
6. [Ред на декларация](#declaration)
7. [Всички property-та](#all-properties)
8. [Влагане в Less и Sass](#nesting)
9. [CSS Modules](#css-modules)
10. [Stylelint](#stylelint)

### <a name="introduction">1. Въведение</a>
Този документ има за цел да наложи базовите правила и представи добрите практики при разработване на CSS стилове. 
Стриктното спазване на посочените по-долу правила  и добри практики ще спомогне в настоящата и бъдеща работа на 
development екипа. Документа е отправна точка при правенето на Code Review. 

### <a name="syntax">2. Синтаксис</a>
* Индентирането се усъществява с 2 интервала, от тук натаък наричани **една индентация**
* Празен ред между дефинициите на стилове
```css
.some-class {
    color: red;
}
  
.another-class { 
    color: blue; 
}
```
* Selector-а се изписва на един ред
* Всеки selector се изписва на нов ред    

Грешно:  
```css
.selector, .selector-secondary, .selector[type=text] {
    padding: 15px;
    margin-bottom: 15px;
}
```
Правилно:
```css
.selector,
.selector-secondary,
.selector[type="text"] {
    padding: 15px;
    margin-bottom: 15px;
}
```
* Всеки вложен selector се изписва с една индентация навътре
* Всяко property е на нов ред с една индентация навътре
* За разделяне на property-то от неговата стойност се поставя един интервал след : при всяка декларация 
```css
.class { 
    property: value;
}
```
* Къдвари скоби  
    - Отварящата скоба трябва да е на същия ред с един интервал след последния selector
    - Затварящата скоба трябва да е на нов ред на същото нивото на selector-а
```css
.class-name { 
    color: green;
    font-size: 16px;
}
```
* Всяко property (включително последното) завършва с точка и запетая ";"
* За разделител се използва запетая интервал ", " (и за selector и за property)
* Специфичните за браузъра property-та се изписват първи 
```css
#selector-1 a {
    -moz-box-shadow: 0 3px 3px rgba(0, 0, 0, 0.2); /* специфично за браузъра */
    -webkit-box-shadow: 0 3px 3px rgba(0, 0, 0, 0.2); /* специфично за браузъра */
    box-shadow: 0 3px 3px rgba(0, 0, 0, 0.2); /* официално property */
}
```

При изписване на много селектори с едно пропърти е допустимо изписването на един ред за по-голяма четимост 
```css
#selector-1 a.class-1 { background-position: 20px 10px; }
#selector-1 a.class-2 { background-position: 20px 10px; } 
#selector-1 a.class-3 { background-position: 20px 20px; }
#selector-1 a.class-4 { background-position: 20px 30px; }
#selector-1 a.class-5 { background-position: 20px 40px; }
#selector-1 a.class-6 { background-position: 20px 50px; }
#selector-1 a.class-7 { background-position: 20px 60px; }
#selector-1 a.class-8 { background-position: 20px 70px; }
```

### <a name="naming">3. Наименоване</a>
Class names
* Класовете се изписват с малки букви
* За разделител се използва тире "-" (не долна черта или camelCase).
* Не се ползват числа в началото на id или class
* Класовете се изписват възможно най-кратко и сбито, но се избягва произволно кратко изписване на класовете.
`.btn` е полезно съкращение за button, но `.s` не означава нищо.
* Използват се смислени имена  
Грешно:
```css
.t { ... }
 
.red_button { ... }  
 
.firstHeader { ... }
```
Правилно:
```css
.tweet { ... }
 
.important { ... }
 
.tweet-header { ... }
```

* Използват се класове вместо тага на елемента за постигане на максимално точно изпълнение
* Селекторите трябва да са къси и по възможност броя на селекторите за елемент да е ограничен до 3

```css
/* Bad example */
span { ... }
 
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
 
.avatar { ... }

/* Good example */
.avatar { ... }
 
.tweet-header .username { ... }
 
.tweet .avatar { ... }
```

### <a name="coments">4. Коментари</a>
Кодът, трябва да е описателен, добре коментиран и достъпен за другите.
Добрите коментари описват контекста или целта на кода. Не се повтаря просто името на класа.  
Грешно:
```css
/* Modal header */
.modal-header {
  ...
}
```
Правилно:
```css
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

### <a name="media-query">5. Поставяна на Media query</a>
Media query-то се поставя възможно най-близо до елементите, за които се отнася. Не се обединяват в едно media query в 
края на документа или в отделен такъв, по този начин става възможно тяхното пропускане.

```css
.element { ... }
 
.element-avatar { ... }
 
.element-selected { ... }
 
@media (min-width: 480px) {
    .element { ...}
  
    .element-avatar { ... }
  
    .element-selected { ... }
}
```

### <a name="declaration">6. Ред на декларация</a>
Взаимносвързаните property-та трябва да са групирани заедно в следния ред:

- Позиционни (Positioning)
- Бокс модел (Box model)
- Типографски (Typographic)
- Визуални (Visual)

Позиционирането е първо, защото може да изкара елемента от нормалното му поведение в документа и да пренапише стилове 
свързани с "Бокс модела". "Бокс моделът" се дефинира след това, тъй като обособява разположението и размерите на елемента.
Останалите два вида property-та не оказват влияние върху горните, затова остават последни. 

```css
.declaration-order {
    /* Positioning */
    position: absolute; /* Позициониране - static / relative / absolute / fixed */
    top: 0; /* Позициониране - размери - % / px */
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100; /* Позициониране - Z-index - стойност */
    
    /* Box-model */
    display: block; /* Показване - none / block / inline / inline-block */
    visibility: visible; /* Показване - visible / hidden */
    float: right; /* Изместване - none / left / right  */ 
    width: 100px; /* Размери - широчина - % / px - както и минимална и максимална ширина */
    height: 100px; /* Размери - височина - % / px - както и минимална и максимална височина */
    line-height: 1.5; /* Размери - височина на линията - px */
    overflow: visible; /* Размери - препълване - visible / hidden / scroll / auto */
    margin: 0; /* Избутване - отвън - (top, right, bottom, left) в px */
    padding: 0; /* Избутване - отвътре - (top, right, bottom, left) в px */

    /* Typography */
    color: #333; /* Цвят - RGB hex - кратко #FFF или #FFFFFF пълно*/
    /* Шрфит - всичко за шрифта - font / font-family / font-size / font-style / font-variant / font-weight /
    @font-face / font-size-adjust / font-stretch */
    font: normal 13px "Helvetica Neue", sans-serif;
    /* Текст - всичко за текста - text-align / text-decoration / text-indent / text-justify / text-outline / 
    text-overflow / text-shadow / text-transform / text-wrap */
    text-align: center; 
    direction: ltr; /* Посока на съдържанието - ltr / rtl */
    letter-spacing: normal; /* Големина разстоянието между символите - px */
    white-space: normal; /* - normal / nowrap / pre */
    word-spacing: normal; /* Големина на интервала между думите - px */
    list-style-type: disc; /* Списъци */
    clear: both; /* Изчистване - на изместените елементи */
    cursor: auto; /* Курсор */
    
    /* Visual */
    background-color: #f5f5f5;
    border: 1px solid #e5e5e5;
    border-radius: 3px;
    opacity: 1;
}
```

### <a name="all-properties">7. Всички property-та</a>
```html
selector {
    /* по азбучен ред */
    animation: ; /* CSS 3 */
    animation-name: ; /* CSS 3 */
    animation-duration: ; /* CSS 3 */
    animation-timing-function: ; /* CSS 3 */
    animation-delay: ; /* CSS 3 */
    animation-iteration-count: ; /* CSS 3 */
    animation-direction: ; /* CSS 3 */
    animation-play-state: ; /* CSS 3 */
    appearance: ; /* CSS 3 */
    backface-visibility: ; /* CSS 3 */
    background: ;
    background-attachment: ;
    background-color: ;
    background-image: ;
    background-position: ;
    background-repeat: ;
    background-clip: ; /* CSS 3 */
    background-origin: ; /* CSS 3 */
    background-size: ; /* CSS 3 */
    border: ;
    border-bottom: ;
    border-bottom-color: ;
    border-bottom-style: ;
    border-bottom-width: ;
    border-collapse: ;
    border-color: ;
    border-left: ;
    border-left-color: ;
    border-left-style: ;
    border-left-width: ;
    border-right: ;
    border-right-color: ;
    border-right-style: ;
    border-right-width: ;
    border-spacing: ;
    border-style: ;
    border-top: ;
    border-top-color: ;
    border-top-style: ;
    border-top-width: ;
    border-width: ;
    border-bottom-left-radius: ;
    border-bottom-right-radius: ;
    border-image: ; /* CSS 3 */
    border-image-outset: ; /* CSS 3 */
    border-image-repeat: ; /* CSS 3 */
    border-image-slice: ; /* CSS 3 */
    border-image-source: ; /* CSS 3 */
    border-image-width: ; /* CSS 3 */
    border-radius: ; /* CSS 3 */
    border-top-left-radius: ; /* CSS 3 */
    border-top-right-radius: ; /* CSS 3 */
    bottom: ;
    box-align: ; /* CSS 3 */
    box-direction: ; /* CSS 3 */
    box-flex: ; /* CSS 3 */
    box-flex-group: ; /* CSS 3 */
    box-lines: ; /* CSS 3 */
    box-ordinal-group: ; /* CSS 3 */
    box-orient: ; /* CSS 3 */
    box-pack: ; /* CSS 3 */
    box-sizing: ; /* CSS 3 */
    box-shadow: ; /* CSS 3 */
    caption-side: ;
    clear: ;
    clip: ;
    color: ;
    column-count: ; /* CSS 3 */
    column-fill: ; /* CSS 3 */
    column-gap: ; /* CSS 3 */
    column-rule: ; /* CSS 3 */
    column-rule-color: ; /* CSS 3 */
    column-rule-style: ; /* CSS 3 */
    column-rule-width: ; /* CSS 3 */
    column-span: ; /* CSS 3 */
    column-width: ; /* CSS 3 */
    columns: ; /* CSS 3 */
    content: ;
    counter-increment: ;
    counter-reset: ;
    cursor: ;
    direction: ;
    display: ;
    empty-cells: ;
    float: ;
    font: ;
    font-family: ;
    font-size: ;
    font-style: ;
    font-variant: ;
    font-weight: ;
    @font-face: ;
    font-size-adjust: ;
    font-stretch: ;
    grid-columns: ; /* CSS 3 */
    grid-rows: ; /* CSS 3 */
    hanging-punctuation: ; /* CSS 3 */
    height: ;
    icon: ; /* CSS 3 */
    @keyframes: ; /* CSS 3 */
    left: ;
    letter-spacing: ;
    line-height: ;
    list-style: ;
    list-style-image: ;
    list-style-position: ;
    list-style-type: ;
    margin: ;
    margin-bottom: ;
    margin-left: ;
    margin-right: ;
    margin-top: ;
    max-height: ;
    max-width: ;
    min-height: ;
    min-width: ;
    nav-down: ; /* CSS 3 */
    nav-index: ; /* CSS 3 */
    nav-left: ; /* CSS 3 */
    nav-right: ; /* CSS 3 */
    nav-up: ; /* CSS 3 */
    opacity: ; /* CSS 3 */
    outline: ;
    outline-color: ;
    outline-offset: ; /* CSS 3 */
    outline-style: ;
    outline-width: ;
    overflow: ;
    overflow-x: ; /* CSS 3 */
    overflow-y: ; /* CSS 3 */
    padding: ;
    padding-bottom: ;
    padding-left: ;
    padding-right: ;
    padding-top: ;
    page-break-after: ;
    page-break-before: ;
    page-break-inside: ;
    perspective: ; /* CSS 3 */
    perspective-origin: ; /* CSS 3 */
    position: ;
    punctuation-trim: ; /* CSS 3 */
    quotes: ;
    resize: ; /* CSS 3 */
    right: ;
    rotation: ; /* CSS 3 */
    rotation-point: ; /* CSS 3 */
    table-layout: ;
    target: ; /* CSS 3 */
    target-name: ; /* CSS 3 */
    target-new: ; /* CSS 3 */
    target-position: ; /* CSS 3 */
    text-align: ;
    text-decoration: ;
    text-indent: ;
    text-justify: ;
    text-outline: ;
    text-overflow: ; /* CSS 3 */
    text-shadow: ; /* CSS 3 */
    text-transform: ;
    text-wrap: ; /* CSS 3 */
    top: ;
    transform: ; /* CSS 3 */
    transform-origin: ; /* CSS 3 */
    transform-style: ; /* CSS 3 */
    transition: ; /* CSS 3 */
    transition-property: ; /* CSS 3 */
    transition-duration: ; /* CSS 3 */
    transition-timing-function: ; /* CSS 3 */
    transition-delay: ; /* CSS 3 */
    vertical-align: ;
    visibility: ;
    width: ;
    white-space: ;
    word-spacing: ;
    word-break: ; /* CSS 3 */
    word-wrap: ;
    z-index: ;
}
```

### <a name="nesting">8.Sass</a>
8.1. Синтаксис    
* Изпалзва се .scss разширението, никога оригиналното .sass 
* Всички partial-и се именоват с долна черта в началото на името `_partial.scss`.
Долната черта позволява на Sass да разбере, че този файл не бива да бъде компилиран до CSS файл.  

8.2. Подредба
1. Properties  
Описват се всички декларации на пропъртита, които не са @include и не са вложени селектори
```css
.btn-green {
    background: green;
    font-weight: bold;
    ...
}
```
2. @include декларации  
Групират се всички @include накрая за лесна четимост.
```css
.btn-green {
    background: green;
    font-weight: bold;
    @include transition(background 0.5s ease);
    ...
}
```
3. Вложени селектори  
Вложените селектори, ако е нужно, се декларират последни. Добавя се празен ред преди вложения селектор.
```scss
.btn {
    background: green;
    font-weight: bold;
    @include transition(background 0.5s ease);
 
    .icon {
        margin-right: 10px;
    }
}
```

* Избятвайте ненужното влагане. Само, защото може да използваме влагането, не означава, че то винаги е необходимо.
Използвайте влагане, когато трябва да се обвържат стилове към определен родител.

Без влагане:
```scss
.table > thead > tr > th { }
 
.table > thead > tr > td { }
```
С влагане:
```scss
.table > thead > tr {
    > th { }
      
    > td { }
}
```

* Не влагайте селектори на повече от 3 нива.
```scss
.page-container {
    .content {
        .profile {
          // STOP!
        }
    }
}
```
Ако се стигне до по-голямо влагане, най-вероятно пишете много специфичен и непреизползваем CSS!
* Не влагайте ID селектори!
  
8.3 Променливи
* Променливите се изписват с малки букви
* За разделител се използва тире "-" (не долна черта или camelCase).
```scss
$my-variable
```

8.4. Mixins  
Mixin-ите се използват за добавяне на ясното или абстракция.
Използването им без аргумент* също може да бъде полезно за това, но ако кода не се компресира, може да допринесе за дублирането на пропъртита.  
*В повечето случаи не се препоръчва използването им без аргумент. 

8.5. Extend  
@extend трябва да се избягва. Има неинтуитивно и потенциално опасно поведение, особено когато се използва с вложени селектори.

8.6. Коментари  
Освен `/* */` могат да се използват и `//` за едноредови коментари.


### <a name="css-modules">9. CSS Modules</a>

9.1. Класове

* При писане на css, който ще бъде използван като css модул, именоваме класовете camelCase.

Грешно:
```css
.class-name {
  ...
}
```
```css
.ClassName {
  ...
}
```
Правилно:
```css
.className {
  ...
}
```
9.2. Използване на css модул

* Когато импортваме даден css модул именуваме обекта `styles`.

Грешно:
```typescript
import login from 'somewhere';
```
Правилно:
```typescript
import styles from 'somewhere';
```
* Ако имаме няколко импорта ги изписваме като след `styles` към името на обекта добавим идентификатор за спецификата на тези стилове.
* Ползваме отново camelCase.

Грешно:
```typescript
import styles from 'somewhere';
import css from 'somewhere';
```
```typescript
import HomeStyles from 'somewhere';
import login from 'somewhere';
```
Правилно:
```typescript
import stylesHome from 'somewhere';
import stylesLogin from 'somewhere';
```

### <a name="stylelint">10. Stylelint</a>

10.1 Инсталиране на stylelint

```bash
sudo npm install -g stylelint
```
или
```bash
sudo yarn global add stylelint
```

10.2. Позволяване на плъгина в PhpStorm

10.2.1. Влезте в Settings/Preferences диалога и натиснете Stylesheets, в категорията Languages and Frameworks, има си поле
Stylelint, върху което трябва да кликнете.

10.2.2. Кликнете чекбокса Enable, за да активирате плъгина. 

10.3. Инсталиране на Standard config

```bash
sudo npm install stylelint-config-standard --save-dev 
``` 
или
```bash
sudo yarn add stylelint-config standard --dev
```

10.4. Инсталиране на плъгина за подреждане на свойствата

```bash
sudo npm install stylelint-order --save-dev 
``` 
или
```bash
sudo yarn add stylelint-order --dev
```

10.5. Инсталиране на плъгина на webpack за Stylelint

```bash
sudo npm install stylelint-webpack-plugin --save-dev
``` 
или
```bash
sudo yarn add stylelint-webpack-plugin --dev
```

10.6. В webpack config файла трябва да добавите плъгина
```javascript
// webpack.config.js
const StyleLintPlugin = require('stylelint-webpack-plugin');
 
module.exports = {
  // ...
  plugins: [
    new StyleLintPlugin(options),
  ],
  // ...
}
```

10.7. Ако използвате SCSS в проекта си може да инсталирате и този плъгин, въпреки че самият Stylelint
има много добра поддръжка на основния scss синтаксис. За повече информация може да проверите плъгина.

 ```bash
 sudo npm install stylelint-scss
 ``` 
 или
 ```bash
 sudo yarn add stylelint-scss
 ```

10.8. Добавяне на кофигурационнип файл на Stylelint
В root директорията добавете файла, който се намира в същата папка тук, с разширение `.stylelintrc`.
