# API DOC
разница между PUT и PATCH: https://ru.stackoverflow.com/questions/1070324/%D0%A0%D0%B0%D0%B7%D0%BD%D0%B8%D1%86%D0%B0-%D0%BE%D1%82%D0%BB%D0%B8%D1%87%D0%B8%D1%8F-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-put-%D0%B8-patch-%D0%B2-rest
## api/shop-bot-web/list/
### GET
Возвращает список всякого говна что у нас есть на проекте
```json
{
    "Shop": [
        {
            "id": 1,
            "owner": 1,
            "created_at": "2022-03-27T14:00:44Z",
            "is_locked": false,
            "owner_username": "whomLZT",
            "is_owner": true,
            "title": "webxedv gay"
        },
        {
            "id": 3,
            "owner": 1,
            "created_at": "2022-03-27T14:01:37Z",
            "is_locked": true,
            "owner_username": "whomLZT",
            "is_owner": true,
            "title": "Заблокированный магазин"
        },
        {
            "id": 2,
            "owner": 1,
            "created_at": "2022-03-27T14:01:21Z",
            "is_locked": false,
            "owner_username": "whomLZT",
            "is_owner": true,
            "title": "Тестовый магазин"
        },
        {
            "id": 5,
            "owner": 1,
            "created_at": "2022-07-19T18:28:48.822622Z",
            "is_locked": false,
            "owner_username": "whomLZT",
            "is_owner": true,
            "title": "1231231"
        }
    ],
    "Bot": [
        {
            "shop": 2,
            "language": 1,
            "title": "Тестовый бот",
            "currency": 1,
            "display_item_out_of_stock": false,
            "display_item_quantity": false,
            "currency_display": "Рубли ₽",
            "language_display": "Русский",
            "id": 1,
            "shop_owner_username": "whomLZT",
            "is_owner": true,
            "is_locked": false,
            "created_at": "2022-05-17T22:27:32.983278Z",
            "active_users": 1,
            "all_users": 1
        },
        {
            "shop": 2,
            "language": 1,
            "title": "Test bot USD",
            "currency": 2,
            "display_item_out_of_stock": false,
            "display_item_quantity": false,
            "currency_display": "USD $",
            "language_display": "Русский",
            "id": 2,
            "shop_owner_username": "whomLZT",
            "is_owner": true,
            "is_locked": false,
            "created_at": "2022-05-17T22:27:32.983278Z",
            "active_users": 0,
            "all_users": 0
        }
    ]
}
```
## /api/shop/list/
### GET
Возвращает список магазинов в которых он модератор/админ
```json
[
    {
        "id": 1,
        "owner": 1,
        "created_at": "2022-03-27T14:00:44Z",
        "is_locked": false,
        "owner_username": "whomLZT",
        "is_owner": true,
        "title": "webxedv gay"
    },
    {
        "id": 2,
        "owner": 1,
        "created_at": "2022-03-27T14:01:21Z",
        "is_locked": false,
        "owner_username": "whomLZT",
        "is_owner": true,
        "title": "Тестовый магазин"
    },
    {
        "id": 3,
        "owner": 1,
        "created_at": "2022-03-27T14:01:37Z",
        "is_locked": true,
        "owner_username": "whomLZT",
        "is_owner": true,
        "title": "Заблокированный магазин"
    }
]
```
## /api/shop/create/
### POST
Создает новый магазин <br><br>
Запрос:
```json
{"title": "1231231"}
```



Ответ:
```json
{
    "id": 5,
    "created_at": "2022-07-19T18:28:48.822622Z",
    "is_locked": false,
    "owner_username": "whomLZT",
    "is_owner": true,
    "title": "1231231"
}
```
---
## /api/shop/update/{id}/
### GET or PUT or POST or DELETE
Детальная информация о магазине. 

Если у пользователя недостаточно прав для редактирования:<br> для примера - id: 4
```json
{
    "detail": "Not found."
}
```
Иначе:

Категории:
1 = 'Аккаунты'
2 = 'Еда' 
0 = 'Другое'

