# Реєстр дефектів, спринт 3

Продукт «ШопЛайн», demo Toolshop. Звіти за шаблоном 4.11. Автор: Пінчук К. (Інженер з тестування). Еталон: SRS v1.1 (docs/sprint2/SRS-1.1.md).
Кожен звіт заведено окремою issue у GitHub (elsezz/SQAT_labs, #1–#14, 16.11.2026) з мітками severity:*, priority:*, status:new, sprint:3.

| Bug ID | Issue | Title | Severity | Priority | TC | Вимога |
|---|---|---|---|---|---|---|
| BUG-001 | [#1](https://github.com/elsezz/SQAT_labs/issues/1) | Пошук: запит «hammer» не знаходить «Sledgehammer», хоча назва містить запит як підрядок (F-60) | Major | P3 | TC-009 | F-60 |
| BUG-002 | [#2](https://github.com/elsezz/SQAT_labs/issues/2) | Оформлення замовлення: на кроці «Sign in» гостю пропонується «Continue as Guest» без облікового запису (F-110, S-20) | Major | P3 | TC-026 | F-110, S-20, 2.1 |
| BUG-003 | [#3](https://github.com/elsezz/SQAT_labs/issues/3) | Контактна форма: вкладення обмежене файлами .txt розміром 0 КБ замість .txt/.pdf/.jpg/.png до 2 МБ (F-140) | Normal | P3 | TC-028 | F-140 |
| BUG-004 | [#4](https://github.com/elsezz/SQAT_labs/issues/4) | Каталог: після зміни сортування на другій сторінці показано товари першої сторінки, а в навігації підсвічено «2» (F-70) | Minor | P3 | TC-016 | F-70, F-40 |
| BUG-005 | [#5](https://github.com/elsezz/SQAT_labs/issues/5) | Реєстрація: поле «House number» обов'язкове (зірочка і помилка «House number is required»), хоча за F-10 воно необов'язкове | Normal | P3 | TC-006, TC-004 | F-10, GUI-65 |
| BUG-006 | [#6](https://github.com/elsezz/SQAT_labs/issues/6) | Ширина 375 px: кнопка меню навігації має висоту 40 px, менше мінімальних 44×44 (U-30) | Minor | P3 | TC-030 | U-30 |
| BUG-007 | [#7](https://github.com/elsezz/SQAT_labs/issues/7) | Сторінка товару «Pliers»: зображення 427×640 у форматі AVIF замість ≥1000×1000 JPEG/WebP (GUI-80) | Minor | P3 | TC-031 | GUI-80 |
| BUG-008 | [#8](https://github.com/elsezz/SQAT_labs/issues/8) | Сторінка товару: кнопка «−» поля «Quantity» активна при значенні 1 (GUI-30) | Trivial | P3 | TC-018 | GUI-30 |
| BUG-009 | [#9](https://github.com/elsezz/SQAT_labs/issues/9) | Сторінка товару: кнопка «+» поля «Quantity» активна при значенні 99 (GUI-30) | Trivial | P3 | TC-019 | GUI-30 |
| BUG-010 | [#10](https://github.com/elsezz/SQAT_labs/issues/10) | Відновлення пароля: після надсилання форми замість повідомлення показано ключ перекладу «page.forgot-password.confirm» (F-30) | Minor | P3 | TC-007 | F-30 |
| BUG-011 | [#11](https://github.com/elsezz/SQAT_labs/issues/11) | Оформлення замовлення: на кроці «Payment» немає підсумку замовлення (сума, знижки, доставка), рахунок створено без вартості доставки (F-110) | Major | P3 | TC-033 | F-110, BL-60 |
| BUG-012 | [#12](https://github.com/elsezz/SQAT_labs/issues/12) | Кабінет: у списку «Invoices» і на сторінці рахунку немає статусу замовлення (F-130) | Normal | P3 | TC-035 | F-130 |
| BUG-013 | [#13](https://github.com/elsezz/SQAT_labs/issues/13) | Реєстрація: після введення поштового індексу і номера будинку форма перезаписує вулицю, місто й область вигаданою адресою (Kris Greens, Tabithastad, Arizona) | Normal | P3 | TC-004, TC-005 | F-10, 1.3 |
| BUG-014 | [#14](https://github.com/elsezz/SQAT_labs/issues/14) | Реєстрація: для пароля без спецсимволу показано хибне повідомлення «Password can not include invalid characters.» не під полем пароля | Minor | P3 | TC-005 | F-10, GUI-50 |

## BUG-001: Пошук: запит «hammer» не знаходить «Sledgehammer», хоча назва містить запит як підрядок (F-60)

**Severity:** Major  **Priority:** P3  
**Linked:** test case TC-009; requirement F-60  
**Reporter:** Пінчук К.  **Date:** 15.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
F-60 (SRS v1.1) вимагає знаходити товари, назва яких містить запит як підрядок без урахування регістру. Фактично пошук знаходить лише товари, де запит є окремим словом: для «hammer» повертає 6 товарів і пропускає «Sledgehammer», який є в каталозі (його показує фільтр Hammer, і він знаходиться запитом sledge). Запит Hammer дає той самий результат. Severity Major: пошук, ключова функція каталогу, повертає неповний результат, покупець не бачить частину товарів. P3: інших кейсів не блокує.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com у браузері, нова сесія.
2. У поле «Search» ліворуч від каталогу ввести hammer.
3. Натиснути кнопку «Search».
4. Прокрутити список результатів до кінця.

### Actual result
Після кроку 3 заголовок «Searched for: hammer» і напис «6 products found for 'hammer'». Список: Claw Hammer with Shock Reduction Grip, Hammer, Claw Hammer, Thor Hammer, Claw Hammer with Fiberglass Handle, Court Hammer. Товару «Sledgehammer» (ціна 17.75) немає.

### Expected result
За F-60: 7 товарів, серед них «Sledgehammer», бо назва містить «hammer» як підрядок без урахування регістру.

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 15.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-001-1.jpg](attachments/BUG-001-1.jpg) - результати пошуку після кроку 3, шість карток
- [BUG-001-2.jpg](attachments/BUG-001-2.jpg) - фільтр «Hammer» на тій самій збірці: сім карток, серед них Sledgehammer

---

## BUG-002: Оформлення замовлення: на кроці «Sign in» гостю пропонується «Continue as Guest» без облікового запису (F-110, S-20)

**Severity:** Major  **Priority:** P3  
**Linked:** test case TC-026; requirement F-110, S-20, 2.1  
**Reporter:** Пінчук К.  **Date:** 15.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
За 2.1 оформлення замовлення доступне лише зареєстрованому покупцю; F-110 передбачає, що неавторизований покупець на кроці 2 входить або реєструється; S-20 вимагає, щоб кроки 3–4 були недоступні неавторизованому користувачу. Фактично крок «Sign in» має вкладку «Continue as Guest» з формою (Email, First name, Last name) для оформлення без облікового запису. Форму не надсилали, щоб не створювати даних на спільному demo. Severity Major: порушено бізнес-правило доступу до оформлення, від якого залежить програма лояльності (знижки і промокоди прив'язані до облікового запису). P3: інших кейсів не блокує.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com у браузері, нова сесія, без входу.
2. Натиснути на картку «Pliers».
3. Натиснути «Add to cart».
4. Натиснути піктограму кошика у верхньому меню.
5. Натиснути «Proceed to checkout».
6. Натиснути вкладку «Continue as Guest».

### Actual result
Після кроку 5 відкрито крок 2 «Sign in» з двома вкладками: «Sign in» і «Continue as Guest». Після кроку 6 показано заголовок «Continue as Guest», текст «Checkout without creating an account», поля «Email address *», «First name *», «Last name *» і кнопку «Continue as Guest».

### Expected result
На кроці «Sign in» доступні лише форма входу і посилання «Register your account»; можливості продовжити оформлення без облікового запису немає (2.1, F-110, S-20).

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 15.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-002-1.jpg](attachments/BUG-002-1.jpg) - крок «Sign in» після кроку 6 з відкритою вкладкою «Continue as Guest»

---

## BUG-003: Контактна форма: вкладення обмежене файлами .txt розміром 0 КБ замість .txt/.pdf/.jpg/.png до 2 МБ (F-140)

**Severity:** Normal  **Priority:** P3  
**Linked:** test case TC-028; requirement F-140  
**Reporter:** Пінчук К.  **Date:** 15.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
F-140 дозволяє один файл .txt, .pdf, .jpg або .png розміром до 2 МБ. Фактично поле «Attachment» приймає лише .txt (атрибут accept=".txt"), а підказка під полем вимагає розмір 0 КБ, тобто прикріпити змістовний файл неможливо. Severity Normal: звернення можна надіслати без вкладення, але покупець не може додати фото пошкодженого товару чи PDF-чек до звернення щодо повернення. P3: кейсів не блокує.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com у браузері, нова сесія.
2. Натиснути «Contact» у верхньому меню.
3. Прочитати підказку під полем «Attachment».
4. Відкрити DevTools (F12), вкладка Elements, виділити поле «Attachment» і переглянути атрибут accept.

### Actual result
Після кроку 3 під полем текст «Only files with the txt extension are allowed, and files must be 0kb.». Після кроку 4 атрибут поля accept=".txt".

### Expected result
За F-140: підказка і атрибут accept дозволяють один файл .txt, .pdf, .jpg або .png розміром до 2 МБ.

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 15.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-003-1.jpg](attachments/BUG-003-1.jpg) - сторінка «Contact», підказка під полем «Attachment»

---

## BUG-004: Каталог: після зміни сортування на другій сторінці показано товари першої сторінки, а в навігації підсвічено «2» (F-70)

**Severity:** Minor  **Priority:** P3  
**Linked:** test case TC-016; requirement F-70, F-40  
**Reporter:** Пінчук К.  **Date:** 15.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
F-70 вимагає застосовувати сортування до всіх сторінок каталогу, F-40 передбачає посторінкову навігацію. Після зміни сортування на сторінці 2 список скидається на першу сторінку відсортованого каталогу, але підсвічування в навігації лишається на «2»; користувач не знає, яку сторінку бачить, і перехід на «2» здається непотрібним. Severity Minor: дані правильні, порушено узгодженість інтерфейсу. P3.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com у браузері, нова сесія.
2. Натиснути «2» у посторінковій навігації під картками.
3. У списку «Sort» ліворуч обрати «Name (A - Z)».
4. Прокрутити до навігації під картками.

### Actual result
Після кроку 3 показано картки Adjustable Wrench, Angled Spanner, Belt Sander, Bolt Cutters, Chisels Set, Circular Saw, Claw Hammer, Claw Hammer with Fiberglass Handle, Claw Hammer with Shock Reduction Grip (перші 9 за абеткою). Після кроку 4 у навігації підсвічено «2».

### Expected result
Номер активної сторінки відповідає показаним карткам: після зміни сортування підсвічено «1» (або показано другу сторінку відсортованого списку, Combination Pliers … Drawer Tool Cabinet).

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 15.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-004-1.jpg](attachments/BUG-004-1.jpg) - кінець списку після кроку 4: картки першої сторінки A–Z і підсвічена «2»

---

## BUG-005: Реєстрація: поле «House number» обов'язкове (зірочка і помилка «House number is required»), хоча за F-10 воно необов'язкове

**Severity:** Normal  **Priority:** P3  
**Linked:** test case TC-006, TC-004; requirement F-10, GUI-65  
**Reporter:** Пінчук К.  **Date:** 16.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
F-10 (SRS v1.1, дефект аудиту № 5) визначає обов'язковими всі поля, крім «номер будинку». Фактично плейсхолдер поля «House number» «e.g. 42 *» позначає його обов'язковим (TC-006), а під час реєстрації з порожнім полем форма показує «House number is required» і не створює обліковий запис (TC-004, 16.11.2026). Реєстрація можлива лише після введення будь-якого номера. Severity Normal: реєстрацію можна завершити, але лише всупереч вимозі, вводячи вигаданий номер. P3: інших кейсів не блокує, обхід є.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com/auth/register у браузері, нова сесія.
2. Заповнити поля: First name = T3-Тест, Last name = Тестенко, Date of Birth = 1995-05-15, Country = Ukraine, Postal code = 01001, Street = Testova St 1, City = Kyiv, State = Kyiv, Phone = 0001234567, Email address = t3.<ддммрр>@example.com, Password = довільний пароль за правилами (наприклад, з великою і малою літерою, цифрою і спецсимволом, не менше 8 символів). Поле «House number» не заповнювати.
3. Натиснути «Register».

### Actual result
Після кроку 1 плейсхолдер «House number» - «e.g. 42 *» (як в обов'язкових полях). Після кроку 3 під полем «House number» червоний блок «House number is required», поле підсвічене як помилкове, обліковий запис не створено, адреса залишається /auth/register.

### Expected result
Поле «House number» без зірочки; після кроку 3 обліковий запис створено і відкрито сторінку входу (F-10).

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 16.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-005-1.jpg](attachments/BUG-005-1.jpg) - форма «Customer registration», плейсхолдер «e.g. 42 *»
- [BUG-005-2.jpg](attachments/BUG-005-2.jpg) - форма після кроку 3: «House number is required» при заповнених інших полях

---

## BUG-006: Ширина 375 px: кнопка меню навігації має висоту 40 px, менше мінімальних 44×44 (U-30)

**Severity:** Minor  **Priority:** P3  
**Linked:** test case TC-030; requirement U-30  
**Reporter:** Пінчук К.  **Date:** 15.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
U-30 вимагає кнопок, придатних для натискання пальцем, не менше 44×44 пікселі за ширини вікна 375 px. Фактично кнопка меню навігації (☰) має розмір 56×40 пікселів. Severity Minor: меню працює, але ціль дотику менша за норму, на телефоні можливі промахи. P3.

### Steps to reproduce
1. Відкрити Chrome DevTools, увімкнути режим пристрою з розміром 375×812.
2. Відкрити https://practicesoftwaretesting.com, нова сесія.
3. У DevTools (Elements) виділити кнопку меню навігації ☰ під логотипом і переглянути її розмір.

### Actual result
Горизонтального прокручування немає; кнопка ☰ має розмір 56×40 пікселів (getBoundingClientRect: width 56, height 40).

### Expected result
Розмір кнопки не менше 44×44 пікселі (U-30).

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 15.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; емуляція мобільного пристрою 375×812 (Android 14, Pixel 8); без входу в обліковий запис

### Attachments
- [BUG-006-1.jpg](attachments/BUG-006-1.jpg) - головна сторінка за ширини 375 px, кнопка ☰ під логотипом

---

## BUG-007: Сторінка товару «Pliers»: зображення 427×640 у форматі AVIF замість ≥1000×1000 JPEG/WebP (GUI-80)

**Severity:** Minor  **Priority:** P3  
**Linked:** test case TC-031; requirement GUI-80  
**Reporter:** Пінчук К.  **Date:** 15.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
GUI-80 вимагає на сторінці товару зображення не менше 1000×1000 пікселів у форматі JPEG або WebP. Фактично головне зображення товару «Pliers» має 427×640 пікселів і формат AVIF (так само картка каталогу: pliers01.avif, 640×432 для Combination Pliers). Severity Minor: зображення відображаються, але деталі товару при збільшенні нечіткі, а AVIF не підтримується частиною старих браузерів. P3; пріоритет вимоги Low.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com у браузері, нова сесія, і натиснути на картку «Pliers» у каталозі (ID товару в адресі змінюється після скидання даних demo).
2. Відкрити DevTools (F12), вкладка Elements, виділити головне зображення товару.
3. Переглянути адресу файлу і natural size у підказці DevTools.

### Actual result
Файл https://practicesoftwaretesting.com/assets/img/products/pliers02.avif, natural size 427×640.

### Expected result
Зображення не менше 1000×1000 пікселів у форматі JPEG або WebP (GUI-80).

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 15.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-007-1.jpg](attachments/BUG-007-1.jpg) - сторінка товару «Pliers»

---

## BUG-008: Сторінка товару: кнопка «−» поля «Quantity» активна при значенні 1 (GUI-30)

**Severity:** Trivial  **Priority:** P3  
**Linked:** test case TC-018; requirement GUI-30  
**Reporter:** Пінчук К.  **Date:** 15.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
GUI-30 вимагає, щоб кнопка «−» була неактивною при значенні 1. Фактично кнопка активна (не має стану disabled і виглядає як звичайна), хоча натискання значення не змінює. Severity Trivial: на функціональність не впливає, лише візуальний стан елемента. P3.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com у браузері, нова сесія.
2. Натиснути на картку «Pliers».
3. Переглянути кнопку «−» ліворуч від поля «Quantity» (значення 1).
4. Натиснути «−».

### Actual result
Після кроку 3 кнопка «−» активна, такого ж кольору, як «+». Після кроку 4 значення лишається 1.

### Expected result
Після кроку 3 кнопка «−» неактивна (disabled) і візуально відрізняється від активної (GUI-30).

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 15.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-008-1.jpg](attachments/BUG-008-1.jpg) - сторінка товару «Pliers», поле «Quantity» = 1, кнопка «−» активна

---

## BUG-009: Сторінка товару: кнопка «+» поля «Quantity» активна при значенні 99 (GUI-30)

**Severity:** Trivial  **Priority:** P3  
**Linked:** test case TC-019; requirement GUI-30  
**Reporter:** Пінчук К.  **Date:** 15.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
GUI-30 вимагає, щоб кнопка «+» була неактивною при значенні 99. Фактично кнопка активна; натискання значення не змінює (верхня межа тримається). Окремий звіт від BUG-008, бо це інший елемент і інша межа. Severity Trivial: на функціональність не впливає. P3.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com у браузері, нова сесія.
2. Натиснути на картку «Pliers».
3. Виділити значення поля «Quantity», ввести 99, натиснути Tab.
4. Переглянути кнопку «+».
5. Натиснути «+».

### Actual result
Після кроку 3 у полі 99. Після кроку 4 кнопка «+» активна. Після кроку 5 значення лишається 99.

### Expected result
Після кроку 4 кнопка «+» неактивна (disabled) (GUI-30).

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 15.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-009-1.png](attachments/BUG-009-1.png) - фрагмент сторінки товару: поле «Quantity» = 99, кнопка «+» активна

---

## BUG-010: Відновлення пароля: після надсилання форми замість повідомлення показано ключ перекладу «page.forgot-password.confirm» (F-30)

**Severity:** Minor  **Priority:** P3  
**Linked:** test case TC-007; requirement F-30  
**Reporter:** Пінчук К.  **Date:** 16.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
F-30 вимагає після надсилання форми показати повідомлення про надсилання листа. Фактично в зеленому блоці підтвердження виведено технічний ключ локалізації «page.forgot-password.confirm» замість тексту, тож користувач не розуміє, чи надіслано лист і що робити далі. Відтворено двічі поспіль. Severity Minor: функцію можна виконати, але повідомлення інтерфейсу нечитабельне. P3: інших кейсів не блокує.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com/auth/login у браузері, нова сесія, мова інтерфейсу EN.
2. Натиснути посилання «Forgot your Password?».
3. У поле «Email address» ввести customer@practicesoftwaretesting.com.
4. Натиснути кнопку «Set New Password».

### Actual result
Після кроку 2 відкрито сторінку «Forgot Password» (/auth/forgot-password) з одним полем «Email address *». Після кроку 4 під кнопкою зелений блок з текстом «page.forgot-password.confirm»; адреса сторінки не змінюється.

### Expected result
Після кроку 4 повідомлення зрозумілим текстом про те, що лист із посиланням для встановлення нового пароля надіслано (F-30).

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 16.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-010-1.jpg](attachments/BUG-010-1.jpg) - сторінка «Forgot Password» після кроку 4 з текстом «page.forgot-password.confirm»

---

## BUG-011: Оформлення замовлення: на кроці «Payment» немає підсумку замовлення (сума, знижки, доставка), рахунок створено без вартості доставки (F-110)

**Severity:** Major  **Priority:** P3  
**Linked:** test case TC-033; requirement F-110, BL-60  
**Reporter:** Пінчук К.  **Date:** 16.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
F-110 вимагає, щоб підсумок замовлення містив суму товарів, знижку за обсяг, знижку за промокодом і вартість доставки за BL-60 (120 грн для суми менше 1500). Фактично на кроці «Payment» є лише список способів оплати і кнопка «Check payment», жодної суми покупець перед підтвердженням не бачить; створений рахунок INV-2026000009 має Total 12.01 для товару за 12.01, тобто без доставки. Severity Major: покупець підтверджує замовлення, не знаючи підсумкової суми, а доставка не нараховується. P3: інших кейсів не блокує.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com у браузері, нова сесія; увійти власним тестовим обліковим записом (зареєстрованим за TC-004).
2. Натиснути на картку «Pliers» (ціна 12.01), натиснути «Add to cart».
3. Натиснути піктограму кошика, потім «Proceed to checkout» на кроках «Cart» і «Sign in».
4. На кроці «Billing Address» за потреби заповнити «House number» = 1 і натиснути «Proceed to checkout».
5. На кроці «Payment» переглянути сторінку; обрати «Cash on Delivery», натиснути «Check payment», потім «Confirm».
6. Відкрити «My invoices» у меню користувача.

### Actual result
Після кроку 5 (до підтвердження) на сторінці лише заголовок «Payment», список способів оплати і кнопка «Check payment»; сум, знижок і доставки немає. Після «Confirm» повідомлення «Thanks for your order! Your invoice number is INV-2026000009.». Після кроку 6 рахунок INV-2026000009 з Total $12.01.

### Expected result
На кроці «Payment» підсумок: сума товарів 12.01, знижка за обсяг 0.00, знижка за промокодом 0.00, доставка 120.00, до сплати 132.01 (F-110, BL-60); рахунок створено на 132.01.

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 16.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; власний тестовий обліковий запис t3.hanna.161126@example.com

### Attachments
- [BUG-011-1.jpg](attachments/BUG-011-1.jpg) - крок «Payment» після вибору «Cash on Delivery»: підсумку немає
- [BUG-011-2.jpg](attachments/BUG-011-2.jpg) - повідомлення з номером рахунку INV-2026000009

---

## BUG-012: Кабінет: у списку «Invoices» і на сторінці рахунку немає статусу замовлення (F-130)

**Severity:** Normal  **Priority:** P3  
**Linked:** test case TC-035; requirement F-130  
**Reporter:** Пінчук К.  **Date:** 16.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
F-130 вимагає, щоб розділ «My invoices» показував для кожного замовлення номер, дату, суму і статус. Фактично таблиця має колонки Invoice Number, Billing Address, Invoice Date, Total і кнопку Details, а сторінка деталей рахунку містить General Information, Billing Address, Payment Information і Products; статусу ніде немає. Severity Normal: покупець бачить замовлення, але не може дізнатися, на якому етапі воно. P3: кейсів не блокує.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com у браузері, нова сесія; увійти обліковим записом, у якого є хоча б одне замовлення (наприклад, після кроків BUG-011).
2. У меню користувача обрати «My invoices».
3. Переглянути заголовки таблиці.
4. Натиснути «Details» біля першого рахунку і переглянути сторінку.

### Actual result
Після кроку 3 колонки: Invoice Number, Billing Address, Invoice Date, Total, (Details). Після кроку 4 поля Invoice Number, Invoice Date, Total, Billing Address (Street, Postal code, City, State, Country), Payment Method, таблиця Products і кнопка «Download PDF»; поля статусу немає.

### Expected result
У таблиці є колонка статусу замовлення, і статус показано на сторінці деталей (F-130).

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 16.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; власний тестовий обліковий запис t3.hanna.161126@example.com

### Attachments
- [BUG-012-1.jpg](attachments/BUG-012-1.jpg) - список «Invoices» з колонками без статусу

---

## BUG-013: Реєстрація: після введення поштового індексу і номера будинку форма перезаписує вулицю, місто й область вигаданою адресою (Kris Greens, Tabithastad, Arizona)

**Severity:** Normal  **Priority:** P3  
**Linked:** test case TC-004, TC-005; requirement F-10, 1.3  
**Reporter:** Пінчук К.  **Date:** 16.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
Форма реєстрації автоматично заповнює Street, City і State за країною, поштовим індексом і номером будинку. Для Ukraine / 01001 вона підставляє адресу в США (Kris Greens, Tabithastad, Arizona) і перезаписує вже введені значення без попередження. Якщо користувач не помітить заміни, у профіль зберігається чужа адреса (TC-004: у профілі і на кроці «Billing Address» з'явилась Kris Greens / Tabithastad / Arizona). Вимога F-10 визначає поля вулиця, місто, область як дані покупця, а 1.3 використовує їх як адресу доставки; заміна введених даних суперечить логіці форми. Severity Normal: обхід є (ввести адресу після номера будинку), але адреса доставки може зберегтися хибною непомітно. P3.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com/auth/register у браузері, нова сесія.
2. У поле Street ввести Testova St 1, у City ввести Kyiv, у State ввести Kyiv.
3. У списку Country обрати Ukraine.
4. У поле Postal code ввести 01001.
5. У поле House number ввести 1 і натиснути Tab.

### Actual result
Після кроку 5 поля змінюються: Street = Kris Greens, City = Tabithastad, State = Arizona; введені на кроці 2 значення втрачено, повідомлення про заміну немає.

### Expected result
Введені користувачем значення Street, City, State не перезаписуються; автозаповнення (якщо є) пропонує адресу, що відповідає країні й індексу, і не замінює дані без підтвердження.

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 16.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-013-1.jpg](attachments/BUG-013-1.jpg) - форма реєстрації після кроку 5: Ukraine, 01001, 1 і підставлена адреса Kris Greens / Tabithastad / Arizona

---

## BUG-014: Реєстрація: для пароля без спецсимволу показано хибне повідомлення «Password can not include invalid characters.» не під полем пароля

**Severity:** Minor  **Priority:** P3  
**Linked:** test case TC-005; requirement F-10, GUI-50  
**Reporter:** Пінчук К.  **Date:** 16.11.2026  **Status:** New  **Reviewer:** ________ (дата ______)

### Description
F-10 вимагає для пароля, що не відповідає правилам, показати повідомлення за GUI-50 (текстом безпосередньо під полем). Для пароля Passw0rdT3 (лише латинські літери і цифри, бракує спецсимволу) форма показує «Password can not include invalid characters.», хоча недопустимих символів немає, а порушене правило - відсутність спецсимволу; повідомлення виведено нижче переліку правил та індикатора надійності, а не безпосередньо під полем. Обліковий запис коректно не створено, дані в полях збережено. Severity Minor: реєстрація захищена правильно, але текст помилки вводить в оману. P3.

### Steps to reproduce
1. Відкрити https://practicesoftwaretesting.com/auth/register у браузері, нова сесія.
2. Заповнити поля: First name = T3-Тест, Last name = Тестенко, Date of Birth = 1995-05-15, Country = Ukraine, Postal code = 01001, House number = 1, Street = Testova St 1, City = Kyiv, State = Kyiv, Phone = 0001234567, Email address = t3.neg.<ддммрр>@example.com.
3. У поле Password ввести Passw0rdT3.
4. Натиснути «Register».

### Actual result
Після кроку 3 у переліку правил три зелені пункти, пункт про спецсимвол сірий. Після кроку 4 нижче індикатора надійності червоний блок «Password can not include invalid characters.»; обліковий запис не створено.

### Expected result
Безпосередньо під полем Password повідомлення про порушене правило, наприклад про відсутність спецсимволу (F-10, GUI-50); обліковий запис не створено.

### Environment
demo https://practicesoftwaretesting.com (Toolshop v5.0, footer «v2.5 | Built 2026-10-11»), стан на 16.11.2026; Chromium 156.0 (вбудований браузер Claude Desktop); Windows 10 x64; вікно 1280×800; без входу в обліковий запис

### Attachments
- [BUG-014-1.jpg](attachments/BUG-014-1.jpg) - форма після кроку 4: правила, індикатор і повідомлення «Password can not include invalid characters.»

---
