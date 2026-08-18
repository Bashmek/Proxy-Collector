# Proxy-Collect

Приложение для поиска и проверки **рабочих** Telegram MTProto прокси.

В отличие от простой проверки порта, здесь выполняется реальный MTProto-handshake (FakeTLS / obfuscated2 + `req_pq_multi`), как это делает клиент Telegram.

## Установка

```bash
pip install -r requirements.txt
```

## Использование

Собрать прокси из публичных источников и проверить их:

```bash
python -m proxy_collect
```

Проверить одну ссылку:

```bash
python -m proxy_collect --check "tg://proxy?server=example.com&port=443&secret=ee..."
```

Параметры:

| Параметр | Описание |
|----------|----------|
| `--source URL` | Добавить свой источник (можно несколько раз) |
| `--input file.txt` | Проверить прокси из локального файла |
| `--concurrency 40` | Параллельных проверок |
| `--limit 100` | Проверить только первые N прокси |
| `--output working_proxies.txt` | Файл с рабочими прокси |
| `--json report.json` | JSON-отчёт с задержкой и метаданными |
| `--quiet` | Вывести только рабочие ссылки |

## Источники по умолчанию

- [telegram-proxy-collector](https://github.com/kort0881/telegram-proxy-collector)
- [SoliSpirit/mtproto](https://github.com/SoliSpirit/mtproto)
- [free-mtproto-proxies](https://github.com/dubblebyte/free-mtproto-proxies)
- [iwh3n/tg-proxy](https://github.com/iwh3n/tg-proxy)

## Как использовать результат

Скопируйте строку из `working_proxies.txt` и откройте её в браузере или вставьте в Telegram: **Настройки → Данные и память → Прокси**.
