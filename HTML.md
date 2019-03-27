[Назад](README.md)

# HTML Coding Standard

[Въведение](#intro)  
[Терминология](#terminology)  
[Правила](#rules)  
    1. [Валиден HTML](#valid-html)  
        1.1. [Използване на правилен тип на документа (Document Type)](#doctype)   
        1.2. [Подравняване](#alignment)  
        1.3. [Всички елементи и прилежащите им атрибути се изписват с малки букви](#small-letters)  
        1.4. [Всички HTML елементи трябва да са затворени](#close-elements)  
        1.5. [Всички празни HTML елементи трябва да са затворени](#close-empty-elements)  
        1.6. [Всяка стойност на атрибути се огражда с двойни кавички](#double-quotes)  
        1.7. [Специалните символи се пишат с техните кодови означения](#special-symbols)  
        1.8. [Не се използват deprecated етикети и атрибути](#deprecated-attr)  
        1.9. [Форми](#forms)  
    2. [Style Sheets](#style)  
    3. [JavaScript](#js)  
    4. [HTML коментари](#comments)  
    5. [SEO](#seo)  
[Използване на HTML5 семантични елемент](#semantic-elements)  
[Примерна структура](#example)  
[Изключения и прекалено много код](#exception)  

## <a name="intro">Въведение</a>
Този документ има за цел да наложи базовите правила и представи добрите 
практики при разработване на HTML код. Стриктното спазване на посочените по-долу правила 
и добри практики ще спомогне в настоящата и бъдеща работа на екипа програмисти.
Документа е отправна точка при извършването на Code Review. 
  
## <a name="terminology">Терминология</a> 
```html
<!DOCTYPE html>
<head>
    <meta charset="UTF-8" />
</head>
<html>
    <body>
        <h1>My First Heading</h1>
        <p>My first paragraph.</p>
        <div>
            Lorem ipsum ...
            <a id="link-1" class="link-class" href="javascript:(function(){xajax_...})();" title="Link Name">Link Name</a>
            <br />
            Lorem ipsum ...
        </div>
    </body>
</html>

```
* **`<h1>`** - отварящ таг
* **`</h1>`** - затварящ таг
* **`"My First Heading"`** - съдържание
* **`<h1>My First Heading</h1>`** - елемент
* **`<br />`** - единичен/самозатварящ се таг
* **`id="..." class="..." title="..."`** - атрибути
* **`onclick="..." on...="..."`** – събития
  
## <a name="rules">Правила</a>
### <a name="valid-html">1. Валиден HTML</a>
#### <a name="doctype">1.1. Използване на правилен тип на документа (Document Type)</a>  
Винаги сe дакларира тип на документа (Document Type) на първия ред от документа:      
```html
<!DOCTYPE html>
```
За консистентност може да се изписват малки букви:
```html
<!doctype html>
```
  
#### <a name="alignment">1.2. Подравняване</a>
* Индетацията става с 2 интервала, от тук нататък нарични **една индентация**
* Спазва се дървовидната структура на изписване - всеки нов елемент една индентация навътре
```html
<section>
    <p>
        <span>This is a span.</span>
        <span>This is a span.</span>
    </p>
    <p>This is a paragraph.</p>
</section>
```
* Да не се добавят празни редове без причина.  
  Празни редове се добавят за отделяне на големи или логически блокове код за четимост.   
* Избягване на редове код по-дълги от 120 символа.
  
#### <a name="small-letters">1.3. Всички елементи и прилежащите им атрибути се изписват с малки букви</a>
Грешно:
```html
<SECTION> 
    <p CLASS="menu">This is a paragraph.</p>
</SECTION>
```
Много грешно:
```html
<Section> 
    <p CLASS="menu">This is a paragraph.</p>
</SECTION>
```
Правилно:
```html
<section> 
    <p class="menu">This is a paragraph.</p>
</section>
```
   
#### <a name="close-elements">1.4. Всички HTML елементи трябва да са затворени</a>
Грешно:
```html
<section>
    <p>This is a paragraph.
    <p>This is a paragraph.
</section>
```
Правилно:
```html
<section>
    <p>This is a paragraph.</p>
    <p>This is a paragraph.</p>
</section>
```
  
#### <a name="close-empty-elements">1.5. Всички празни HTML елементи (елементи, които не са създадени да имат тяло) трябва да са затворени</a>
```html
<meta charset="utf-8" />
<img class="image" src="" alt="" /> 
```
  
#### <a name="double-quotes">1.6. Всяка стойност на атрибути се огражда с двойни кавички</a>
```html
<p id="paragraph" class="menu">This is a paragraph.</p>
```
  
#### <a name="special-symbols">1.7. Специалните символи се пишат с техните кодови означения.</a>
* символът "&" се въвежда в кода като "`&amp;`"
* символът "©" се въвежда в кода като "`&copy;`"

Списък със специалните символи и техните кодови означения може да намерите [тук](http://www.ascii.cl/htmlcodes.htm) 
  
#### <a name="deprecaed-attr">1.8. Не се използват deprecated етикети и атрибути.</a>

| Deprecated   | Описание                                 | Заместител        |
|--------------|------------------------------------------|-------------------|
| `<applet>`   | Inserts applet                           | `<object>`        |
| `<acronym>`  | Defines an acromyn                       | `<abbr>`          |
| `<basefont>` | Sets font styles                         | font style sheets |
| `<big>`      | Defines big text                         |                   |
| `<center>`   | Centers elements                         |                   |
| `<dir>`      | Directory list                           | `<ul>`            |
| `<font>`     | Applies font styles                      | font style sheet  |
| `<frame>`    | Defines a window (a frame) in a frameset |                   |
| `<frameset>` | Defines a set of frames                  |                   |
| `<isindex>`  | Adds search field                        | `<form>`          |
| `<menu>`     | Menu list                                | `<ul>`            |
| `<strike>`   | Strike through                           | text style sheets |
| `<tt>`       | Defines teletype text                    | text style sheets |
  
#### <a name="forms">1.9. Форми</a>
* **Препоръчително** Полетата (`<input>`) във формата да имат етикет (`<label>`) с "for" атрибут, който да съвпада с "id" атрибута на полето.
Това спомага достъпността на полето (`<input>`), при клик върху етикета (`<label>`)
```html
<label for="field-email">email</label>
<input type="email" id="field-email" name="email" value="" />
```
* **Препоръчително** Всяко поле (`<input>`) да има атрибут "id", който да е уникален за страницата. Не е задължително да съвпада
с атрибута "name".
* Използването на новите типове полета (`<input>`) във формите е препоръчително, където това има смисъл и за браузъри, които ги поддържат.
* Placeholder атрибутът се използва навсякъде, където е уместно.

```html
<div>
    <label for="field-email">Email</label>
    <input type="email" id="field-email" name="email" value="name@example.com">
</div>
<div>
    <label for="field-phone">Phone</label>
    <input type="phone" id="field-phone" name="phone" value="" placeholder="+44 077 12345 678">
</div>
<div>
    <label for="field-url">Homepage</label>
    <input type="url" id="field-url" name="url" value="" placeholder="http://example.com">
</div>
```
  
### <a name="style">2. Style Sheets</a>
* Използва се опростен синтаксис за линкване на стил в `<head>` тага на HTML страницата
```html
<head>
    <title>My Favorites Kinds of Corn</title>
    <link rel="stylesheet" type="text/css" media="screen" href="path/to/file.css" />
    <link rel="stylesheet" type="text/css" media="screen" href="path/to/anotherFile.css" />
</head>
```
* Стилове в HTML страница не трябва да има. Само в краен случай трябва да се прибягва до inline стилизиране и влагане на
 CSS в страницата.
* Именуването на класове и ид-та трябва да отговаря на CSS стандарта.
  
### <a name="js">3. JavaScript</a>
Основната цел е страницата да се зарежда възможно най-бързо за потребителя. При зареждане на скрипт браузъра не може да 
продължи, докато целия файл не бъде зареден. По този начин потребителя ще трябва да изчака по-дълго, преди да забележи някакъв 
прогрес. Ако има JS файлове, чиято единствена цел е да добавя функционалност, поставете тези файлове преди затварянего на <body> 
елемента. Това е най-добрата практика.

```html
<body>
    <p>Example paragraph.</p>
    <script type="text/javascript" src="path/to/file.js"></script>
    <script type="text/javascript" src="path/to/anotherFile.js"></script>
</body>
```
  
### <a name="comments">4. HTML коментари</a>
* Кратките коментари се изписват на един ред по следния начин: 
```html
<!-- This is a comment -->
```
* Коментари на повече от един ред се изписват по този начин:
```html
<!-- 
    This is a long comment example. This is a long comment example.
    This is a long comment example. This is a long comment example.
-->
```
  
### <a name="seo">5. SEO</a>
* Всеки документ трябва да използва HTML5 doctype и <html> елемента трябва да има "lang" атрибут. В <head> елемента трябва да се използват поне "viewport" и "charset" мета тагове.
* Title Tag (Заглавен таг) - Текстът, който се появява най-отгоре в браузъра, описващ съдържанието на сайта. Важно е той да е уникален за всяка страница.
* Heading Tag - Използване на главни тагове – h1 до h6
        – Добавяне на таг h1 най-горе в страницата;  
        – Добавят се не повече от 1 `<h1>` таг на страница;  
        – Ако имаме подзаглавие, следователно то трябва да е в `<h2>`;  
* Image ALT Tags (ALT тагове на изображенията) - `<img>` тагът задължително има атрибут "alt". Това подсказва на търсачките какво показват изображенията.
* Link title attribute - `<a>` тагът задължително има атрибут "title"
* Meta description 

Незадължителни мета тагове
Тези мета тагове не са задължително, но крайното решение зависи не от разработчика, а от бизнеса и заданието.
Затова вземете информирано решение преди да ги отхвърлите.
* Social meta tags - [Повече информациа](http://ogp.me/)
* Geo meta tag 
* Keywords meta tag
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1">
    
    <!-- Title tag -->
    <title>Example Site</title>
    <!-- Description meta tag -->
    <meta name="description" content="This is an example of a meta description. This will often show up in search results.">
    <!-- Keywords meta tag -->
    <meta name="keywords" content="example test">
    <!-- Geo meta tag -->
    <meta name="geo.position" content="latitude; longitude">
    <meta name="geo.placename" content="Place Name">
    <meta name="geo.region" content="Country Subdivision Code">
    <!-- Social meta tags -->
    <meta property="og:title" content="" />
    <meta property="og:type" content="" />
    <meta property="og:url" content="" />
    <meta property="og:image" content="" />
</head>
<body>
    <h1>I'm a title!</h1>
    <h2>I'm a subtitle!</h1>
    <img src="" alt="image" />
    <a href="" title="link">Link</a>
</body>
</html>
```
### <a name="semantic-elements">Използване на HTML5 семантични елементи</a>
* Елемент `<header>` - представлява заглавие на елемент или група от елементи. Тага `<header>` позволява използването на няколко
заглавия в един документ за разлика от възможността която предоставя HTML4.   
Пример:
```html
<article>
    <header>
        <h1>HTML</h1>
        <p><time pubdate datetime="1990"></time></p>
    </header>
    <p>HTML5 is the fifth revision of the HTML standard (created in 1990 and standardized as HTML 4 as of 1997.....</p>
</article>
```
* Елемент `<nav>` - дефинира навигацията на сайта. Той е предназначен за големи блокове от навигационни връзки. Не всички
 връзки трябва да са в `<nav>` елемента, а само главното навигационно меню.  
Пример:
```html
<nav>
    <a href="/html/">HTML</a> 
    <a href="/css/">CSS</a> 
    <a href="/js/">JavaScript</a> 
    <a href="/jquery/">jQuery</a>
</nav>
```
* Елемент `<article>` - представлява предмет/статия. Съдържанието в `<article>` трябва да има смисъл само по себе си и 
да може да се разпространява независимо и отделно от останалата част на сайта. Използва се най - често за публикация
във форум; публикация в блог; новини; коментари и др.  
Пример:
```html
<article>
    <h1>HTML</h1>
    <p>HTML5 is the fifth revision of the HTML standard (created in 1990 and standardized as HTML 4 as of 1997.....</p>
</article>
```
* Елемент `</section/>` е тематично групирано съдържание, обикновено със заглавие. Този елемент позволява влагане на нова 
сегмантична структура във вече съществуващ елемент.   
Пример:
```html
<section>
    <h1>WWF</h1>
    <p>The World Wide Fund for Nature (WWF) is....</p>
</section>
```
* Елемент `<aside>` - той представя съдържание което е странично от основното съдържание на страницата. Съдържанието в 
`<aside>` се счита за неважно и може да бъде пропуснато, ако сайта се възпроизвежда на устройство с малък екран като телефон.   
Пример:
```html
<p>My family and I visited The Epcot center this summer.</p>
<aside>
  <h4>Epcot Center</h4>
  <p>The Epcot Center is a theme park in Disney World, Florida.</p>
</aside>
```
* Елемент `<footer>` - може да съдържа информация за автора на страницата; навигация на сайта; авторските права върху 
използваните материали и връзки към други (подобни) публикации.   
Пример:
```html
<footer>
    <p>Posted by: John Williams</p>
    <p><time pubdate datetime="2013-05-05"></time></p>
</footer>
```
  
### <a name="example">Примерна структура</a> 
```html
<!-- START ARTICLE /LOCATION -->
<article class="article">
    <h2>
        <a class="bullet" href="#location">Location</a>
        <span class="ornament"></span>
        <span class="shape"></span>
    </h2>
    <p>You are located on a huge continent with room for more than 40 000 Empires, which don't begin their development on equal terms, due to being managed by two different races - Imperians and Nomads.</p>
    <p>Each Empire has a total of 19 available provinces, ready to be: <br />attacked (Fortress siege), turned into vassals or annexed.</p>
    <p>No player can control foreign provinces. The only right he has is to attack them, destroying the Fortress, or pillage them, slaughtering civil population. Researches and the rest of the buildings.</p>
    <p>Besides the territories of your own Empire, those on the Imperial Map, you dispose of spots on the Global Map, equally accessible for everyone, but with different destinations:</p>
    <ul>
        <li>For foundation of Colonies - the most numerable spots, randomly located and intended for colonizing by an individual player.</li>
        <li>For building an Alliance Castle and establishing an Alliance expansion of cultural and military influence all over the Global Map.</li>
        <li class="last">For construction of Rally Point, gathering all Alliance army in a departure point for any Alliance military mission.</li>
    </ul>
</article>
<!-- END ARTICLE /LOCATION --> 
```
  
### <a name="exceptions">Изключения и прекалено много код</a>
При наличието на прекалено много атрибути или прекалено дълъг код се допуска всеки нов атрибут да е на нов ред. Всеки атрибут
трябва да е един таб навътре спрямо отварящия етикет, както следва:
 ```html
<a 
    id="..."
    class="..."
    href="some-link"
    title="..."
>
Link
</a>
<input 
	id="input-id-nth"
	class="input-class"
	type="text"
    name="soldiers-escort"
    value="something"
    disabled="disabled"
/>
```
