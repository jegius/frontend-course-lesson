# Работа с позиционированием

<div class="subtitle">
Управление расположением элементов в CSS
</div>

<ul v-click class="mt-16">
<li>Все типы позиционирования</li>
<li>Работу с z-index</li>
<li>Управление видимостью элементов</li>
<li>Практические примеры</li>
</ul>

---

# Свойство position

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="1">

## Основные значения

- **`static`** — по умолчанию
- **`relative`** — относительное
- **`absolute`** — абсолютное
- **`fixed`** — фиксированное
- **`sticky`** — липкое

</div>

<div v-click="2" class="code-demo">

```css
.element {
  position: relative;
  top: 20px;
  left: 30px;
}
```

<div class="highlight-box mt-4">
💡 <strong>Помни</strong>: top, left, right, bottom работают только с позиционированными элементами
</div>

</div>

</div>

---

# Static — поведение по умолчанию

<div class="grid grid-cols-2 gap-8 mt-8">

<div>

<div v-click="1">

```css
.box {
  position: static;
  /* top, left НЕ работают! */
  top: 100px; /* игнорируется */
}
```

</div>

<div v-click="2" class="highlight-box">
🎯 <strong>Ключевая идея</strong>: элемент остается в обычном потоке документа
</div>

</div>

<div v-click="3">

<div class="container-demo">
  <div class="position-box" style="position: static;">Static Box</div>
  <div class="position-box" style="position: static;">Static Box 2</div>
  <div class="position-box" style="position: static;">Static Box 3</div>
</div>

</div>

</div>

---

# Relative — смещение от исходной позиции

<div class="grid grid-cols-2 gap-8 mt-8">

<div>

<div v-click="1">

```css
.box {
  position: relative;
  top: 20px;
  left: 30px;
}
```

</div>

<div v-click="2" class="highlight-box">
✨ <strong>Особенность</strong>: другие элементы ведут себя так, будто элемент не двигался
</div>

<div v-click="3">

**Используется для:**
- Микросмещений
- Создания контекста для absolute

</div>

</div>

<div v-click="4">

<div class="container-demo">
  <div class="position-box" style="position: static;">Обычный</div>
  <div class="position-box" style="position: relative; top: 20px; left: 30px; background: #e74c3c;">Смещенный</div>
  <div class="position-box" style="position: static;">Обычный</div>
</div>

</div>

</div>

---

# Absolute — абсолютное позиционирование

<div class="grid grid-cols-2 gap-8 mt-6">

<div>

<div v-click="1">

```css
.parent {
  position: relative; /* контекст */
}

.child {
  position: absolute;
  top: 10px;
  right: 20px;
}
```

</div>

<div v-click="2" class="highlight-box">
🎯 <strong>Правило</strong>: позиционируется относительно ближайшего предка с position ≠ static
</div>

</div>

<div v-click="3">

<div class="container-demo">
  <div style="position: relative; height: 150px; background: #e8f5e8; color: #000">
    Родитель (relative)
    <div class="position-box" style="position: absolute; top: 10px; right: 10px; background: #e74c3c;">
      Absolute
    </div>
  </div>
</div>

</div>

</div>

<div v-click="4" class="mt-6">

<strong>Идеально для:</strong> модальных окон, всплывающих меню, тултипов

</div>

---

# Fixed и Sticky

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="1">

## Fixed — привязка к viewport

```css
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
```

<div class="highlight-box">
📌 <strong>Использование</strong>: фиксированные шапки, кнопки "наверх"
</div>

</div>

<div v-click="2">

## Sticky — гибридное решение

```css
.sidebar {
  position: sticky;
  top: 20px;
}
```

<div class="highlight-box">
🔄 <strong>Поведение</strong>: relative → при скролле → fixed
</div>

</div>

</div>

---

# Z-index — управление слоями

<div class="grid grid-cols-2 gap-8 mt-8">

<div>

<div v-click="1">

```css
.modal {
  position: fixed;
  z-index: 1000;
}

.overlay {
  position: fixed;
  z-index: 999;
}
```

</div>

<div v-click="2" class="highlight-box">
⚠️ <strong>Важно</strong>: z-index работает только с позиционированными элементами
</div>

</div>

</div>

---

# Управление видимостью

<div v-click="1">

<div class="comparison-table">

| Свойство | Видимость | Занимает место | События |
|----------|-----------|----------------|---------|
| `opacity: 0` | ❌ | ✅ | ✅ |
| `visibility: hidden` | ❌ | ✅ | ❌ |
| `display: none` | ❌ | ❌ | ❌ |

</div>

</div>

<div class="grid grid-cols-3 gap-6 mt-8">

