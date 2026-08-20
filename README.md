# HTML / CSS — структура проекта

Учебный шаблон: HTML по страницам, CSS по слоям и компонентам.  
Learning template: HTML by pages, CSS by layers and components.  
Ուսումնական շաբլոն․ HTML ըստ էջերի, CSS ըստ շերտերի և կոմպոնենտների։

---

## Русский

### Дерево файлов

```text
main/
├── README.md
├── index.html                 ← главная страница (корень сайта)
├── pages/                     ← все остальные HTML-страницы
│   ├── about.html
│   └── contact.html
├── css/
│   ├── main.css               ← единственный файл, который подключает HTML
│   ├── base/                  ← глобальное: токены, reset, media
│   │   ├── variables.css
│   │   ├── global.css
│   │   └── media.css
│   ├── layout/                ← каркас страницы
│   │   ├── header.css
│   │   └── footer.css
│   ├── components/            ← переиспользуемые блоки (1 компонент = 1 файл)
│   │   ├── button.css
│   │   ├── input.css
│   │   └── card.css
│   └── pages/                 ← стили конкретной страницы
│       ├── home.css
│       ├── about.css
│       └── contact.css
└── assets/
    ├── images/
    ├── fonts/
    └── icons/
```

### Правила HTML

1. `index.html` лежит в корне — это точка входа.
2. Остальные страницы — только в `pages/`. Не складывайте HTML в `css/` или `assets/`.
3. В `<head>` подключайте **только** `css/main.css`.
   - с корня: `href="css/main.css"`
   - из `pages/`: `href="../css/main.css"`
4. Повторяющиеся блоки (`header`, `footer`, `nav`) копируйте с теми же классами на каждой странице.
5. Классы по BEM: блок `card`, элемент `card__title`, модификатор `btn--primary`.

### Правила CSS

Порядок импорта в `main.css` фиксированный:

1. **variables** — цвета, шрифты, отступы, радиусы (`--color-primary`, `--space-md` …)
2. **global** — reset, `body`, заголовки, `.container`
3. **layout** — `header`, `footer`
4. **components** — `button`, `input`, `card`
5. **pages** — уникальные стили страницы
6. **media** — breakpoints в конце, чтобы перекрывать предыдущие правила

| Файл | Зачем |
|------|--------|
| `base/variables.css` | Все дизайн-токены. Меняете тему — правите только этот файл. |
| `base/global.css` | Reset и базовые теги. Без классов компонентов. |
| `base/media.css` | `@media` (640 / 768 / 1024 / 1280). Mobile first. |
| `layout/header.css` | Шапка и навигация. |
| `layout/footer.css` | Подвал. |
| `components/button.css` | `.btn`, `.btn--primary`, `.btn--secondary`, `.btn--lg` |
| `components/input.css` | `.form`, `.field`, `.input`, `.textarea` |
| `components/card.css` | `.cards`, `.card`, `.card__body` |
| `pages/*.css` | Только то, что есть на одной странице. |

**Один компонент — один файл.** Не кладите стили кнопки в `card.css`.  
Новый блок (например модальное окно): `css/components/modal.css` → `@import` в `main.css`.

### Как открыть

Откройте `index.html` в браузере или поднимите локальный сервер из папки проекта.

---

## English

### File tree

```text
main/
├── README.md
├── index.html                 ← home page (site root)
├── pages/                     ← all other HTML pages
│   ├── about.html
│   └── contact.html
├── css/
│   ├── main.css               ← the only stylesheet HTML links to
│   ├── base/                  ← tokens, reset, media
│   │   ├── variables.css
│   │   ├── global.css
│   │   └── media.css
│   ├── layout/                ← page chrome
│   │   ├── header.css
│   │   └── footer.css
│   ├── components/            ← reusable blocks (1 component = 1 file)
│   │   ├── button.css
│   │   ├── input.css
│   │   └── card.css
│   └── pages/                 ← page-specific styles
│       ├── home.css
│       ├── about.css
│       └── contact.css
└── assets/
    ├── images/
    ├── fonts/
    └── icons/
```

### HTML rules

1. Keep `index.html` at the project root — that is the entry page.
2. Put every other page in `pages/`. Do not mix HTML into `css/` or `assets/`.
3. Link **only** `css/main.css` in `<head>`.
   - from root: `href="css/main.css"`
   - from `pages/`: `href="../css/main.css"`
4. Reuse the same `header` / `footer` / `nav` markup and class names on every page.
5. Use BEM: block `card`, element `card__title`, modifier `btn--primary`.

