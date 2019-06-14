# Tertium.Styleguide (HTML / CSS / JS)

## Представление

Структуру любой страницы можно представить как сетку, в которой расположены модули. Например, на странице могут быть модули: "Шапка" (header), модуль "Контент" (div.content), в котором находятся модули "Новости" (div.news) и "Авторизация" (div.auth), а в самом внизу располагается "Подвал" (footer).

Внутри модулей могут быть компоненты. Например, модуль "Шапка" состоит из компонентов "Логотип", "Главное Меню" и "Поиск".

Каждый компонент состоит из элементов. Например, в компоненте "Новости" есть списочный элемент (ul), который в свою очередь состоит из элементов (li).

Иерархию можно представить следующим образом:

```text
Модуль -> Компонент -> Элемент
```

### Элемент

> Элемент - это примитивный, предельно простой блок.

Создаём простой элемент:

```html
<img src="logo.svg" class="logo" />
```

Добавляем ему стиль:

```sass
.logo {}
```

Делаем обёртку - теперь с этим будет удобнее работать:

```html
<span class="logo">
  <img src="logo.svg" />
</span>
```

Теперь стиль будет выглядеть так:

```sass
.logo {
  img {}
}
```

Выглядит максимально просто, и не нужно усложнять этот вид дополнительными атрибутами. Если на странице несколько логотипов, можно уточнить:

```html
<span class="main-logo">
  <img src="logo.svg" />
</span>
```

Если этот элемент нужно отображать в разных ситуациях по-разному, хорошо использовать принцип компонента.

### Компонент

> Компонент - это блок из одного или нескольких элементов, который можно переиспользовать.

### Модификатор

Для того, чтобы внести какое-либо изменение в блок, достаточно добавить ему модификатор (состояние). Например, если мы хотим скрыть блок, достаточно добавить ему класс hide. Будет лучше, если модификатор будет отвечать на вопрос "Какой?". Соответственно, hide -> hidden.

```html
<span class="main-logo hidden">
  <img src="logo.svg" />
</span>
```

Логотип может быть нестандартного размера. Можно подсмотреть нотацию в популярных системах, таких как, например, Bootstrap. Попробуем показать логотип небольшого размера:

```html
<span class="main-logo xs">
  <img src="logo.svg" />
</span>
```

На другой странице логотип может быть очень большим:

```html
<span class="main-logo xl">
  <img src="logo.svg" />
</span>
```

Отобразить это в стилях очень просто:

```sass
.main-logo {
  img {}
  & .xs {}
  & .xl {}
}
```

Если нужно манипулировать элементом image в зависимости от размера:

```sass
.main-logo {
  img {}
  & .xs {
    img {}
  }
  & .xl {
    img {}
  }
}
```

Для того, чтобы производить изменения с логотипом может понадобится скрипт. Когда кода и логики становится много, удобно держать всю логику в одной директории. Названия файлов должны по возможности отражать название компонента.

```filesystem
components/logo/logo.js
components/logo/logo.png
components/logo/logo.sass
components/logo/logo.svg
```

Файл logo.js может быть классом компонента и содержать логику инстанса и соответствующих ему методов.

```javascript
class Logo {
  constructor(el) {
    this.el = el;
  }
  
  hide() {
    this.el.classList.add('hidden');
  }
  
  show() {
    this.el.classList.remove('hidden');
  }
}
```

Вызов компонента осуществляется в модуле.

### Модуль

> Модуль - это логически выделенный блок, состоящий из одного или несколько компонентов.

Например, семантический HTML-элемент header - это модуль.

```html
<header>
  <span class="main-logo">
    <img src="logo.svg" />
  </span>
</header>
```

Добавляем меню:

```html
<header>

  <span class="main-logo">
    <img src="logo.svg" />
  </span>

  <nav class="main-menu">
    <a href="/home/">Home</a>
    <a href="/contacts/">Contacts</a>
  </nav>

</header>
```

Инициализируем модуль Header и компонент Logo.

```javascript
import Logo from './components/logo/logo';

const header = {};
header.mainLogo = new Logo(document.querySelector('.main-logo'));
```

## Именование

Названия должны быть короткими и ёмкими. Все названия, кроме названий JS-классов, пишутся с маленькой буквы.

```html
<input type="text" name="name" />
```

Все пробелы заменяются на дефисы. Имена существительные всегда стоят последними.

```html
<input type="text" name="name" />
<input type="text" name="secret-name" />
<input type="text" name="secret-names" />
```

В JS используется camelCase:

```javascript
const secretNames = document.querySelector('input[name="secret-names"]');
```

Дополнительные атрибуты присваиваются только если в этом есть действительно необходимость. Чем проще и чище выглядит элемент, тем лучше.

```html
<input type="text" name="name" />
```

Иногда лучше конкретизировать, чтобы в стилях лучше понимать о каком элементе идёт речь:

```sass
input[name="name"] {}
```

CSS-класс присваивается только если он содержит какой-то общий для нескольких элементов стиль.

```html
<input type="text" name="name" class="rounded-borders" />
<textarea name="description" class="rounded-borders"></textarea>
```

```sass
.rounded-borders {
  border-radius: 6px;
}
```

По возможности надо избегать повторений:

```html
<form class="modern">
  <input type="text" name="name" />
  <textarea name="description"></textarea>
<form>
```

Можно оставить rounded-borders отдельным классом, чтобы потом переиспользовать.

```sass
.rounded-borders {
  border-radius: 6px;
}

form.modern {
  input, textarea {
    .rounded-borders;
  }
}
```

### Структура файлов и папок

```filesystem
app/
components/
modules/
```
