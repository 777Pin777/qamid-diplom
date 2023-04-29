# **Дипломный проект профессии «Инженер по тестированию»**

**Ссылка на задание/требования:** https://github.com/netology-code/qamid-diplom/blob/main/README.md

**Описание**

Автоматизация тестирования мобильного приложения "Мобильный хоспис".

Приложение предоставляет функционал по работе с претензиями хосписа и включает в себя:

1. Информацию о претензиях и функционал для работы с ними.
2. Новостную сводку хосписа.
3. Тематические цитаты.

**План тестирования:** Plan.md (https://github.com/777Pin777/qamid-diplom/blob/master/Plan.md)

**Чек-лист проекта с отметками о пройденых и непройденых тестах:** Check (https://docs.google.com/spreadsheets/d/1D5mbm0mrcwMBeJ967QA4bE5jMiysW-20tK7SajmM3jM/edit?usp=sharing)

**Тест-кейсы:** Cases (https://docs.google.com/spreadsheets/d/1hT7CQkQ35FxwDxytLo_39yz6etSw6_UNDc7euUXwYPo/edit?usp=sharing)

**Проект автоматизации тест-кейсов:**
https://github.com/777Pin777/qamid-diplom/tree/master/fmh-android

## **Процедура запуска авто-тестов:**

**1 способ (без Allure)**

1. Склонировать репозиторий https://github.com/777Pin777/qamid-diplom

2. Открыть проект fmh-android в Android Studio.

3. Запустить эмулятор (API 29) или подключить устройство для тестирования.

4. Запустить тесты консольной командой ./gradlew connectedAndroidTest.

**2 способ (с выгрузкой Allure-results)**

1. Склонировать репозиторий https://github.com/777Pin777/qamid-diplom

2. Открыть проект fmh-android в Android Studio.

3. Запустить эмулятор (API 29) или подключить устройство для тестирования.

4. Во вкладке Project левым кликом мыши (или аналогичным образом) выделить каталог app.

5. Запустить тесты сочетанием клавиш Shift+Ctl+R (Mac) или Shift+Ctrl+F10 (Windows). Если не получается, то во вкладке Run нажать Run all tests.

6. По завершению, выгрузите каталог /data/data/ru.iteco.fmhandroid/files/allure-results с эмулятора или тестового устройства (при помощи Device Manager). Лучше выгрузить в корень директории проекта.

7. Выполните локально консольную команду allure serve, находясь на уровень выше каталога allure-results.

**Комментарии проверяющему:**

1. Сильно усложнила себе задачу. Тесты работают исключительно с новостями, заявками и комментариями, которые создаются во время тестов. Также есть метод удаления именно ранее созданной новости. Если тест не стабилен и новость не удаляется, то это может оказать влияние на другие тесты.

2. Пришлось закомментировать некоторые тесты, которые связаны с созданием заявок. Проверка созданной заявки происходит среди сотней других (свайп) - один тест занимает приблизительно, до 30 мин. Тесты проходят, если запустить в одиночку. Проще тестировать вручную или подчистить заявки на сервере.

3. Есть крайне нестабильные тесты (около 11) при запуске всех тестов: создание и редактирование комментариев к заявкам, тесты, связанные с проверками в блоке новостей, 1 тест на проверку блока заявок, 2 теста для проверок главного блока. Если их запускать в одиночку, то они проходят.

4. Технические трудности с тестом для проверки фильтрации заявок (openStatusIsChosenDuringClaimsFiltering). Трудности со свайпом.

5. Обнаружено 2 бага (см. issues).

6. Использовала паттерн Page Object.

7. Со мной поделились кастомными методами, которые дополняют библиотеку (класс MainHelper): свайп, поиск элемента с определенным индексом.

8. Добавила в приложение три id: поле ввода логина, поле ввода пароля, поле ввода комментария к заявке.