### CSS rules

Import order in `main.css` is fixed:

1. **variables** — colors, type, spacing, radii
2. **global** — reset, `body`, headings, `.container`
3. **layout** — `header`, `footer`
4. **components** — `button`, `input`, `card`
5. **pages** — styles unique to one page
6. **media** — breakpoints last, so they can override

| File | Role |
|------|------|
| `base/variables.css` | Design tokens. Change the theme here only. |
| `base/global.css` | Reset and base tags. No component classes. |
| `base/media.css` | `@media` (640 / 768 / 1024 / 1280). Mobile first. |
| `layout/header.css` | Header and nav. |
| `layout/footer.css` | Footer. |
| `components/button.css` | `.btn` and variants |
| `components/input.css` | `.form`, `.field`, `.input`, `.textarea` |
| `components/card.css` | `.cards`, `.card` |
| `pages/*.css` | Styles that exist on one page only. |

**One component, one file.** Do not put button styles in `card.css`.  
New block (e.g. modal): add `css/components/modal.css` and `@import` it in `main.css`.

### How to open

Open `index.html` in a browser, or start a local server from the project folder.

---

## Հայերեն

### Ֆայլերի ծառ

```text
main/
├── README.md
├── index.html                 ← գլխավոր էջ (կայքի արմատ)
├── pages/                     ← մնացած HTML էջերը
│   ├── about.html
│   └── contact.html
├── css/
│   ├── main.css               ← միակ ֆայլը, որ HTML-ը կապում է
│   ├── base/                  ← տոկեններ, reset, media
│   │   ├── variables.css
│   │   ├── global.css
│   │   └── media.css
│   ├── layout/                ← էջի կմախք
│   │   ├── header.css
│   │   └── footer.css
│   ├── components/            ← կրկնվող բլոկներ (1 կոմպոնենտ = 1 ֆայլ)
│   │   ├── button.css
│   │   ├── input.css
│   │   └── card.css
│   └── pages/                 ← կոնկրետ էջի ոճեր
│       ├── home.css
│       ├── about.css
│       └── contact.css
└── assets/
    ├── images/
    ├── fonts/
    └── icons/
```

### HTML կանոններ

1. `index.html`-ը պահեք արմատում — դա մուտքի էջն է։
2. Մնացած էջերը միայն `pages/`-ում։ HTML մի դրեք `css/` կամ `assets/` մեջ։
3. `<head>`-ում կապեք **միայն** `css/main.css`։
   - արմատից՝ `href="css/main.css"`
   - `pages/`-ից՝ `href="../css/main.css"`
4. `header`, `footer`, `nav` նույն class-ներով կրկնեք յուրաքանչյուր էջում։
5. BEM՝ բլոկ `card`, էլեմենտ `card__title`, մոդիֆիկատոր `btn--primary`։

### CSS կանոններ

`main.css`-ի import-ի հերթականությունը ֆիքսված է.

1. **variables** — գույներ, տառատեսակ, հեռավորություններ
2. **global** — reset, `body`, վերնագրեր, `.container`
3. **layout** — `header`, `footer`
4. **components** — `button`, `input`, `card`
5. **pages** — միայն մեկ էջի ոճեր
6. **media** — breakpoint-ները վերջում, որպեսզի վերագրեն նախորդ կանոնները

| Ֆայլ | Նշանակություն |
|------|----------------|
| `base/variables.css` | Դիզայնի տոկեններ։ Թեման փոխում եք միայն այստեղ։ |
| `base/global.css` | Reset և բազային թեգեր։ Առանց կոմպոնենտների class-ների։ |
| `base/media.css` | `@media` (640 / 768 / 1024 / 1280)։ Mobile first։ |
| `layout/header.css` | Գլխամաս և նավիգացիա։ |
| `layout/footer.css` | Տողատակ։ |
| `components/button.css` | `.btn` և տարբերակներ |
| `components/input.css` | `.form`, `.field`, `.input`, `.textarea` |
| `components/card.css` | `.cards`, `.card` |
| `pages/*.css` | Ոճեր, որ կան միայն մեկ էջում։ |

**Մեկ կոմպոնենտ — մեկ ֆայլ։** Կոճակի ոճերը մի գրեք `card.css`-ում։  
Նոր բլոկ (օր. modal)՝ `css/components/modal.css`, ապա `@import` `main.css`-ում։

### Ինչպես բացել

Բացեք `index.html` բրաուզերում կամ գործարկեք լոկալ սերվեր նախագծի պանակից։
