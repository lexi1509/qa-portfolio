# Баг-репорт: Не открывается поддомен shop.avtoshkolamaster.ru (DNS_PROBE_FINISHED_NXDOMAIN)

---

## Мета-информация

| Поле | Значение |
|------|----------|
| **ID** | BUG-003 |
| **Проект** | [master164.ru](https://master164.ru) / Магазин мерча |
| **Дата обнаружения** | 2026-03-08 |
| **Автор** | Любовь Алексеева |
| **Тип дефекта** | Ошибка DNS / Недоступность ресурса |

---

## Заголовок
При переходе на поддомен `shop.avtoshkolamaster.ru` (по кнопке с главной страницы или напрямую) возникает ошибка DNS_PROBE_FINISHED_NXDOMAIN, сайт не открывается.

---

## Предусловие
Пользователь находится на главной странице сайта [https://master164.ru](https://master164.ru).

---

## Окружение (Environment)

| Компонент | Значение |
|-----------|----------|
| **Устройство** | MacBook Pro 16" 2021 |
| **ОС** | macOS Tahoe 26.2 |
| **Браузеры** | Safari, Яндекс.Браузер |
| **Сайт** | [https://master164.ru](https://master164.ru) |
| **Поддомен** | [https://shop.avtoshkolamaster.ru](https://shop.avtoshkolamaster.ru) |

---

## Шаги воспроизведения

1. Открыть главную страницу [https://master164.ru](https://master164.ru).
2. Найти и нажать кнопку **«Магазин мерча Мастер»**.
3. Дождаться попытки перехода по адресу `https://shop.avtoshkolamaster.ru`.
4. (Альтернативно) Попробовать открыть указанный поддомен напрямую в браузере.

---

## Фактический результат (Actual Result)

*   При переходе по ссылке браузер выдаёт системную страницу с ошибкой соединения.
*   В деталях ошибки указан код: **DNS_PROBE_FINISHED_NXDOMAIN**.
*   Поддомен `shop.avtoshkolamaster.ru` не резолвится в IP-адрес.
*   Страница магазина мерча не загружается.
*   Проблема стабильно воспроизводится в браузерах Safari и Яндекс.Браузер.

**Подтверждение от внешнего сервиса:**
Сервис [brokenlinkcheck.com](https://www.brokenlinkcheck.com/) при проверке сайта также идентифицировал ссылку на `https://shop.avtoshkolamaster.ru/` как битую с причиной **"bad host"**.

---

## Ожидаемый результат (Expected Result)

*   При нажатии на кнопку «Магазин мерча Мастер» поддомен `shop.avtoshkolamaster.ru` открывается корректно.
*   Доменное имя успешно резолвится в IP-адрес.
*   Страница магазина мерча загружается полностью, пользователь видит интерфейс магазина (товары, категории, корзину).
*   Ошибки соединения или DNS не возникают.

---

## Скриншоты

| Описание | Изображение |
|----------|-------------|
| Кнопка «Магазин мерча Мастер» на главной странице | ![Кнопка магазина](https://github.com/lexi1509/qa-portfolio/raw/main/screenshots/shop-button.png) |
| Отчёт сервиса BrokenLinkCheck, подтверждающий битую ссылку | ![Отчёт BrokenLinkCheck](https://github.com/lexi1509/qa-portfolio/raw/main/screenshots/broken-link-check-report.png) |
| Ошибка DNS_PROBE_FINISHED_NXDOMAIN в браузере Safari | ![Ошибка Safari](https://github.com/lexi1509/qa-portfolio/raw/main/screenshots/safari-dns-error.png) |
| Ошибка в Яндекс.Браузере | ![Ошибка Яндекс.Браузер](https://github.com/lexi1509/qa-portfolio/raw/main/screenshots/yandex-browser-dns-error.png) |

---

## Статус

🐞 **Открыт**