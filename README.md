IP-туннель (VPN) с tun-интерфейсом на Python
============================================

Данный код был написан в рамках трансляции
(https://www.youtube.com/watch?v=tgXV1h_YMu4).



Тестирование
------------

Для тестирования используются Linux network namespaces и простой HTTP-сервер,
чтобы убедиться, что туннель работает.

### Подготовка

Команда `sudo ./test/prepare` создаст network namespaces и мост между ними.

### Запуск туннеля и HTTP-сервера

Каждую из этих команд нужно запустить в отдельном окне терминала
и не прерывать.

* `sudo ./test/tunnel_server`
* `sudo ./test/tunnel_client`
* `sudo ./test/http_server`

### Тестирование

Выполнение команды `sudo ./test/curl` должно вывести на экран сообщение
`Hello, World!`. Это означает, что HTTP-запросы передаются по нашему туннелю.

### Завершение

Завершите каждый из процессов, висящих в открытых окнах терминала, с помощью
сочетания клавиш **Ctrl+C** (иногда может потребоваться несколько нажатий).
Затем выполните команду `sudo ./test/cleanup` для удаления namespace'ов.
