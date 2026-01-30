# SCSS / SASS

## 1. დაყენება

ბრაუზერებს არ შეუძლიათ `.scss` ფაილების პირდაპირ წაკითხვა. მათ მხოლოდ `.css` ესმით. გვჭირდება კომპილატორი, რათა `SCSS` გარდავქმნათ (დავაკომპილიროთ) `CSS`-ად.

1. გახსენით VS Code Extensions.

1. მოძებნეთ `Live Sass Compiler`.

1. დააყენეთ

1. დაარესტარტეთ VS Code.

1. გახსენით `.scss`-ის ფაილი და დააჭირეთ `Watch Sass` ღილაკს ქვედა პანელში.

ავტომატურად შეიქმნება `.css`-ის ფაილი.

> HTML-ში უნდა ჩასვათ `.css` ფაილი და არა `SCSS`.

## 2. Nesting

**SCSS:**

```SCSS
.navbar {
  background-color: black;

  // ჩაშენებული ელემენტი (Nested)
  ul {
    margin: 0;

    li {
      display: inline-block;
    }
  }
}
```

იგივეა რაც

**CSS:**

```CSS
.navbar {
  background-color: black;
}

.navbar ul {
    margin: 0;
}

.navbar ul li {
    display: inline-block;
}
```

> შემოიფარგლეთ 3 მშობლით.

## 3. მშობლის სელექტორი (&)

სიმბოლო `&` აკოპირებს მშობელი კლასის სახელს.

**SCSS:**

```SCSS
.btn {
    background: blue;

    &:hover { // იგივეა რაც .btn:hover
        background: darkblue;
    }

    &-primary { // იგივეა რაც .btn-primary
        background: red;
    }
}
```

## 4. მედია ქუერის ჩაშენება

გვაძლევს საშუალებას ჩავწეროთ რესპონსიული სტილები პირდაპირ იმ ელემენტის შიგნით, რომელსაც ეკუთვნის. აღარ მოგიწევს ფაილის ბოლოში სქროლვა.

**SCSS:**

```SCSS
.container {
  width: 100%;

  @media (min-width: 768px) {
    width: 50%;
  }
}
```

იგივეა რაც:

**CSS:**

```CSS
.container {
  width: 100%;
}

@media (min-width: 768px) {
    .container{
        width: 50%;
    }
}
```

## 5. CSS ცვლადები

გამოიყენება ისეთი მნიშვნელობებისთვის, რომლებიც მომავალში შეიძლება შეიცვალოს.

**CSS:**

```CSS
:root {
    --primary-color: #ff0000;
}

.box {
    background-color: var(--primary-color);
}
```

# Bootstrap 5

## 1. ინსტალაციის მეთოდები

### მეთოდი A: CDN (სწრაფი დაწყება)

არ მოითხოვს გადმოწერას. საუკეთესოა სწავლისთვის და მარტივი საიტებისთვის.

##### 1. CSS (ჩასვით `<head>` ტეგში):

link:css

```HTML
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css">
```

#### 2. JS (ჩასვით `</body>` ტეგის დახურვამდე):

```HTML
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js"></script>
```

### მეთოდი B: NPM (პროფესიონალური)

საუკეთესოა ისეთი ფრეიმვორკებისთვის, როგორიცაა Angular, React ან Vue.

#### 1. ბრძანება ტერმინალში:

```
npm install bootstrap
```

2. გამოყენება (და იმპორტი მთავარ ფაილში):

```HTML
<link rel="stylesheet" htef="./node_modules/bootstrap/dist/css/bootstrap.min.css">
```

```HTML
<script src="./node_modules/bootstrap/dist/js/bootstrap.min.js"></script>
```

## 2. ფერები (პალიტრა)

Bootstrap-ის ფერები არის სემანტიკური (ეფუძნება მნიშვნელობას და არა უბრალოდ ფერს).

| კლასის სუფიქსი | ფერი           | მნიშვნელობა                              |
| -------------- | -------------- | ---------------------------------------- |
| `*-primary`    | **ლურჯი**      | მთავარი მოქმედება / ბრენის ძირითადი ფერი |
| `*-secondary`  | **ნაცრისფერი** | ნაკლებად მნიშვნელოვანი                   |
| `*-success`    | **მწვანე**     | დასრულებული / წარმატების ჩვენება         |
| `*-danger`     | **წითელი**     | შეცდომა / წაშლა                          |
| `*-warning`    | **ყვითელი**    | გაფრთხილება                              |
| `*-info`       | **ცისფერი**    | ინფორმაცია                               |
| `*-light`      | **თეთრი/ღია**  | ღია ფონი                                 |
| `*-dark`       | **შავი/მუქი**  | მუქი ფონი                                |