```json
{
    "id": 2,
    "owner": 1,
    "created_at": "2022-03-27T14:01:21Z",
    "is_locked": false,
    "owner_username": "whomLZT",
    "is_owner": true,
    "category": 1
}
```
### PUT or PATCH
Передача магазина другому пользователю.
```json
{"owner": 1}
```

### PUT or PATCH
Изменение категории 
```json
{"category": 2}
```
---
## /api/bot/list/
### GET
Список ботов привязанных к магазину
```json
[
    {
        "shop": 2,
        "language": 1,
        "title": "Тестовый бот",
        "currency": 1,
        "display_item_out_of_stock": false,
        "display_item_quantity": false,
        "currency_display": "Рубли ₽",
        "language_display": "Русский",
        "id": 1,
        "shop_owner_username": "whomLZT",
        "is_owner": true,
        "is_locked": false,
        "created_at": "2022-05-17T22:27:32.983278Z",
        "active_users": 1,
        "all_users": 1
    },
    {
        "shop": 2,
        "language": 1,
        "title": "Test bot USD",
        "currency": 2,
        "display_item_out_of_stock": false,
        "display_item_quantity": false,
        "currency_display": "USD $",
        "language_display": "Русский",
        "id": 2,
        "shop_owner_username": "whomLZT",
        "is_owner": true,
        "is_locked": false,
        "created_at": "2022-05-17T22:27:32.983278Z",
        "active_users": 0,
        "all_users": 0
    }
]
```
---
## /api/bot/update/{id}/
### PATCH or PUT or DELETE
Используется для изменения принадлежности бота к магазину и настроек валюты и языка бота.
```json
{
    "shop": 2,
    "language": 1,
    "title": "Новый бот",
    "currency": 1,
    "display_item_out_of_stock": false,
    "display_item_quantity": false,
    "token": "2095237739:AAF_3QyjhSVgiKGMtchDzQA1BiBNEI4321M"

}
```
### GET
```json
{
    "shop": 2,
    "language": 1,
    "title": "Тестовый бот",
    "currency": 1,
    "display_item_out_of_stock": false,
    "display_item_quantity": false,
    "currency_display": "Рубли ₽",
    "language_display": "Русский",
    "id": 1,
    "shop_owner_username": "whomLZT",
    "is_owner": true,
    "is_locked": false,
    "created_at": "2022-05-17T22:27:32.983278Z",
    "active_users": 1,
    "all_users": 2
}
```
---
## /api/bot/create/
### POST
Создание бота(нужно заполнять поля при создании)

Может возникнуть ошибка валидации токена!!!!
```json
{
    "shop": 2,
    "language": 1,
    "title": "Новый бот",
    "currency": 2,
    "display_item_out_of_stock": false,
    "display_item_quantity": false,
    "token": "2095237739:AAF_3QyjhSVgiKGMtchDzQA1BiBNEI4321M"
}
```
---
## api/category/list/{shop_id}/
### GET
Extend - продолжает категорию
Extend - null - корневая категория

В примере shop_id = 5
```json
[
    {
        "id": 1,
        "shop": 5,
        "title": "123213123",
        "extend": null,
        "extend_title": null
    },
    {
        "id": 2,
        "shop": 5,
        "title": "3123123",
        "extend": null,
        "extend_title": null
    }
]
```
## api/category/update/{id}/
### PUT or PATCH or DELETE
```json
{
    "id": 1,
    "shop": 5,
    "title": "123213123",
    "extend": null,
    "extend_title": null,
    "is_hidden": false
}
```
### GET
```json
{
    "id": 1,
    "shop": 5,
    "title": "123213123",
    "extend": null,
    "extend_title": null,
    "is_hidden": false
}
```
---
## api/category/create/
### POST
```json
{
    "shop": 5,
    "title": "3123123",
    "extend": null
}
```
---
## api/charts/shop/<int:pk>/orders_amount/<str:delta>/
### GET
delta - может принимать значения: "day" / "month"

