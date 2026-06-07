## Проектирование сервиса ставок

Сервис ставок (Auction Engine) получает на вход список ставок, на выход отдаёт победителя

### Границы и API

* Сервис ставок по протоколу OpenRTB принимает Bid Requests от внешних DMP
* Ранжирует по набору параметров ставки и выбирает победителя
* Отдает Bid Response по протоколу OpenRTB

```
BidsRequest {
    bids: [
        {
            bid_id,
            min_amount,
            banner_params: {
                height,
                width,
                ...
            },
            user_data: {
                user_id,
                device_type,
                location,
                ...
            }
        }
    ]
}

BidsResponse {
    bid_id,
    amount,
}
```

### Зависимости от других сервисов

Данные о ставках сервис получает из Postgres и из AdServer. Ставки кэшируются.

### Модель данных

```
Bid: {
    bid_id,
    min_amount,
    banner_params: {
        height,
        width,
        ...
    },
    user_data: {
        user_id,
        device_type,
        location,
        ...
    }
}
```