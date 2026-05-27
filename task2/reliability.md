## Паттерны надёжности   
| Взаимодействие | Circuit breaker | Retry | Кэш | Идемпотентость |
| --- | --- | --- | --- | --- |
| API Gateway -> Ad Server | Размыкаем для некоторых DSP | Нет | Нет | Нет |
| Ad Server -> Auction Engine | Нет | Retry с фиксированной задержкой, тк важен быстрый отклик | Кэш кампаний |  Нет |
| Advertiser Dashboard -> Financial Service | Нет | Retry с exponential backoff + jitter | Нет | Есть, чтобы не списать несколько раз одно и то же |