<div v-click="2" class="code-demo">

### Opacity

```css
.fade {
  opacity: 0;
  transition: opacity 0.3s;
}
```
Для анимаций

</div>

<div v-click="3" class="code-demo">

### Visibility

```css
.hidden {
  visibility: hidden;
}
```
Сохраняет layout

</div>

<div v-click="4" class="code-demo">

### Display

```css
.invisible {
  display: none;
}
```
Полное удаление

</div>

</div>
---

# Ключевые выводы

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="1">

## ✅ Лучшие практики

- `relative` у родителя для контроля `absolute` детей
- `z-index` только с `position ≠ static`
- `opacity` для анимаций видимости
- `sticky` требует указания направления

</div>

<div v-click="2">

## ⚠️ Частые ошибки

- Забыть `position` при использовании `z-index`
- Не учитывать контекст для `absolute`
- Использовать `display: none` вместо `opacity` в анимациях

</div>

</div>

<div v-click="3" class="text-center mt-12">

### Готовы создавать сложные интерфейсы! 🚀

</div>

---
layout: center
---

<div class="subtitle">Анимации</div>

---

# Цель анимаций

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="1">

## 🎯 Зачем анимировать?

- Сделать интерфейс **живым**
- Показать **связь** между действиями
- Улучшить **восприятие** UX
- Добавить **эмоций** в продукт

</div>

<div v-click="2">

## 🚀 Ключевой принцип

<div class="highlight-box performance-good">
✅ <strong>Хорошая анимация</strong> не вызывает layout и paint. Она использует только композицию (compositing).
</div>

</div>

</div>

<div v-click="3" class="text-center mt-12">

### Анимируйте только `transform` и `opacity` для максимальной производительности

</div>

---

# Transition — плавные изменения

<div class="grid grid-cols-2 gap-8 mt-6">

<div>

<div v-click="1">

```css
.button {
  opacity: 0;
  transform: translateY(10px);
  transition: all 0.3s ease;
}

.button.visible {
  opacity: 1;
  transform: translateY(0);
}
```

</div>

<div v-click="2">

```js
// JavaScript
setTimeout(() => {
  button.classList.add('visible');
}, 1000);
```

</div>

</div>

<div v-click="3">

<div class="code-demo">
<button class="demo-button">Наведи на меня</button>
</div>

<div class="highlight-box">
💡 <strong>Transition</strong> — для изменений между двумя состояниями
</div>

</div>

</div>

---

# Производительность: хорошо vs плохо

<div class="grid grid-cols-2 gap-6 mt-6">

<div>

<div v-click="1" class="performance-bad code-demo">

### ❌ Медленные анимации

```css
/* Вызывает layout + paint */
.slide {
  transition: top 0.3s ease;
}
.slide.active {
  top: 100px;
}
```

```css
/* Дорогая перерисовка */
.box {
  transition: width 0.3s ease;
}
```

</div>

</div>

<div>

<div v-click="2" class="performance-good code-demo">

### ✅ Быстрые анимации

```css
/* Только композиция */
.slide {
  transition: transform 0.3s ease;
}
.slide.active {
  transform: translateY(100px);
}
```

```css
/* GPU-ускоренно */
.box {
  transition: transform 0.3s ease;
}
```

</div>

</div>

</div>

<div v-click="3" class="mt-6">

| Свойство | Layout? | Paint? | Производительность |
|----------|---------|--------|--------------------|
| `top`, `left`, `width` | ✅ | ✅ | ❌ Плохо |
| `color`, `background` | ❌ | ✅ | ⚠️ Средне |
| `transform`, `opacity` | ❌ | ❌ | ✅ Отлично |

</div>

---

# @keyframes — сложные анимации

<div v-click="1">

```css
@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateX(-100%);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.slide {
  animation: slideIn 0.5s ease-out forwards;
}
```

</div>

<div v-click="2" class="mt-6">

<div class="animation-demo slide-demo"></div>

</div>

<div v-click="3" class="highlight-box">
🎬 <strong>@keyframes</strong> — для сложных последовательностей с несколькими промежуточными состояниями
</div>

---

# Многоточечные анимации

<div v-click="1">

```css
@keyframes bounce {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
  100% {
    transform: translateY(0);
  }
}

.bouncy {
  animation: bounce 0.6s ease-in-out infinite alternate;
}
```

</div>

<div v-click="2" class="grid grid-cols-3 gap-8 mt-8">

<div class="code-demo">

### Easing functions

```css
ease-out /* быстро → медленно */
ease-in  /* медленно → быстро */
cubic-bezier(0.4, 0, 0.2, 1)
```

</div>

<div class="code-demo">

### Timing