Возвращает данные для highchart графика для оборота по заказам
```json
"chart_orders": {
"dates_list":[
"2021-09-04T09:09:09.034Z",
"2021-09-04T10:09:09.034Z",
"2021-09-04T11:09:09.034Z",
"2021-09-04T12:09:09.034Z",
"2021-09-04T13:09:09.034Z",
"2021-09-04T14:09:09.034Z",
"2021-09-04T15:09:09.034Z",
"2021-09-04T16:09:09.034Z",
"2021-09-04T17:09:09.034Z",
"2021-09-04T18:09:09.034Z",
"2021-09-04T19:09:09.034Z",
"2021-09-04T20:09:09.034Z",
"2021-09-04T21:09:09.034Z",
"2021-09-04T22:09:09.034Z",
"2021-09-04T23:09:09.034Z",
"2021-09-05T00:09:09.034Z",
"2021-09-05T01:09:09.034Z",
"2021-09-05T02:09:09.034Z",
"2021-09-05T03:09:09.034Z",
"2021-09-05T04:09:09.034Z",
"2021-09-05T05:09:09.034Z",
"2021-09-05T06:09:09.034Z",
"2021-09-05T07:09:09.034Z",
"2021-09-05T08:09:09.034Z"
],
"series":[
{
"name":"Заказы",
"data":[
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0
]
}
]
}
}
```
---
## charts/shop/<int:pk>/orders/<str:delta>/
### GET
delta - может принимать значения: "day" / "week" / "mouth"

Возвращает данные для highchart графика для числа заказов

```json
{
"chart_orders":{
"dates_list":[
"2021-09-04T09:13:04.319Z",
"2021-09-04T10:13:04.319Z",
"2021-09-04T11:13:04.319Z",
"2021-09-04T12:13:04.319Z",
"2021-09-04T13:13:04.319Z",
"2021-09-04T14:13:04.319Z",
"2021-09-04T15:13:04.319Z",
"2021-09-04T16:13:04.319Z",
"2021-09-04T17:13:04.319Z",
"2021-09-04T18:13:04.319Z",
"2021-09-04T19:13:04.319Z",
"2021-09-04T20:13:04.319Z",
"2021-09-04T21:13:04.319Z",
"2021-09-04T22:13:04.319Z",
"2021-09-04T23:13:04.319Z",
"2021-09-05T00:13:04.319Z",
"2021-09-05T01:13:04.319Z",
"2021-09-05T02:13:04.319Z",
"2021-09-05T03:13:04.319Z",
"2021-09-05T04:13:04.319Z",
"2021-09-05T05:13:04.319Z",
"2021-09-05T06:13:04.319Z",
"2021-09-05T07:13:04.319Z",
"2021-09-05T08:13:04.319Z"
],
"series":[
{
"name":"Заказы",
"data":[
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0
]
}
]
}
}
```
---
## charts/bot/<int:pk>/orders_bot/<str:delta>/
### GET
delta - может принимать значения: "day" / "week" / "mouth"

Возвращает данные для highchart графика для числа заказов
---
## charts/bot/<int:pk>/users/<str:delta>/
### GET
delta - может принимать значения: "day" / "week" / "mouth"

Возвращает данные для highchart графика для числа заказов
---
## /api/statistics/shop/{id}/
### GET

В примере id = 2
```json
{"paid_orders": 1, "sold_in_total": 2, "sold_for_a_total_of": "110"}
```

## /api/statistics/bot/{id}/

В примере id = 1
### GET
```json
{
    "paid_orders": 1,
    "sold_in_total": 11,
    "sold_for_a_total_of": "100.00",
    "active_users": 1,
    "all_users": 2
}
```

## api/order/last/{shop_id}/
### GET

В примере id = 2
```json
[
    {
        "id": 1,
        "product_title": "Тестовый товар",
        "user_username": "whom",
        "paid_at": "2021-07-21T16:23:01Z"
    },
    {
        "id": 2,
        "product_title": "Тестовый товар",
        "user_username": "whom",
        "paid_at": "2021-08-03T23:03:09Z"
    }
]
```

## api/order/list/{shop_id}/
### GET

В примере id = 2
```json
[
    {
        "id": 1,
        "user_username": "whomLZT",
        "product_title": "Укажите название товара.123",
        "product_type": 1,
        "status": 1,
        "amount": "100.00",
        "quantity": 11,
        "strings": "675675",
        "address": "Не указан",
        "full_name": "Не указано",
        "maiL_address": "Не указан",
        "phone_number": "Не указан"
    }
]
```

