# Подключение к базе данных в кластере [!KEYREF MY]

Чтобы подключиться к кластеру БД с виртуальной машины Яндекс.Облака, эта машина должна находиться в той же сети Облака.

## Аутентификация

[!KEYREF MY]-кластеры [!KEYREF mmy-short-name] поддерживают только шифрованные соединения. Поэтому для подключения к такому кластеру необходим SSL-сертификат. Подготовить все нужные аутентификационные данные можно так:

    ```bash
    $ mkdir ~/.mysql
    $ wget "https://[!KEYREF s3-storage-host][!KEYREF pem-path]" -O ~/.mysql/root.crt
    $ chmod 0600 ~/.mysql/root.crt
    ```

## Строка подключения

Теперь вы можете подключиться к БД с помощью команды `mysql`:

```bash
$ mysql --host=<адрес хоста>
        --port=3306
        --ssl-ca=~/.mysql/root.crt
        --ssl-mode=REQUIRED
        --user=<имя пользователя базы данных>
        --password <имя базы данных>
```

Адреса всех хостов в кластере БД можно найти на странице нужного кластера в консоли управления.