```css
duration: 0.3s  /* длительность */
delay: 0.1s     /* задержка */
iteration-count: infinite
```

</div>

<div class="code-demo">

### Fill modes

```css
forwards  /* остается в конце */
backwards /* стартует с начала */
both      /* и то, и другое */
```

</div>

</div>

---

## Оптимизация для GPU

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="1">

## will-change

```css
.slide {
  will-change: transform, opacity;
  transition: all 0.3s ease;
}

/* После анимации */
.slide.animated {
  will-change: auto;
}
```

<div class="highlight-box">
⚡ Создает отдельный слой в GPU
</div>

</div>

<div v-click="2">

## transform3d hack

```css
.slide {
  /* Принудительно поднимает на слой */
  transform: translateZ(0);
  /* или */
  transform: translate3d(0, 0, 0);
}
```

<div class="highlight-box">
🎯 Используй осторожно — много слоев = много памяти
</div>

</div>

</div>

---

# Лучшие практики анимаций

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="1">

## ✅ Делай

- Анимируй `transform` и `opacity`
- Используй `cubic-bezier` для естественности
- Добавляй `will-change` для критичных анимаций
- Длительность 200-500ms для UI
- Тестируй в DevTools Performance

</div>

<div v-click="2">

## ❌ Не делай

- Анимируй `width`, `height`, `top`, `left`
- Используй слишком долгие анимации (>500ms)
- Забывай убирать `will-change` после анимации
- Анимируй одновременно много элементов
- Используй `ease-in` для появлений

</div>

</div>

<div v-click="3" class="highlight-box mt-8">
🎯 <strong>Цель</strong>: анимация должна проходить только через <strong>Compositing</strong> фазу — тогда она будет максимально плавной
</div>

---

# Отладка производительности

<div v-click="1">

## Chrome DevTools

1. **Performance** tab → запись
2. Ищи желтые и красные блоки (layout/paint)
3. **Rendering** tab → Paint flashing
4. **Layers** tab → просмотр GPU слоев

</div>

<div v-click="2" class="mt-8">

```css
/* Идеальная анимация */
.perfect-animation {
  transform: translateX(0);
  opacity: 1;
  transition: transform 0.3s ease-out, opacity 0.3s ease-out;
  will-change: transform, opacity;
}
```

<div class="highlight-box performance-good">
✅ Эта анимация будет работать на <strong>GPU</strong> и не заблокирует основной поток
</div>

</div>

---

# Заключение

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="1">

## Что изучили

- **Transition** vs **@keyframes**
- Производительные свойства
- GPU-оптимизация
- Практические паттерны

</div>

<div v-click="2">

## Ключевые правила

1. **Transform + Opacity** = быстро
2. **will-change** для критичных анимаций
3. **300-500ms** — оптимальная длительность
4. **cubic-bezier** для естественности

</div>

</div>

<div v-click="3" class="text-center mt-12">

### Теперь ваши анимации будут плавными! ✨

</div>

---
layout: center
---

# Готовы к Critical Rendering Path?

<div class="subtitle">
Узнаем, как браузер рендерит страницы
</div>

---

# Critical Rendering Path

<div class="subtitle">
Как браузер превращает код в пиксели на экране
</div>

<div v-click class="mt-16">

- 6 ключевых фаз рендеринга
- Что такое layout thrashing
- Как оптимизировать производительность
- Метрики производительности

</div>

---

# Что такое Critical Rendering Path?

<div v-click="1">

<div class="highlight-box">
🎯 Определение: Последовательность шагов, которые браузер выполняет для превращения HTML, CSS и JS в видимые пиксели на экране
</div>

</div>

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="2">

## 🚀 Зачем это знать?

- Понимать, **где тормозит** ваш сайт
- Оптимизировать **время загрузки**
- Избежать **layout thrashing**
- Создавать **быстрые** веб-приложения

</div>

<div v-click="3">

## 📊 Ключевые метрики

- **FCP** — First Contentful Paint
- **LCP** — Largest Contentful Paint
- **CLS** — Cumulative Layout Shift
- **FID** — First Input Delay

</div>

</div>

---

# 6 фаз рендеринга — конвейер браузера

<div class="phase-container">

<div v-click="1" class="pipeline-step">
<strong>1. HTML Parsing</strong><br>
HTML → DOM Tree
</div>

<div v-click="1" class="pipeline-arrow">↓</div>

<div v-click="2" class="pipeline-step">
<strong>2. CSS Parsing</strong><br>
CSS → CSSOM Tree
</div>

<div v-click="2" class="pipeline-arrow">↓</div>

<div v-click="3" class="pipeline-step">
<strong>3. Render Tree</strong><br>
DOM + CSSOM → Render Tree
</div>

