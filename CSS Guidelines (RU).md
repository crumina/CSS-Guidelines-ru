# Общие советы и рекомендации по CSS
Русский перевод ([оригинал](https://github.com/csswizardry/CSS-Guidelines/blob/master/CSS%20Guidelines.md))

* [твиттер автора](http://twitter.com/csswizardry) / [твитнуть оригинал](https://twitter.com/intent/tweet?text=CSS+Guidelines+by+%40csswizardry%3A+https://github.com/csswizardry/CSS-Guidelines/)
* [мой твиттер](http://twitter.com/meshokmuki) / [твитнуть перевод](https://twitter.com/intent/tweet?text=%D0%A0%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D0%B0%D1%86%D0%B8%D0%B8%20%D0%BF%D0%BE%20CSS%20%D0%BE%D1%82+%40csswizardry%3A+https://github.com/pozadi/CSS-Guidelines-ru/+%D0%BF%D0%B5%D1%80%D0%B5%D0%B2%D0%B5%D0%BB%20%40meshokmuki)


## CSS документ

Мы используем оглавление в начале каждого CSS файла, в котором перечисленны секции документа. Заголовок каждой секции предваряется знаком `$` чтобы потом было легко найти нужную секуию с помощью поиска.

### Синтаксис и форматирование

Мы записываем каждое свойство на отделбной строке, что полезно для системы контроля версий, и сортируем свойства по смыслу, а не по оглавлению.

Имена классов мы записываем строчными буквами используя дефис в качестве разделителя: `.thisIsBad{}` &mdash; плохо, `.this_is_also_bad{}` &mdash; тоже плохо, `.this-is-correct{}` &mdash; хорошо.

Мы всегда ставим знак `;` после последнего свойства, чтобы избежать потенциальную синтаксическую ошибку, которую потом трудно будет найти.

Пример файла отформатированного в соответствии с этими рекомендациями можно посмотреть по этой ссылке: [github.com/csswizardry/vanilla/&hellip;/style.css](http://github.com/csswizardry/vanilla/blob/master/css/style.css)

**См. также:**

* [coding.smashingmagazine.com/&hellip;/writing-css-for-others](http://coding.smashingmagazine.com/2011/08/26/writing-css-for-others)
* [jasoncale.com/&hellip;/5-dont-format-your-css-onto-one-line](http://jasoncale.com/articles/5-dont-format-your-css-onto-one-line)


## Комментарии

Комментируйте чем больше тем лучше. Всё что может быть полезным, можно даже вставить кусок HTML кода, который поможет понять текущий кусок CSS.

Не стесьняйтесь быть многословными, всёравно файл будет пропущен через минификатор.


## Отступы

Для каждого уровня вложенности в HTML пытайтесь сделать соответствующие отступы в CSS. Например:

    .nav{}
        .nav li{}
            .nav a{}

    .promo{}
        .promo p{}

Также выравнивайте свойства с вендорными префиксами как-то так:

    -webkit-border-radius:4px;
       -moz-border-radius:4px;
            border-radius:4px;

Это лучше читается, но более важно, что (если редактор это поддерживает) можно отредактировать столбец изменив значение сразу для всех свойств.


## Создание новых ~компонентов~

При создании нового ~компоненнта~ пишите сначала HTML код, а потом CSS. Так вы сможете visually see which CSS properties are naturally inherited and thus avoid reapplying redundant styles.


## Объектно ориентированный CSS (OOCSS)

При создании компонентов старайтесь придерживаться принципов DRY (Don't Repeat Yourself &mdash; не повторяйся) и OO (Обектно Ориентированный)

Вместо создания множества уникальных компонентов попытайтесь найти повторяющиеся участки в дизайне и абстрагируйте их. ~После чего постройте скелет на основе этих объектов, и потом добавляйте дополнительные классы чтобы расширить их стили для более уникального вида.~

~Если вы создаете новый компонент, разделите его на структуру и "тему оформления". Постройте структуру используя очень объщие классы, которые мы можем использовать повторно, и затем используйте более специфичные классы чтобы настроить "тему оформления"~


**См. также:**

* [csswizardry.com/&hellip;/the-nav-abstraction](http://csswizardry.com/2011/09/the-nav-abstraction)
* [stubbornella.org/&hellip;/the-media-object-saves-hundreds-of-lines-of-code](http://stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code)


## ~Разметка~

Все компоненты должны быть полностью независимы от ширины. Ваши компоненты должны всегда оставаться растягивающимися и их ширина должна регулироваться системой сетки.

**Никогда** не указывайте высоту. Высота должна быть указана только у элементов которые имели высоту _до того_ как попали на сайт (т.е. картинки и спрайты). Вообще никогда не устанавливайте высоту для элементов `p`, `ul`, `div`, каких угодно. Обычно вы можете достич желаемого эффекта при помощи высоты строки (свойство `line-height`), что гараздо более гибко.

Систему сетки следует рассматривать в качестве полок. Они содержат контенет, но не являются им. Вы создаете стелаж из полок и затем наполняете его контентом.

Вам не следует никогда задавать какие-нибудь стили для служебных классов сетки, они нужны только для создания сетки. Никогда, ни при каких обстоятельствах, не применяйте свояства box-модели к элементам сетки.


## Размеры

Мы используем комбинацию методов для установки размеров элементов пользовательского интерфейса. Проценты, пиксели, em, rem'ы и, даже, вообще ничего.

**См. также:**

* [csswizardry.com/&hellip;/measuring-and-sizing-uis-2011-style](http://csswizardry.com/2011/12/measuring-and-sizing-uis-2011-style)


## Размеры текста

Мы используем rem'ы (с откатом к пикселям для старых браузеров). Мы не хотим устанавливать размеры шрифтов в пикелах в качестве стандарта. ??? Мы оставляем свойство `line-height` безразмерным везде, только если мы не пытаемся выровнить текст по вертикали. ???

Мы хотим избегать установки размера шрифта раз за разом, что бы достичь этого мы создаем предопределенные наборы размеров шрифтов в виде классов. И потом мы можем использовать эти классы повторно, вместо установки размера раз за разом.

Перед тем как написать очередное свойство `font-size`, проверьте нет ли уже готового класса.

**См. также:**

* [csswizardry.com/&hellip;/pragmatic-practical-font-sizing-in-css](http://csswizardry.com/2012/02/pragmatic-practical-font-sizing-in-css)


## Shorthand

It might be tempting to use declarations like `background:red;` but in doing so what we are actually saying is ‘I want no image to scroll, aligned top left and repeating X and Y and a background colour of red’. Nine times out of ten this won’t cause any issues but that one time it does is annoying enough to warrant not using such shorthand. Instead use `background-color:red;`.

Similarly, declarations like `margin:0;` are nice and short, but **be explicit**. If you’re actually only really wanting to affect the margin on the bottom of an element then it is more appropriate to use `margin-bottom:0;`.

Be explicit in which properties you set and take care to not inadvertently unset others with shorthand. E.g. if you only want to remove the bottom margin on an element then there is no sense in blitzing all margins with `margin:0;`.

Shorthand is good, but easily misused.


## Селекторы

Сохраняйте селекторы эфективными и переносимыми.

Тяжелые привязанные к расположению селекторы плохи по ряду причин. Возьмем для примера `.sidebar h3 span{}`. Этот селектор слишклм сильно привязан к положению элемента в HTML, и, таким образом, мы не можем перенести элемент `span` из `h3`, который, в свою очередь, должен оставаться внутри `.sidebar`.

Слишком длинные селекторы также могут вызвать проблемы с производительностью. Чем больше проверок в селекторах (наприме в `.sidebar h3 span` 3 проверки, а в `.content ul p a` -- четыре), тем больше работы для браузера.

Убедитесь что стили не привязаны к расположению в HTML, где это возможно и что селекторы красивые и короткие.

**Помните:** классы не бывают семантичными или несемантичными; они бывают разумны или неразумны! Хватит думать о семантичных именах классов и выберете что-то разумное и что будет служить долго.

**См. также:**

* [speakerdeck.com/&hellip;/breaking-good-habits](http://speakerdeck.com/u/csswizardry/p/breaking-good-habits)
* [csswizardry.com/&hellip;/writing-efficient-css-selectors](http://csswizardry.com/2011/09/writing-efficient-css-selectors)

### Слишком точные селекторы

Слишком точные селекторы &mdash; это например `div.promo`. Мы скорее всего могли добиться тогоже эффекта используя `.promo`. Конечно, иногда мы _хотим_ установить свойство для класса и элемента (например если у вас есть объщий класс `.error`, который должен выгляжеть иначе когда применяется к разным элементам (пример: `.error{ color:red; }` `div.error{ padding:14px; }`)), но в основном старайтесь избегать этого по возможности.

Другой пример слишком точного селектора &mdash; `ul.nav li a{}`. Как и выше, здесь мы можем опустить `ul`, и т.к. мы знаем что `.nav` &mdash; это список, каждый эдемент `a` _обязан_ быть внутри `li`. Таким образом мы можем упростить `ul.nav li a{}` до просто `.nav a{}`.

### Производительность

Whilst it is true that browsers will only ever keep getting faster at rendering CSS, efficiency is something we could do to keep an eye on. Short selectors, not using the universal (`*{}`) selector and avoiding more complex CSS3 selectors should help circumvent these problems.

**См. также:**

* [csswizardry.com/…/writing-efficient-css-selectors](http://csswizardry.com/2011/09/writing-efficient-css-selectors)


## Be explicit, don’t make assumptions ~Будьте явными, не делайте предположений~

Instead of using selectors to drill down the DOM to an element, it is often best to put a class on the element you explicitly want to style. Let’s take a specific example.

Imagine you have a promotional banner with a class of `.promo` and in there there is some text and call-to-action link. If there is just one `a` in the whole of `.promo` then it may be tempting to style that call-to-action via `.promo a{}`.

The problem here should be obvious in that as soon as you add a simple text link (or any other link for that matter) to the `.promo` container it will inherit the call-to-action styling, whether you want it to or not. In this case you would be best to explicitly add a class (e.g. `.cta`) to the link you want to affect.

Be explicit; target the element you want to affect, not its parent. Never assume that markup won’t change.


## ID и классы

Не используйте ID в CSS **вообще**. Они могут быть полезны для JavaScript и ссылок внутри документа, но используйте только классы в CSS. Мы не хотим видеть не единого ID ни в одном CSS документе.

Классы имеют большое преимущество -- возможность многоразового использования (даже если вы не хотите, вы всеравно можете), и еще они ~низкоспецифичные~.

**См. также:**

* [csswizardry.com/&hellip;/when-using-ids-can-be-a-pain-in-the-class](http://csswizardry.com/2011/09/when-using-ids-can-be-a-pain-in-the-class)


## `!important`

Это нормально использовать `!important` в классах-помощниках, и только в них. Будет праdильно добавить `!important` в `.error` (`.error{ color:red!important }`), т.к. вы знаете что хотите чьлюы это правило _всегда_ имело приоритет.

Не рекомендуется использовать `!important` повсеместно, например что-бы переопределить свойство определенное с более высоким уровнем вложенности. Переработайте свой код и попытайтесь решить эту проблему рефакторингом селекторов. Поддержание селекторов короткими и избегание ID сильно поможет с проблемами такого рода.


## Магические числа и абсолютные значения

A magic number is a number which is used because ‘it just works’. These are bad because they rarely work for any real reason and are not usually very futureproof or flexible/forgiving. They tend to fix symptoms and not problems.

For example, using `.dropdown-nav li:hover ul{ top:37px; }` to move a dropdown to the bottom of the nav on hover is bad, as 37px is a magic number. 37px only works here because in this particular scenario the `.dropdown-nav` happens to be 37px tall.

Instead we should use `.dropdown-nav li:hover ul{ top:100%; }` which means no matter how tall the `.dropdown-nav` gets, the dropdown will always sit 100% from the top.

Every time you hard code a number think twice; if you can avoid it by using keywords or ‘aliases’ (i.e. `top:100%` to mean ‘all the way from the top’) or&mdash;even better&mdash;no measurements at all then you probably should.

Every hard-coded measurement you set is a commitment you might not necessarily want to keep.


## Отдельные стили для IE (и других браузеров)

IE stylesheets can, by and large, be totally avoided. The only time an IE stylesheet may be required is to circumvent blatant lack of support (e.g. PNG fixes).

As a general rule, all layout and box-model rules can and _will_ work without an IE stylesheet if you refactor and rework your CSS. This means we never want to see `<!--[if IE 7]> element{ margin-left:-9px; } < ![endif]-->` or other such CSS that is clearly using arbitrary styling to just ‘make stuff work’.


## Отладка

If you run into a CSS problem **take code away before you start adding more** in a bid to fix it. The problem exists in CSS that is already written, more CSS isn’t the right answer!

Delete chunks of markup and CSS until your problem goes away, then you can determine which part of the code the problem lies in.

It can be tempting to put an `overflow:hidden;` on something to hide the effects of a layout quirk, but overflow was probably never the problem; **fix the problem, not its symptoms.**


## Препроцессоры

By following the above advice you should typically find the need for a preprocessor decreases dramatically. If you still wish to use a preprocessor then by all means do so, but only as en extension of the above, not an alternative.

For example, preprocessors’ nesting abilities often lead to overly specific and location dependent selectors. Let’s use our `. nav a{}` example again:

    .nav{
        li{
            a{}
        }
    }

Will compile to:


    .nav {}
    .nav li {}
    .nav li a {}

Whilst this is a very timid example, it does help illustrate how a lot of preprocessors’ built in ‘helpful’ aspects actually go against our ideals; `.nav li a{}` could (and should) just be `.nav a{}`.

Also, with mixins and the like, preprocessors teach you how to recognise abstractions&mdash;which is great&mdash;but not necessarily how to use them properly; there’s no point writing an abstracted mixin when you proceed to repeat it a dozen times in a stylesheet.

Be sure to know the ins-and-outs of excellent vanilla CSS and where a preprocessor can _aid_ that, not hinder or undo it. Learn the downsides of preprocessors inside-out and then fuse the best aspects of the two with the bad bits of neither.

