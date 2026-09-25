# Юридичні документи Wayly

Публічна оферта й політика конфіденційності. Опубліковані окремо від коду,
бо `noter28/Wayly` приватний, а GitHub Pages на безкоштовному плані працює
лише для публічних репозиторіїв.

- Репозиторій: https://github.com/noter28/wayly-legal (публічний, GitHub Pages з `main`, `/`)
- Сайт: https://noter28.github.io/wayly-legal/
- Оферта: https://noter28.github.io/wayly-legal/oferta.html (+ `oferta.pdf`)
- Політика: https://noter28.github.io/wayly-legal/privacy.html (+ `privacy.pdf`)

Цей репозиторій — єдине джерело правди: зміни сюди, push у `main`,
Pages оновиться за хвилину. У репозиторії бота копій немає.

## Чого навмисно немає

У публічній версії прибрані РНОКПП, номер взяття на облік, домашня адреса й
телефон — лишились ПІБ ФОП, email і посилання на бота. Повні реквізити є в
оригінальних PDF (не публікуються). Якщо LiqPay чи банк вимагатимуть адресу
на сайті — вирішувати окремо (напр. юридична адреса замість домашньої).

PDF згенеровані з HTML:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless \
  --no-pdf-header-footer --print-to-pdf=oferta.pdf "file://$PWD/oferta.html"
```

## Де бот посилається на оферту

Гілка `feat/liqpay-support-payment` (LiqPay-інтеграція, на момент написання
ще не закомічена): `src/bot/utils/rating.py` — `OFFER_URL` і
`offer_note(button)`; рядок «Натискаючи «Підтримати»/«Оплатити», ви
погоджуєтесь з офертою» додається до `support_text()` (після поїздки) і
`owed_text()` (екран «оплатіть минулі»), у репозиторії `noter28/Wayly`. Обидва відправлення —
`parse_mode="HTML"`, `disable_web_page_preview=True`. Тест:
`test_every_pay_button_comes_with_the_offer` у `tests/bot/test_ratings.py`.

У `/start` посилання свідомо немає.

## Відкрите питання

Оферта п. 5.3: внесок добровільний, його відсутність «не тягне за собою жодних
обмежень». Режим LiqPay-гілки «спочатку оплатіть минулі поїздки» цьому
суперечить — перед його увімкненням треба змінити оферту тут.