<div v-click="3" class="pipeline-arrow">↓</div>

<div v-click="4" class="pipeline-step">
<strong>4. Layout (Reflow)</strong><br>
Расчет геометрии элементов
</div>

<div v-click="4" class="pipeline-arrow">↓</div>

<div v-click="5" class="pipeline-step">
<strong>5. Paint</strong><br>
Отрисовка пикселей
</div>

<div v-click="5" class="pipeline-arrow">↓</div>

<div v-click="6" class="pipeline-step">
<strong>6. Composite</strong><br>
Наложение слоев
</div>

</div>

---

# Фаза 1-2: Parsing HTML & CSS

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click="1">

## HTML → DOM

```html
<!DOCTYPE html>
<html>
  <head>
    <link href="style.css" rel="stylesheet">
  </head>
  <body>
    <h1>Привет!</h1>
    <p>Это параграф</p>
  </body>
</html>
```

<div class="highlight-box">
🌳 Браузер строит <strong>дерево DOM</strong>
</div>

</div>

<div v-click="2">

## CSS → CSSOM

```css
h1 {
  color: blue;
  font-size: 2rem;
}

p {
  margin: 1rem 0;
  line-height: 1.5;
}
```

<div class="warning-box">
⚠️ <strong>CSS блокирует рендеринг</strong> — даже неиспользуемый CSS!
</div>

</div>

</div>

<div v-click="3" class="mt-8">

### Важно: JavaScript может блокировать parsing

```html
<script src="app.js"></script> <!-- Блокирует parsing -->
<script src="app.js" defer></script> <!-- Не блокирует -->
```

</div>

---

# Фаза 3: Render Tree

<div v-click="1">

<div class="highlight-box">
🌲 <strong>Render Tree</strong> = DOM + CSSOM, но только <strong>видимые</strong> элементы
</div>

</div>

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click="2">

## Что попадает в Render Tree

```html
<div>Видимый текст</div>
<p>Тоже видимый</p>
<img src="photo.jpg" alt="Фото">
```

✅ **Включается** в дерево отрисовки

</div>

<div v-click="3">

## Что НЕ попадает

```html
<div style="display: none">Скрытый</div>
<head>...</head>
<script>...</script>
```

❌ **Исключается** из дерева отрисовки

</div>

</div>

<div v-click="4" class="mt-8">

```css
.element {
  visibility: hidden; /* В дереве ЕСТЬ */
  opacity: 0;         /* В дереве ЕСТЬ */
  display: none;      /* В дереве НЕТ */
}
```

</div>

---

# Фаза 4: Layout (Reflow)

<div v-click="1">

<div class="highlight-box">
📐 <strong>Layout</strong> — браузер рассчитывает <strong>точные размеры и позицию</strong> каждого элемента
</div>

</div>

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click="2">

## Что вызывает Layout

```js
// Изменение геометрии
element.style.width = '300px';
element.style.padding = '20px';
element.style.fontSize = '18px';

// Чтение геометрических свойств
const height = element.offsetHeight;
const width = element.getBoundingClientRect().width;
```

</div>

<div v-click="3">

## Layout Thrashing ⚠️

```js
// ПЛОХО: каждая итерация = reflow
for (let i = 0; i < items.length; i++) {
  items[i].style.left = items[i].offsetLeft + 10 + 'px';
}

// ХОРОШО: сначала читаем, потом пишем
const positions = items.map(item => item.offsetLeft);
items.forEach((item, i) => {
  item.style.left = positions[i] + 10 + 'px';
});
```

</div>

</div>

<div v-click="4" class="warning-box">
⚠️ <strong>Layout Thrashing</strong> — циклы чтения/записи геометрии, убивающие производительность
</div>

---

# Фаза 5: Paint

<div v-click="1">

<div class="highlight-box">
🎨 <strong>Paint</strong> — браузер рисует пиксели: цвета, текст, тени, границы
</div>

</div>

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click="2">

## Что вызывает Paint

```css
.element {
  color: red;           /* Paint */
  background: blue;     /* Paint */
  box-shadow: 0 2px 4px rgba(0,0,0,0.1); /* Paint */
  border-radius: 8px;   /* Paint */
}
```

<div class="warning-box">
⚠️ Paint может быть <strong>очень дорогим</strong>, особенно для больших областей
</div>

</div>

<div v-click="3">

## Что НЕ вызывает Paint

```css
.element {
  transform: translateX(100px); /* Только Composite */
  opacity: 0.5;                 /* Только Composite */
}
```

<div class="success-box">
✅ <strong>Transform</strong> и <strong>opacity</strong> — самые быстрые для анимации
</div>

</div>

