# Your Style Flutter App

Your style app for beautiful people

## Использованные библиотеки

- splashscreen - для создания качественного загрузочного экрана
- http - для осуществление запросов API
- carousel_slider - для создания слайдеров внутри приложения
- flappy_search_bar - для созания полноэкранного поиска
- url_launcher - для открытия ссылок и перенаправления пользователя в браузер

## Описание основных файлов и директорий проекта

Проект содержит следующие директории:

- assets - содержит переиспользуемые файлы, классы констант и переиспоьзуемых функций
- models - содержит классы моделей, необходимых для типизации, а также конструкторы и json декодеры
- others - содержит классы переиспользуемых виджетов
- pages - содержит классы всех разделов приложения
- services - содержит статичный класс для работы с API

## Описание всех файлов и классов

Стартовым файлом является main.dart. В нет содержится класс приложения, который запускает Splash экран, а тот в свою очередь запускает MainPage.

### Базовые классы

[MainPage](./lib/main.dart) - носит архитектурное назначение и предназначен для построении навигации в приложении. Содержит в себе 5 фрагментов (BasePage), которые при инициализации получают стартовый фрагмент и запускают его. Далее строят дочернюю навигацию внутри себя.

[BasePage](./lib/BasePage.dart) - дочерняя для MainPage навигационный фрагмент. Сам по себе не отображает никакой информации, кроме находящегося в нем фрагмента.

### Файл констант

[consts](./lib/assets/consts.dart) - файл содержащий в себе все переиспользуемый константы в проекте. На текущий момент содержит только константу основного цвета приложения.

### Классы типизации

[offers](./lib/models/offer.dart) - содержит все классы моделей используемый в приложении. Каждая модель имеет конструтор и json декодер. Сейчас имеются классы:

- Offer - класс товара приложения

- Category - класс категории магазина

- PriceRange - класс для API получения диапазона цен

### API приложения

[ApiService](./lib/services/api.service.dart) - класс для работы с API. Имеет конструктор запросов, все методы статичный, каждый метод возвращает ассинхронный Promise задачу на получение каких-либо данных. Имеются апи получения списка товаров, категорий, диапазона цен. API получения списка товаров имеет возможность фильтрации и пагинации.

### Переиспользуемые виджеты

[ApiService](./lib/other/BaseCard.dart) - Виджет карточки товаров, содержит кнопки добавления в корзину и в избранное. Нажатие на саму карточку перенаправляет в браузер пользователя.

### Страницы приложения

Реализованы следующий разделы:

- Список каталогов

- Стараница избранного

- Страница фильтров

- Вкладка "Главное"

- Страница списка товаров

- Страница профиля пользователя

- Страница поиска

[CatalogPage](./lib/pages/CatalogsPage.dart) - Экран со списком каталогов магазина. Автоматически подгружает список, по нажатию на любой элемент происходит навигация на страницу списка товаров с автивированным филтром.

[FavoritsPage](./lib/pages/favoritsPage.dart) - Страница с избранными товарами, добавление в избранное происходит нажатием на иконку favorit на карточке товара. В пустом состоянии пользователю предлагается продолжить покупку.

[FiltersPage](./lib/pages/FiltersPage.dart) - Сттраница фильтрации списка товаров. Перейти на нее можно со вкладки списка товаров, по нажатию на кнопку применить перенаправляет на экран списка товаров с применненным фильтром. На текущий момент доступна только фильтрация по цене с помощью Range слайдера.

[MainPage](./lib/pages/MainPage.dart) - Страница "Главное" с последними акциями и актуальными категориями.

[ProductList](./lib/pages/ProductList.dart) - Список товаров. Реализовано как Grid список с пагинацией. Имеется возможность фильтрации. Конструктор класса принимает параметры фильтрации, по которым фильтрует список при запросе.

[ProfilePage](./lib/pages/ProfilePage.dart) - Страница профиля с основной информацией о пользователе.

[SearchPage](./lib/pages/SearchPage.dart) - Страница поиска, позволяет динамично искать товары, в случае, если результаты поиска устраивают пользователя, то он нажимает применить и происходит навигация на список товаров с примененным фильтром.