## order/list/my/
### GET
```json
[
    {
        "id": 1,
        "user_username": "whomLZT",
        "product_title": "Укажите название товара.123",
        "product_type": 1,
        "status": 3,
        "amount": "100.00",
        "quantity": 11,
        "strings": "675675",
        "address": "Не указан",
        "full_name": "Не указано",
        "maiL_address": "Не указан",
        "phone_number": "Не указан"
    }
]
```

## api/order/update/<int:pk>/
### GET
в примере pk=1
```json
{
    "id": 1,
    "user_username": "whomLZT",
    "product_title": "Укажите название товара.",
    "product_type": 1,
    "status": 2,
    "amount": "1.00",
    "quantity": 1,
    "strings": "123123",
    "address": "Не указан",
    "full_name": "Не указано",
    "mail_address": "Не указан",
    "phone_number": "Не указан",
    "created_at": "2022-03-03T14:38:25Z",
    "paid_at": "2022-03-03T14:38:25Z",
    "shop_title": "12312312"
}
```


## api/user/me/
### GET
```json
{
    "username_telegram": "whomLZT",
    "balance": 0.0,
    "purchases_worth": 500.0,
    "total_purchases": 2,
    "earned": 100.0
}
```

## api/user/list/{bot_id}/
### GET
В примере bot_id = 1
```json
[
    {
        "user": 1,
        "is_banned": false,
        "chat_id": 415924423,
        "username": null,
        "is_active": true
    },
    {
        "user": 4,
        "is_banned": false,
        "chat_id": 5316965624,
        "username": null,
        "is_active": false
    }
]
```
## api/user/list/{bot_id}/
### GET
response:
```json
[
  {
    "user":2,
    "is_banned":false,
    "chat_id":123,
    "username":"whom",
    "is_active":true
  }
]
```
## api/user/update/<int:bot_id>/<int:pk>/
### GET

```json
{
    "user": 2,
    "is_banned": false,
    "chat_id": null,
    "username": null,
    "is_active": true,
    "created_at": "2022-08-26T20:36:13Z",
    "balance": "0.00"
}
```
### PUT
```json
{
    "is_banned": true,
    "balance": "0.00"
}
```



## api/user/send_message/<int:user_id>/
### POST
request 
message = "Сообщение пользователю"

response
Удачно
```json
{"success": true}
```
Ошибки
```json
{
  "success": false, 
  "error": "Пользователь заблокирован"
}
```
```json
{
  "success": false,
  "error": "Пользователь заблокировал бота!"
}
```
```json
{
  "success": false,
  "error": "Пользователь не найден!"
}
```
```json
{
  "success": false,
  "error": "Сообщение не передано!"
}
```

## api/product/list/<shop_id>/
### GET
В примере shop_id = 2
```json
[
    {
        "id": 1,
        "title": "Тестовый товар",
        "shop": 2,
        "type": "Строковый (Цифровой)",
        "category": 6,
        "category_title": "12321312312 whom 12",
        "quantity": 1,
        "strings": "123",
        "price": "0.00",
        "is_hidden": false
    }
]
```

## api/product/update/<product_id>/
### GET
в примере id = 1
```json
{
    "id": 1,
    "title": "Укажите название товара.",
    "shop": 1,
    "type": "Строковый (Цифровой)",
    "category": null,
    "category_title": null,
    "quantity": 1,
    "strings": "123123123",
    "price": "100.00",
    "is_hidden": false,
    "message_after_purchase": "123123",
    "description": "Описание товара",
    "created_at": "2023-01-09T15:44:47.279561Z"
}
```

## api/notifications/list/
### GET
SUCCESS = (1, 'Success') <br>
ERROR = (2, 'Error')
```json
[
    {
        "id": 1,
        "title": "12312",
        "text": "3123213123",
        "type": 1,
        "created_at": "2022-05-18T19:31:56Z",
        "unread": false
    },
    {
        "id": 2,
        "title": "123213",
        "text": "23232323",
        "type": 2,
        "created_at": "2022-05-18T19:32:05Z",
        "unread": false
    }
]
```

## api/notifications/unread/
### GET

```json
{
    "unread_notifications": 0
}
```