</div>

---

# Фаза 6: Composite

<div v-click="1">

<div class="highlight-box">
🧩 <strong>Composite</strong> — браузер объединяет все слои в финальное изображение (часто на GPU)
</div>

</div>

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click="2">

## Создание слоев

```css
.layer {
  /* Поднимает элемент на отдельный слой */
  will-change: transform;
  /* или */
  transform: translateZ(0);
  /* или */
  opacity: 0.99;
}
```

</div>

<div v-click="3">

## Преимущества слоев

- 🚀 **Анимации** `transform`/`opacity` — на GPU
- ⚡ **Независимые** изменения без влияния на другие элементы
- 🎯 **Максимальная производительность**

</div>

</div>

<div v-click="4" class="warning-box">
⚠️ <strong>Осторожно</strong> слишком много слоев = высокое потребление памяти GPU
</div>

---

# Измерение производительности

<div class="metrics-grid">

<div v-click="1" class="metric-card">
<strong>FCP</strong><br>
First Contentful Paint<br>
<small>Когда появился первый контент</small>
</div>

<div v-click="2" class="metric-card">
<strong>LCP</strong><br>
Largest Contentful Paint<br>
<small>Самый большой элемент загружен</small>
</div>

<div v-click="3" class="metric-card">
<strong>CLS</strong><br>
Cumulative Layout Shift<br>
<small>Нестабильность макета</small>
</div>

<div v-click="4" class="metric-card">
<strong>FID</strong><br>
First Input Delay<br>
<small>Задержка первого взаимодействия</small>
</div>

</div>

<div v-click="5" class="mt-8">

## Инструменты для измерения

- **Chrome DevTools** → Performance tab

</div>

---

# Как избежать Layout Thrashing

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click="1">

## ❌ Плохие практики

```js
// Принудительный синхронный layout
element.style.padding = '10px';
console.log(element.offsetWidth); // → Reflow!

// Циклы с чтением геометрии
for (let el of elements) {
  el.style.top = el.offsetTop + 10 + 'px';
}
```

</div>

<div v-click="2">

## ✅ Хорошие практики

```js
// Батчинг операций
requestAnimationFrame(() => {
  elements.forEach(el => {
    el.style.transform = `translateY(10px)`;
  });
});

// Использование DocumentFragment
const fragment = document.createDocumentFragment();
// добавляем элементы во fragment
container.appendChild(fragment); // один reflow
```

</div>

</div>

<div v-click="3" class="success-box mt-8">
✅ <strong>Золотое правило</strong>: сначала все чтения, потом все записи
</div>

---

# Оптимизация Critical Rendering Path

<div v-click="1">

## 1. Минимизируйте блокировку рендеринга

```html
<!-- Критический CSS inline -->
<style>
  body { font-family: sans-serif; margin: 0; }
  .header { background: blue; color: white; }
</style>

<!-- Некритический CSS отложенно -->
<link rel="preload" href="styles.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
```

</div>

<div v-click="2">

## 2. Оптимизируйте JavaScript

```html
<script src="critical.js"></script>
<script src="non-critical.js" defer></script>
<script src="analytics.js" async></script>
```

</div>

<div v-click="3">

## 3. Предзагрузка ресурсов

```html
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>
<link rel="preload" href="hero.jpg" as="image">
```

</div>

---

# Динамические изменения DOM

<div v-click="1">

<div class="highlight-box">
💡 При изменениях через JavaScript браузер проходит <strong>только нужные фазы</strong> CRP, не весь путь заново
</div>

</div>

<div class="grid grid-cols-3 gap-4 mt-8">

<div v-click="2" class="pipeline-step">
<strong>Layout</strong><br>
<small>Если изменилась геометрия</small>
<code>width, height, padding</code>
</div>

<div v-click="3" class="pipeline-step">
<strong>Paint</strong><br>
<small>Если изменился внешний вид</small>
<code>color, background, shadow</code>
</div>

<div v-click="4" class="pipeline-step">
<strong>Composite</strong><br>
<small>Если изменились слои</small>
<code>transform, opacity</code>
</div>

</div>

<div v-click="5" class="mt-8">

```js
// Layout + Paint + Composite
element.style.width = '300px';

// Paint + Composite
element.style.color = 'red';

// Только Composite (самое быстрое!)
element.style.transform = 'translateX(100px)';
```

</div>

---

# Практические советы

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click="1">

## 🚀 Для быстрой загрузки

- Инлайните критический CSS
- Используйте `defer` для JS
- Оптимизируйте изображения
- Минифицируйте ресурсы
- Используйте CDN

</div>

<div v-click="2">

## ⚡ Для плавной работы