### გამოყენება:

- `ტექსტი`: `.text-primary`

- `ფონი (Background)`: `.bg-danger`

- `ჩარჩო (Border)`: `.border-success` (აუცილებელია `.border` კლასის დამატებაც)

## 3. Margins & Padding

> **ფორმულა**: `{property}{მხარე}`-`{ზომა}`

### Properties

- `m` - **Margin**
- `p` - **Padding**

### მხარეები (Sides)

- `t` = **Top** (ზემოთ)

- `b` = **Bottom** (ქვემოთ)

- `s` = **Start** (მარცხნივ/დასაწყისი)

- `e` = **End** (მარჯვნივ/დასასრული)

- `x` = **X-ღერძი** (მარცხნივ და მარჯვნივ)

- `y` = **Y-ღერძი** (ზემოთ და ქვემოთ)

- **(ცარიელი)** = ოთხივე მხარე

### მაგალითები:

- `mt-5` (Margin Top 5 - ზედა გარე დაშორება 5)

- `px-3` (Padding Left & Right 3 - მარცხენა და მარჯვენა შიდა დაშორება 3)

- `m-0` (ყველა გარე დაშორების მოხსნა)

## 4. Grid - 12 Columns System

> წესი: რიგები (Rows) უნდა იყოს კონტეინერებში. სვეტები (Cols) უნდა იყოს რიგებში. სვეტების ჯამი უნდა უდრიდეს 12-ს.

```HTML
<div class="container">
  <div class="row">
    <!-- მობილურზე მთლიანი სიგანე, ტაბლეტზე 6 სვეტი (ნახევარი) -->
    <div class="col-12 col-md-6">A</div>
    <div class="col-12 col-md-6">B</div>
  </div>
</div>
```

## 5. განლაგება და ზომები

### სიგანე და სიმაღლე (Width & Height)

- **სიგანე**: `.w-25`, `.w-50`, `.w-75`, `.w-100`, `.w-auto`

- **სიმაღლე**: `.h-25`, `.h-50`, `.h-75`, `.h-100`

- **ეკრანის სიმაღლე (Viewport Height)**: `.vh-100` (მთლიანი ეკრანის სიმაღლე)

### Display

- `.d-none`: ელემენტის დამალვა.

- `.d-block`: ბლოკად ჩვენება (Block).

- `.d-inline`: ხაზოვნად ჩვენება (Inline).

- `.d-flex`: Flexbox-ის გააქტიურება.

> **რესპონსიული**: `.d-none` `d-md-block` (დამალულია მობილურზე, გამოჩნდება ტაბლეტიდან ზემოთ)

## 6. პოზიციონირება

> შენიშვნა: გამოიყენეთ `start` და `end` ნაცვლად `left` და `right`-ისა.

### სახეობები

- `.position-relative`: ნორმალური ნაკადი, საყრდენი წერტილი "absolute" ელემენტებისთვის.

- `.position-absolute`: თავისუფლად ტივტივებს მშობელი "relative" ელემენტის შიგნით.

- `.position-fixed`: ეკრანზე მიწებება (სქროლვის დროს არ მოძრაობს).

- `.sticky-top`: მიეწებებია ზევით, როცა მას გასცდებით სქროლვისას.

### კოორდინატები

- `.top-0`

- `.bottom-0`

- `.start-0` (მარცხნივ)

- `.end-0` (მარჯვნივ)

- `.translate-middle`: აცენტრირებს "absolute" ელემენტს (იგივეა რაც `translate(-50%, -50%)`).

```HTML
<div class="position-relative">
  <div class="position-absolute top-0 end-0">9+</div>
</div>
```

## 7. ტექსტი და ტიპოგრაფია

### Alignment

- `.text-start` (მარცხნივ გასწორება)

- `.text-center` (ცენტრში გასწორება)

- `.text-end` (მარჯვნივ გასწორება)

### ზომა და სისქე

- **ზომები:** `.fs-1` (დიდი)-დან `.fs-6` (პატარა)-მდე.

- **სათაურის ზომები:** `.h1` (დიდი)-დან `.h6` (პატარა)-მდე.

- **სისქე:** `.fw-bold` (მუქი), `.fw-normal` (ნორმალური), `.fw-light` (თხელი).

- **დახრილი:** `.fst-italic`.

### ტრანსფორმაციები

- `.text-uppercase` (დიდი ასოები)

- `.text-lowercase` (პატარა ასოები)

- `.text-capitalize` (პირველი ასო დიდი)

- `.text-decoration-none` (ხაზის მოცილება ლინკებისთვის)
