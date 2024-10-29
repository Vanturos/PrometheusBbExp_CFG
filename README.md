# PrometheusBbExp_CFG
Данный репозиторий содержит конфигурационные файлы для **Prometheus** и **BlackBox Exporter**, которые позволяют мониторить метрики доступности ресурса `https://ptsecurity.com`.

Для их применения достаточно использовать флаг `--config.file=<config-name.yml>` при запуске blackbox и prometheus соответственно.
Для мониторинга используется HTTP probing — Blackbox Exporter выполняет HTTP-запросы к целевому сайту, проверяя его доступность и корректность ответа. 

В конфигурации Blackbox Exporter определены следующие параметры:
1. HTTP Method: используется метод GET, который подходит для базовой проверки доступности страницы.
2. Timeout: максимальное время ожидания ответа от сайта составляет 5 секунд. Если ответ не получен в течение этого времени, проверка считается неуспешной.
3. Valid HTTP Versions: проверка поддерживает версии HTTP/1.1 и HTTP/2, чтобы соответствовать современным стандартам и убедиться, что сервер работает с актуальными версиями протокола.
4. Valid Status Codes: в конфигурации по умолчанию ожидаются коды 2xx, указывающие на успешный ответ.

Модуль в используемый Blackbox Exporter - http_2xx - модуль настроен для выполнения HTTP-запросов, ожидая успешный ответ от целевого ресурса. Если ответ соответствует статусу 2xx, то проверка считается успешной.

Пример работы сбора метрик доступности, визуализированный с помощью grafana и dashboard[https://grafana.com/grafana/dashboards/7587-prometheus-blackbox-exporter/] для нее:
![image](https://github.com/user-attachments/assets/12b2e282-a146-415d-8667-3acb1d4d3185)