- Анимируйте только `transform`/`opacity`
- Избегайте layout thrashing
- Используйте `will-change` осторожно
- Группируйте DOM-изменения
- Используйте `requestAnimationFrame`

</div>

</div>

<div v-click="3" class="highlight-box mt-8">
🎯 <strong>Цель</strong>: минимизировать время до <strong>First Contentful Paint</strong> и избежать <strong>layout thrashing</strong>
</div>

---

# Critical Rendering Path

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="1">

## Что изучили

- **6 фаз** рендеринга браузера
- Причины **layout thrashing**
- **Метрики** производительности
- Способы **оптимизации**

</div>

<div v-click="2">

## Ключевые выводы

1. **HTML/CSS** блокируют рендеринг
2. **Layout** — самая дорогая операция
3. **Transform/Opacity** — максимально быстрые
4. **Измеряйте** производительность в DevTools

</div>

</div>

<div v-click="3" class="text-center mt-12">

### Теперь вы понимаете, как работает браузер! 🧠

</div>

---
# SPA vs MPA

<div class="subtitle">
Архитектурные подходы к построению веб-приложений
</div>

<div v-click class="mt-16">

**За 15 минут разберем:**
- Что такое MPA и SPA
- Преимущества и недостатки каждого подхода
- Роутинг на стороне клиента
- Современные гибридные решения

</div>
---

<div class="subtitle">Single vs Multi Page Applications</div>

---

# Введение в архитектуры

<div v-click="1">

<div class="highlight-box">
🎯 <strong>Ключевой вопрос</strong>: Как пользователь переходит между страницами вашего приложения?
</div>

</div>

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="2" class="mpa-box architecture-box">

## MPA
**Multi Page Application**

Каждый переход = новая страница
Полная перезагрузка браузера

</div>

<div v-click="3" class="spa-box architecture-box">

## SPA
**Single Page Application**

Один HTML-файл
JavaScript управляет содержимым

</div>

</div>

<div v-click="4" class="text-center mt-8">

### Оба подхода имеют свое место в современной веб-разработке

</div>

---

# MPA — традиционный подход

<div v-click="1">

<div class="highlight-box">
📄 <strong>MPA</strong> каждая страница — отдельный HTML-файл или генерируется сервером
</div>

</div>

<div v-click="2" class="mt-8">

## Как работает MPA

<div class="text-center mt-4">
<div class="flow-step">example.com</div>
<span class="flow-arrow">→</span>
<div class="flow-step">example.com/catalog</div>
<span class="flow-arrow">→</span>
<div class="flow-step">example.com/product/123</div>
</div>

<div class="text-center mt-4 text-sm text-gray-600">
Каждый переход = полная перезагрузка страницы
</div>

</div>

---

<div class="grid grid-cols-2 gap-8 mt-8">

<div>

## Что происходит при клике

1. Запрос к серверу
2. Сервер возвращает новый HTML
3. Браузер полностью перезагружает страницу
4. Новая страница отображается

</div>

<div v-click="1">

## Примеры MPA

- Блоги и новостные сайты
- Корпоративные сайты
- E-commerce (частично)
- Википедия
- Большинство сайтов 2000-х

</div>

</div>

---

# MPA: плюсы и минусы

<div class="pros-cons-grid">

<div v-click="1" class="pros-box">

## ✅ Преимущества

- **Простота разработки** — привычные технологии
- **Отличное SEO** — поисковики легко индексируют
- **Работает без JS** — доступность из коробки
- **Стабильность** — каждая страница изолирована
- **Быстрая первичная загрузка** каждой страницы

</div>

<div v-click="2" class="cons-box">

## ❌ Недостатки

- **Медленная навигация** — полная перезагрузка
- **Повторная загрузка** ресурсов (CSS, JS, изображения)
- **Нет состояния** между страницами
- **Ощущение "сайта"**, не приложения
- **Избыточная передача** данных

</div>

</div>

<div v-click="3" class="highlight-box mt-8">
💡 <strong>Идеально для</strong>: контентных сайтов, блогов, лендингов, простых корпоративных сайтов
</div>

---

# SPA — современный подход

<div v-click="1">

<div class="highlight-box">
⚡ <strong>SPA</strong>: одна HTML-страница, JavaScript динамически меняет содержимое
</div>

</div>

<div v-click="2" class="mt-8">

## Как работает SPA

<div class="text-center">
<div class="flow-step">Загрузка app.html + app.js</div>
</div>

<div class="text-center mt-4">
<div class="flow-step">Показ /home</div>
<span class="flow-arrow">→</span>
<div class="flow-step">Показ /profile</div>
<span class="flow-arrow">→</span>
<div class="flow-step">Показ /settings</div>
</div>

