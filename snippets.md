Рабочие куски кода, проверенные на практике — можно копировать прямо в проект.

---

# 🎨 CSS Floating Label Input (без JavaScript)

> [!abstract] Описание > 
> Анимированное поле ввода в стиле Material Design. Подсказка (`label`) плавно поднимается наверх при фокусе или наличии введенного текста. Реализовано **исключительно на HTML и CSS** без использования JavaScript. 
> 

tags: 
- frontend/css 
- ui/components/input 
- snippets/code

html:
```html 
<div class="container"> 
	<div class="entryarea"> 
		<input type="text" id="username" required> 
		<label for="username" class="labelline">
			Enter your name
		</label> 
	</div> 
</div>
```
css:
```css
:root {
    /* === Цвета === */
    --bg-color: #1c2841;               /* Основной фон страницы и маскировки метки */
    --color-default: #f0ffff;          /* Цвет текста и рамки по умолчанию */
    --color-accent: #66ff00;           /* Акцентный цвет (при фокусе) */

    /* === Размеры компонента === */
    --container-width: 680px;           /* Ширина всей формы */
    --input-height: 80px;               /* Высота поля ввода */
    --input-font-size: 2.2em;          /* Размер шрифта в инпуте */
    --input-padding-x: 30px;           /* Горизонтальный отступ внутри инпута */
    --input-border-radius: 10px;       /* Закругление углов */
    --input-border-width-default: 2px; /* Толщина рамки в покое */
    --input-border-width-active: 4px;  /* Толщина рамки при фокусе */

    /* === Исходное состояние метки (Label) === */
    --label-font-size: 1.6em;          /* Размер шрифта метки */
    --label-padding-x: 25px;           /* Внутренний отступ метки */
    --label-margin-x: 20px;            /* Внешний отступ метки */

    /* === Активное состояние метки (при всплытии) === */
    --label-active-height: 30px;       /* Высота плашки подписи при всплытии */
    --label-active-padding-x: 12px;    /* Горизонтальный отступ всплывшей метки */
    --label-active-translate-x: -15px; /* Сдвиг по горизонтали */
    --label-active-translate-y: -16px; /* Сдвиг по вертикали (наверх) */
    --label-active-scale: 0.88;        /* Масштаб уменьшения текста */

    /* === Анимация и слои === */
    --transition-fast: 0.1s ease;
    --transition-normal: 0.2s ease;
    --z-index-floating: 1111;
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    display: flex;
    min-height: 100vh;
    justify-content: center;
    align-items: center;
    background: var(--bg-color);
}

.container {
    width: var(--container-width);
}

.entryarea {
    position: relative;
    height: var(--input-height);
    line-height: var(--input-height);
}

input {
    position: absolute;
    width: 100%;
    outline: none;
    font-size: var(--input-font-size);
    padding: 0 var(--input-padding-x);
    line-height: var(--input-height);
    border-radius: var(--input-border-radius);
    border: var(--input-border-width-default) solid var(--color-default);
    background-color: transparent;
    transition: var(--transition-fast);
    z-index: var(--z-index-floating);
}

.labelline {
    position: absolute;
    font-size: var(--label-font-size);
    color: var(--color-default);
    padding: 0 var(--label-padding-x);
    margin: 0 var(--label-margin-x);
    background-color: var(--bg-color);
    transition: var(--transition-normal);
}

input:focus,
input:valid {
    color: var(--color-accent);
    border: var(--input-border-width-active) solid var(--color-accent);
}

input:focus + .labelline,
input:valid + .labelline {
    color: var(--color-accent);
    height: var(--label-active-height);
    line-height: var(--label-active-height);
    padding: 0 var(--label-active-padding-x);
    transform: translate(var(--label-active-translate-x), var(--label-active-translate-y)) scale(var(--label-active-scale));
    z-index: var(--z-index-floating);
}
```

![[Pasted image 20260810110023.png|431]]