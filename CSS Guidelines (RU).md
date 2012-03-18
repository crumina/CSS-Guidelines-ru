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

When building a new component write markup **before** CSS. This means you can visually see which CSS properties are naturally inherited and thus avoid reapplying redundant styles.


## Объектно ориентированный CSS (OOCSS)

When building components try and keep a DRY, OO frame of mind.

Instead of building dozens of unique components, try and spot repeated design patterns abstract them; build these skeletons as base ‘objects’ and then peg classes onto these to extend their styling for more unique circumstances.

If you have to build a new component split it into structure and skin; build the structure of the component using very generic classes so that we can reuse that construct and then use more specific classes to skin it up and add design treatments.

**См. также:**

* [csswizardry.com/&hellip;/the-nav-abstraction](http://csswizardry.com/2011/09/the-nav-abstraction)
* [stubbornella.org/&hellip;/the-media-object-saves-hundreds-of-lines-of-code](http://stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code)


## Layout ~Разметка~

All components should be left totally free of widths; your components should always remain fluid and their widths should be governed by a grid system.

Heights should **never** be be applied to elements. Heights should only be applied to things which had dimensions _before_ they entered the site (i.e. images and sprites). Never ever set heights on `p`s, `ul`s, `div`s, anything. You can normally achieve the desired effect with line-heights which are far more flexible.

Grid systems should be thought of as shelves. They contain content but are not content in themselves. You put up your shelves then fill them with your stuff.

You should never apply any styles to a grid item, they are for layout purposes only. Never, under any circumstances, apply box-model properties to a grid item.


## Размеры

We use a combination of methods for sizing UIs. Percentages, pixels, ems, rems and nothing at all.

**См. также:**

* [csswizardry.com/&hellip;/measuring-and-sizing-uis-2011-style](http://csswizardry.com/2011/12/measuring-and-sizing-uis-2011-style)


## Размеры текста

We use rems (with a pixel fallback for older browsers only). We do not want to define any font sizes in pixels as standard. We define line heights unitlessly everywhere **unless** we are trying to align text to known heights.

We want to avoid defining font sizes over and over; to achieve this we have a predefined scale of font sizes tethered to classes. We can recycle these rather than having to declare styles over and over.

Before writing another font-size declaration, see if a class for it already exists.

**См. также:**

* [csswizardry.com/&hellip;/pragmatic-practical-font-sizing-in-css](http://csswizardry.com/2012/02/pragmatic-practical-font-sizing-in-css)


## Shorthand

It might be tempting to use declarations like `background:red;` but in doing so what we are actually saying is ‘I want no image to scroll, aligned top left and repeating X and Y and a background colour of red’. Nine times out of ten this won’t cause any issues but that one time it does is annoying enough to warrant not using such shorthand. Instead use `background-color:red;`.

Similarly, declarations like `margin:0;` are nice and short, but **be explicit**. If you’re actually only really wanting to affect the margin on the bottom of an element then it is more appropriate to use `margin-bottom:0;`.

Be explicit in which properties you set and take care to not inadvertently unset others with shorthand. E.g. if you only want to remove the bottom margin on an element then there is no sense in blitzing all margins with `margin:0;`.

Shorthand is good, but easily misused.


## Селекторы

Keep selectors efficient and portable.

Heavily location-based selectors are bad for a number of reasons. For example, take `.sidebar h3 span{}`. This selector is too location-based and thus we cannot move that `span` outside of a `h3` outside of `.sidebar` and maintain styling.

Selectors which are too long also introduce performance issues; the more checks in a selector (e.g. `.sidebar h3 span` has three checks, `.content ul p a` has four), the more work the browser has to do.

Make sure styles aren’t dependent on location where possible, and make sure selectors are nice and short.

**Помните:** classes are neither semantic or insemantic; they are sensible or insensible! Stop stressing about ‘semantic’ class names and pick something sensible and futureproof.

**См. также:**

* [speakerdeck.com/&hellip;/breaking-good-habits](http://speakerdeck.com/u/csswizardry/p/breaking-good-habits)
* [csswizardry.com/&hellip;/writing-efficient-css-selectors](http://csswizardry.com/2011/09/writing-efficient-css-selectors)

### Слишком точные селекторы

An over-qualified selector is one like `div.promo`. We could probably get the same effect from just using `.promo`. Of course sometimes we will _want_ to qualify a class with an element (e.g. if you have a generic `.error` class that needs to look different when applied to different elements (e.g. `.error{ color:red; }` `div.error{ padding:14px; }`)), but generally avoid it where possible.

Another example of an over-qualified selector might be `ul.nav li a{}`. As above, we can instantly drop the `ul` and because we know `.nav` is a list, we therefore know that any `a` _must_ be in an `li`, so we can get `ul.nav li a{}` down to just `.nav a{}`.

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

Do not use IDs in CSS **at all**. They can be used in your markup for JS and fragment-identifiers but use only classes for styling. We don’t want to see a single ID in this (or any other) stylesheet.

Classes come with the benefit of being reusable (even if we don’t want to, we can) and they have a nice, low specificity.

**См. также:**

* [csswizardry.com/&hellip;/when-using-ids-can-be-a-pain-in-the-class](http://csswizardry.com/2011/09/when-using-ids-can-be-a-pain-in-the-class)


## `!important`

It is okay to use `!important` on helper classes only. To add `!important` preemptively is fine, e.g. `.error{ color:red!important }`, as you know you will **always** want this rule to take precedence.

Using `!important` reactively, e.g. to get yourself out of nasty specificity situations, is not advised. Rework your CSS and try to combat these issues by refactoring your selectors. Keeping your selectors short and avoiding IDs will help out here massively.


## Магические числа и абсолютные значения

A magic number is a number which is used because ‘it just works’. These are bad because they rarely work for any real reason and are not usually very futureproof or flexible/forgiving. They tend to fix symptoms and not problems.

For example, using `.dropdown-nav li:hover ul{ top:37px; }` to move a dropdown to the bottom of the nav on hover is bad, as 37px is a magic number. 37px only works here because in this particular scenario the `.dropdown-nav` happens to be 37px tall.

Instead we should use `.dropdown-nav li:hover ul{ top:100%; }` which means no matter how tall the `.dropdown-nav` gets, the dropdown will always sit 100% from the top.

Every time you hard code a number think twice; if you can avoid it by using keywords or ‘aliases’ (i.e. `top:100%` to mean ‘all the way from the top’) or&mdash;even better&mdash;no measurements at all then you probably should.

Every hard-coded measurement you set is a commitment you might not necessarily want to keep.


## Conditional stylesheets

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