<div class="text-center mt-4 text-sm text-gray-600">
JavaScript меняет содержимое без перезагрузки
</div>

</div>

---

<div class="mt-8">

## Что происходит при "переходе"

1. JavaScript перехватывает клик
2. Обновляет URL в адресной строке
3. Загружает данные через API (если нужно)
4. Обновляет нужную часть DOM

</div>

---

# SPA: плюсы и минусы

<div class="pros-cons-grid">

<div v-click="1" class="pros-box">

## ✅ Преимущества

- **Быстрая навигация** после загрузки
- **Ощущение приложения** — как нативное
- **Богатые интерактивные** возможности
- **Современные фреймворки** (React, Vue, Angular)
- **Состояние** сохраняется между "страницами"

</div>

<div v-click="2" class="cons-box">

## ❌ Недостатки

- **Медленная первичная** загрузка (большой JS)
- **Сложности с SEO** (но решаемо)
- **Не работает без JavaScript**
- **Сложность разработки** и отладки
- **Управление состоянием**

</div>

</div>

<div v-click="3" class="highlight-box mt-8">
💡 <strong>Идеально для</strong>: веб-приложений, админок, CRM, почтовых клиентов, социальных сетей
</div>

---

# Сравнение MPA vs SPA

<div v-click="1">

<div class="comparison-table">

| Критерий | MPA | SPA |
|----------|-----|-----|
| **Переходы между страницами** | Полная перезагрузка | Нет перезагрузки |
| **Первичная загрузка** | Быстро (маленький HTML) | Медленнее (JS-фреймворк) |
| **Навигация** | Медленная | Очень быстрая |
| **SEO** | Отлично | Требует усилий (SSR) |
| **Разработка** | Простая | Сложная |
| **UX** | Как сайт | Как приложение |
| **Работа без JS** | ✅ | ❌ |

</div>

</div>

---
layout: center
---

<div class="mt-6 text-center">

### Выбор зависит от типа проекта и требований

</div>

---

# Проблема: навигация в SPA

<div v-click="1">

<div class="highlight-box">
🤔 <strong>Вопрос</strong>: Как в одном HTML-файле показывать разные "страницы" и менять URL?
</div>

</div>

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="2">

## Что нужно для SPA-навигации

- Перехват кликов по ссылкам
- Изменение URL **без запроса к серверу**
- Отображение нужного компонента
- Поддержка кнопок "Назад/Вперед"
- Возможность поделиться ссылкой

</div>

<div v-click="3">

## URL должны работать

<div class="url-example">myapp.com/dashboard</div>
<div class="url-example mt-2">myapp.com/profile/john</div>
<div class="url-example mt-2">myapp.com/settings</div>

Каждый URL должен показывать соответствующую "страницу"

</div>

</div>

<div v-click="4" class="highlight-box mt-8">
💡 Для решения этих проблем нужен <strong>Client-Side Routing</strong> (роутинг на стороне клиента)
</div>

---

# Client-Side Routing

<div v-click="1">

<div class="highlight-box">
🛣️ <strong>Client-Side Router:</strong> JavaScript-библиотека, которая управляет навигацией без перезагрузки страницы
</div>

</div>

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click="2">

## Как работает роутер

```js
// Псевдокод
const routes = {
  '/home': HomeComponent,
  '/profile': ProfileComponent,
  '/settings': SettingsComponent
};

function navigate(path) {
  history.pushState(null, '', path);
  renderComponent(routes[path]);
}
```

</div>

<div v-click="3">

## History API

```js
// Изменить URL без перезагрузки
history.pushState(state, title, url);

// Слушать кнопки назад/вперед
window.addEventListener('popstate', (event) => {
  handleRouteChange();
});
```

</div>

</div>

---

<div class="mt-8">

## Популярные роутеры

- **React Router** (React)
- **Vue Router** (Vue.js)
- **Angular Router** (Angular)

</div>

---

# Пример простого роутера

<div v-click="1">

```js
class SimpleRouter {
  constructor() {
    this.routes = {};
    window.addEventListener('popstate', () => this.handleRoute());
    this.handleRoute();
  }

  addRoute(path, handler) {
    this.routes[path] = handler;
  }

  navigate(path) {
    history.pushState({}, '', path);
    this.handleRoute();
  }

  handleRoute() {
    const path = window.location.pathname;
    const handler = this.routes[path] || this.routes['/404'];
    if (handler) handler();
  }
}
```
</div>

--- 

<div v-click="1">

```js
// Использование
const router = new SimpleRouter();
router.addRoute('/home', () => showHome());
router.addRoute('/about', () => showAbout());
router.addRoute('/404', () => showNotFound());
```

