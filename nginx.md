# Nginx
---

1. Вывод количества самых активных ip-адресов за последнее время из access.log

```
  less /var/log/nginx/access.log | cut -d' ' -f1 | sort | uniq -c
```
      

---

2. Чем ограничивается количество соединений соединений в nginx?
```
  # max clients = worker_connections * worker_processes
  # max clients is also limited by the number of socket connections available on the system (~64k)
```

---

3. В каком блоке задаётся worker_connections?
```
  events { }
```

---

4. Для чего используется модуль upstream в nginx?

```
  Описывает группу серверов. Серверы могут слушать на разных портах. Кроме того, можно одновременно использовать серверы, слушающие на TCP- и UNIX-сокетах.
```
  
---

5. Как настроить keep-alive для upstream в nginx?

```
  Указать директивы:
  proxy_http_version 1.1;
  proxy_set_header Connection "";

  upstream {
    hash $cookie_val consistent;
    keepalive 60; # for 30 upstreams;
  }
```

---

6. Методы балансировки в NGINX (не nginx+)
  - Round Robin.
  - Hash.
  - IP Hash.
  - Least Connections.
  - Random.
  - Least Time (только в платной версии NGINX).

---

7. Как ограничить количество соединений для сервера в upstream?
  Указать max_conns.

---

8. Для чего используется weight в nginx?
  Для указания приоретизации подключения.
