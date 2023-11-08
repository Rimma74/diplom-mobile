# Дипломный проект курса «Адаптивная и мобильная верстка»

**Диплом должен быть реализован локально и опубликован на сервисе [GitHub Pages](https://pages.github.com/). 

В рамках дипломного проекта вам необходимо сверстать макет сайта для трех групп устройств: десктопные экраны, планшеты и смартфоны.

Макеты сайта для различных экранов выглядят так:

![Layout](img/layouts.jpg)

Исходные файлы макетов хранятся в директории [sources](./sources/) репозитория:

- `NOEMI_mq_desktop.psd` – макет для экрана шириной 1200px и более,
- `NOEMI_mq_tablet.psd` – макет для экрана шириной 768px,
- `NOEMI_mq_mobile.psd` – макет для экрана шириной 360px.

О верстке промежуточных состояний подробнее читайте в разделе [Промежуточные состояния между макетами](#Промежуточные-состояния-между-макетами).

Также папка [sources](./sources/) содержит jpg-изображения – превью макетов для быстрого просмотра. **Не верстайте сайт с превью, используйте для верстки psd-макеты.**

В поддиректории [fonts](./sources/fonts/) вы можете найти использующиеся в макете шрифты, а в поддиректории [svg](./sources/svg/) — иконки в формате `svg`.

## Требования

#### Содержание
- [Основа проекта](#Основа-проекта)
- [Кроссбраузерная верстка](#Кроссбраузерная-верстка)
- [Семантическое использование тегов](#Семантическое-использование-тегов)
- [Семантические названия атрибутов](#Семантические-названия-атрибутов)
- [Валидная верстка](#Валидная-верстка)
- [Соответствие верстки макету](#Соответствие-верстки-макету)
- [Реализация сетки](#Реализация-сетки)
- [Промежуточные состояния между макетами](#Промежуточные-состояния-между-макетами)
- [Добавление меньшего или большего количества контента в блоки](#Добавление-меньшего-или-большего-количества-контента-в-блоки)
- [Ошибки загрузки изображений](#Ошибки-загрузки-изображений)
- [Не используйте CSS-методологии](#Не-используйте-CSS-методологии)
- [Не используйте готовые библиотеки](#Не-используйте-готовые-библиотеки)
- [Не используйте CSS-препроцессоры или PostCSS](#Не-используйте-CSS-препроцессоры-или-PostCSS)
- [Не используйте autoprefixer](#Не-используйте-autoprefixer)
- [Оформление кода](#Оформление-кода)
- [Файловая структура проекта](#Файловая-структура-проекта)
- [Публикация проекта](#Публикация-проекта)
- [Как правильно задавать вопросы дипломному руководителю?](Как-правильно-задавать-вопросы-дипломному-руководителю?)

### Основа проекта
Макет диплома для курса MQ основан на макете диплома для курса HTML. Вы можете взять код предыдущего диплома за основу и доработать его в соответствии с требованиями к диплому текущего курса. 

Обратите внимание, что следует заменить в коде все абсолютные пути до файлов с картинками, шрифтами и иконками на относительные.
Инструкция по работе с относительными путями в рамках проекта: [инструкция](https://github.com/netology-code/guides/tree/master/relative-link).

### Кроссбраузерная вёрстка
В рамках проекта свёрстанные макеты должны корректно отображаться на следующих типах устройств:
- компьютерах с операционными системами Windows и Mac OS,
- планшетах и смартфонах с операционной системой iOS,
- планшетах и смартфонах с операционной системой Android.

Кроме поддержки основных типов устройств также требуется, чтобы вёрстка корректно работала в следующих браузерах:
- Последняя версия Google Chrome,
- Последняя версия Mozilla FireFox,
- Последняя версия Edge,
- Последняя версия Opera,
- Последняя версия Safari,
- Последняя версия Mobile Safari,
- Последняя версия Mobile Chrome.

В случае, если у вас нет какого-то устройства или программы, постарайтесь их найти или используйте эмуляторы, встроенные в браузер. Тестирование на реальных устройствах является важным навыком современного специалиста.

### Соответствие вёрстки макету
Итоговый проект должен быть копией макетов, предоставленных дизайнером. При реализации допускаются небольшие отличия:
- толщина шрифта в браузерах и фотошопе,
- межсимвольное расстояние,
- различия в отступах до 5px.

### Промежуточные состояния между макетами
Дизайнер подготовил три макета отображения страницы для устройств с шириной экрана 360px, 768px и 1200px. Но дизайнер не предоставил отображения страницы в промежуточных состояниях, поэтому их нужно реализовать с помощью принципа «Резиновая вёрстка».

Таким образом, на экранах с шириной больше 1200px фоновые блоки будут растягиваться на всю ширину экрана, а их контент будет центрироваться.

На устройствах с шириной экрана от 1200px и более вам нужно реализовать дизайн макета `NOEMI_mq_desktop.psd`.

Для устройств с шириной экрана, попадающей в диапазон от 641px до 1200px, вам нужно реализовать резиновый дизайн макета `NOEMI_mq_tablet.psd`.

Для устройств с шириной экрана от 640px и меньше вам нужно реализовать резиновый дизайн макета `NOEMI_mq_mobile.psd`.

### Состояния при повороте экрана
Вёрстка раздела «Сейчас в тренде» должна отличаться при портретной (вертикальной) ориентации экрана и при пейзажной (горизонтальной).

Для устройств с шириной экрана, попадающей в диапазон от 641px до 1200px, при портретной ориентации экрана карточки трендов должны быть выстроены в две колонки, а при пейзажной ориентации — в четыре.

Для устройств с шириной экрана от 640px и меньше, при портретной ориентации экрана должна быть одна колонка с карточками, а при пейзажной — две.

![Layout](img/rotation.jpg)

### Вёрстка всплывающей формы (попап)
Каждый макет содержит всплывающую форму на слое `Popup`, этот слой по умолчанию скрыт. Свёрстанная форма должна отображаться по центру экрана, поверх вуали, затемняющей страницу. 

**Вам не нужно реализовывать всплытие формы и её скрывание при клике на крестик.** Достаточно, чтобы форма была в разметке и ваш дипломный руководитель мог её найти. 

После того, как закончите с вёрсткой всплывающего окна добавьте блоку класс `_hidden` и задайте этому классу свойства, скрывающие блок.

![Layout](sources/NOEMI_mq_desktop_popup.jpg)

### Вёрстка бургер-меню
**Вам не нужно реализовывать сворачивание и разворачивание бургер-меню при клике на иконку**. В зависимости от макета, должна быть видима либо иконка, либо меню.

### Семантическое использование тегов
В макетах проекта содержатся следующие элементы:
- Разделы,
- Заголовки,
- Ссылки,
- Изображения,
- Подписи,
- Абзацы.

Все эти элементы имеют специальные теги в стандарте HTML5, поэтому в рамках проекта вам необходимо их использовать.

К примеру, следующий код является грубой ошибкой:
```html
<div class="header">
  <div class="title">Заголовок сайта</div>
</div>
```

Кроме использования семантических тегов, также нужно правильно вкладывать теги по типу контекста. Запрещается в строчный элемент помещать блочный. Например, следующий код будет ошибочным:

```html
<span class="information">
  <h2 class="title">Заголовок блока</h2>
</span>
```

### Семантические названия атрибутов
Кроме использования семантических тегов также необходимо давать семантические названия на английском языке в качестве значений атрибутов. Не используйте транслит. 

Пример:
```html
<header class="shapka"></header>
```
Данный пример является грубой ошибкой. Название класса `shapka` следует заменить на `header`. Пример корректного названия:
```html
<header class="header"></header>
```
### Валидная вёрстка
После полной реализации вёрстки протестируйте её с помощью сервиса [W3C Markup Validation Service](https://validator.w3.org). В итоговом отчете не должно быть ошибок или предупреждений.

### Реализация сетки
Реализовать сетку страницы вам нужно при помощи `flexbox`. Использование библиотек, которые уже имеют готовые классы для сетки (например, Twitter Bootstrap, Zurb Foundation и другие), будет считаться ошибкой.

Также ошибкой будет считаться использование следующих способы вёрстки сетки:
- таблицы,
- float-сетка,
- сетка с помощью `inline-block` элементов,
- CSS Grids.

### Добавление меньшего или большего количества контента в блоки
Нужно протестировать блоки с информацией, добавив в них больше или меньше контента, чем представлено в макетах. Блоки не должны сломать соседние блоки, текст при этом должен быть полностью читаемым.

[Этот пункт встречался в дипломе для курса HTML](https://github.com/netology-code/html-2-diploma#%D0%94%D0%BE%D0%B1%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BC%D0%B5%D0%BD%D1%8C%D1%88%D0%B5%D0%B3%D0%BE-%D0%B8%D0%BB%D0%B8-%D0%B1%D0%BE%D0%BB%D1%8C%D1%88%D0%B5%D0%B3%D0%BE-%D0%BA%D0%BE%D0%BB%D0%B8%D1%87%D0%B5%D1%81%D1%82%D0%B2%D0%B0-%D0%BA%D0%BE%D0%BD%D1%82%D0%B5%D0%BD%D1%82%D0%B0-%D0%B2-%D0%B1%D0%BB%D0%BE%D0%BA%D0%B8).

### Ошибки загрузки изображений
При вёрстке изображений вам нужно предусмотреть ситуацию, когда по какой-либо причине они не загрузятся.

- В случае контентных изображений вёрстка не должна сломаться, а вместо изображения должен отображаться альтернативный текст, из которого станет понятно, что было изображено на картинке.

- Для декоративных изображений вам необходимо подобрать подложки для текста, чтобы текст был читаемым в любой ситуации. 

### Не используйте CSS-методологии
В рамках курса мы не рассматриваем CSS-методологии. Например БЭМ, OOCSS, SMACSS и другие. Поэтому при работе над дипломом не используйте их.

### Не используйте готовые библиотеки
В рамках дипломного проекта не следует использовать готовые библиотеки (например, normalize.css, reset.css, bootstrap и другие). Весь код вы должны написать самостоятельно.

### Не используйте CSS-препроцессоры или PostCSS
В рамках курса мы не рассматриваем способы организации кода с использованием CSS-препроцессоров и PostCSS. Поэтому в дипломе вам не следует их использовать.

### Не используйте autoprefixer
Для реализации кроссбраузерной вёрстки дипломного проекта вам не потребуется autoprefixer, поэтому его использование не приветствуется.

### Оформление кода
Дипломный проект обязательно должен соответствовать принятому стилю кода для [HTML](https://github.com/netology-code/codestyle/tree/master/html) и [CSS](https://github.com/netology-code/codestyle/tree/master/css). В случае ошибок в оформлении проект не может быть принят и будет отправлен на доработку. 

### Файловая структура проекта
Файловая структура проекта должна состоять из следующих элементов:
- `css` — папка, содержащая стили проекта,
- `fonts` — папка, содержащая шрифты проекта,
- `images` — папка, содержащая графику проекта,
- `index.html` — HTML-страница.

Файла проекта должны соответствовать [правилам именования файлов](https://github.com/netology-code/codestyle/tree/master/naming).  

### Публикация проекта

При разработке проекта и для итоговой демонстрации вам нужно использовать сервис GitHub Pages. Перед работой с сервисом ознакомьтесь с видео-инструкцией по [ссылке](https://embed.new.video/cxEqtfQzkYST15TtikEAWF?sig=eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lwIjoiMTA5LjI1Mi40MS45OCIsInZpZGVvX3Rva2VuIjoiY3hFcXRmUXprWVNUMTVUdGlrRUFXRiJ9.fqxDLhpUA1gcTj6mnjqO0q9r5Wvqk8by1jdkCzz6FMY)

### Как правильно задавать вопросы дипломному руководителю?
Что поможет решить большинство частых проблем:

1. Попробовать найти ответ сначала самому в интернете. Скилл поиска ответов пригодится вам в профессиональной деятельности. И только после этого спрашивать дипломного руководителя.
1. Если вопросов больше одного, то присылайте их в виде нумерованного списка. Так дипломному руководителю будет проще отвечать на каждый из них. 
1. Пори необходимости прикрепите к вопросу скриншоты и стрелочкой покажите где не получается. Программу для этого можно скачать здесь [https://app.prntscr.com/ru/](https://app.prntscr.com/ru/)
1. По возможности, задавайте вопросы в комментариях к коду. 
1. Начинать работу над дипломом как можно раньше! Чтобы было больше времени на правки.
1. Делайте диплом частями, а не всё сразу. Если сделать всё сразу, то количество комментариев от дипломного руководителя может вас деморализовать. 

Что может стать источником проблем:

1. Вопросы вида «Ничего не работает. Не запускается. Всё сломалось.». Дипломный руководитель не сможет ответить на на такой вопрос без дополнительных уточнений. Цените своё время и время других.
2. Откладывание диплом на последний момент.
3. Ожидание моментального ответа на свой вопрос. Дипломные руководители - работающие разработчики, которые занимаются, кроме преподавания, своими проектами. Их время ограничено, поэтому постарайтесь задавать правильные вопросы, чтобы получать быстрые ответы!