</div>

---

# Практический пример навигации

<div v-click="1">

```html
<!-- HTML -->
<nav>
  <a href="/home" onclick="navigate('/home'); return false;">Главная</a>
  <a href="/profile" onclick="navigate('/profile'); return false;">Профиль</a>
  <a href="/settings" onclick="navigate('/settings'); return false;">Настройки</a>
</nav>

<div id="app">
  <!-- Сюда рендерятся компоненты -->
</div>
```

</div>

---

<div v-click="1">

```js
function navigate(path) {
  // Меняем URL
  history.pushState({}, '', path);

  // Рендерим нужный компонент
  const app = document.getElementById('app');

  if (path === '/home') {
    app.innerHTML = '<h1>Главная страница</h1><p>Добро пожаловать!</p>';
  } else if (path === '/profile') {
    app.innerHTML = '<h1>Профиль</h1><p>Ваши данные</p>';
  } else if (path === '/settings') {
    app.innerHTML = '<h1>Настройки</h1><p>Конфигурация</p>';
  }
}
```

</div>

---

# Современные гибридные подходы

<div v-click="1">

<div class="highlight-box">
🔄 <strong>Тренд</strong>: границы между SPA и MPA стираются, появляются гибридные решения
</div>

</div>

<div class="grid grid-cols-2 gap-6 mt-8">

<div v-click="2">

## SSR — Server-Side Rendering

```js
// Next.js, Nuxt.js, SvelteKit
// Рендер SPA на сервере для SEO
```

- **Первая загрузка**: HTML с сервера (быстро + SEO)
- **Навигация**: как SPA (быстро)

</div>

<div v-click="3">

## SSG — Static Site Generation

```js
// Gatsby, Next.js, Nuxt.js
// Генерация статических HTML файлов
```

- **Build time**: генерирует HTML для всех страниц
- **Runtime**: ведет себя как SPA

</div>

</div>

<div v-click="4" class="mt-8">

## Islands Architecture

```js
// Astro, Fresh
// Интерактивные "острова" в статическом HTML
```

- **Основа**: статический HTML (быстро)
- **Острова**: React/Vue компоненты по необходимости

</div>

---

# Выбор архитектуры

<div class="grid grid-cols-2 gap-8 mt-6">

<div v-click="1">

## Выбирайте MPA, если:

- 📰 **Контентный сайт** (блог, новости)
- 🛍️ **E-commerce** с простой навигацией
- 🏢 **Корпоративный сайт**
- 📄 **Лендинги**
- 🔍 **SEO критично** с первого дня
- 👥 **Команда небольшая** или без опыта SPA

</div>

<div v-click="2">

## Выбирайте SPA, если:

- 💼 **Веб-приложение** (админка, CRM)
- 📧 **Интерактивный сервис** (почта, чат)
- 🎮 **Богатый UI** с анимациями
- 📱 **Mobile-first** подход
- 👨‍💻 **Команда опытная** в фронтенде
- ⚡ **UX важнее** первичной загрузки

</div>

</div>

<div v-click="3" class="highlight-box mt-8">
💡 <strong>Современное решение:</strong> рассмотрите **SSR/SSG** фреймворки для получения преимуществ обоих подходов
</div>

---

# Эволюция веб-архитектур

<div v-click="1" class="text-center">

<div class="flow-step">Статические HTML страницы</div>
<div class="mt-2">↓</div>
<div class="flow-step">Серверная генерация (PHP, ASP)</div>
<div class="mt-2">↓</div>
<div class="flow-step">AJAX + частичные обновления</div>
<div class="mt-2">↓</div>
<div class="flow-step">SPA фреймворки</div>
<div class="mt-2">↓</div>
<div class="flow-step">Гибридные подходы (SSR, SSG, Islands)</div>

</div>

<div v-click="2" class="highlight-box mt-8">
🚀 <strong>Настоящее:</strong> Universal/Isomorphic приложения, которые работают везде одинаково
</div>

---

# Заключение

<div class="grid grid-cols-2 gap-8 mt-8">

<div v-click="1">

## Что изучили

- **MPA** — традиционные многостраничники
- **SPA** — одностраничные приложения
- **Client-Side Routing** — навигация без перезагрузки
- **Гибридные подходы** — лучшее из двух миров

</div>

<div v-click="2">

## Ключевые выводы

1. **Выбор** зависит от типа проекта
2. **SPA** требует роутинга для навигации
3. **Гибридные** решения набирают популярность
4. **Нет универсального** ответа — всё зависит от задач

</div>

</div>

<div v-click="3" class="text-center mt-12">

### Теперь вы можете обоснованно выбирать архитектуру! 🎯

</div>

