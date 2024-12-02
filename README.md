# Домашнее задание к занятию "`Zabbix`" - `Татаринцев Алексей`

---

### Задание 1
`Установите Zabbix Server с веб-интерфейсом`


1. `У меня установлен ubuntu 20.04,поэтому делаем конфигуратор на него и начинаю установку`
![1](https://github.com/Foxbeerxxx/zabbix/blob/main/img/img1.png)`
2. `Делаем все выполнения под Рутом`
```
sudo -s
```
3. `Устанавливаю на Ubuntu - Zabbix`
```
# wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu20.04_all.deb
# dpkg -i zabbix-release_latest_6.0+ubuntu20.04_all.deb
# apt update
```
4. `Устанавливаю Zabbix сервер и веб интерфейс`
```
# apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
```

5. `Создаю базу данных`
```
# sudo -u postgres createuser --pwprompt zabbix
# sudo -u postgres createdb -O zabbix zabbix
```
6. `Импортирую начальную схему`
```
# zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
```

7. `Запускаем процессы zabbiz сервера и агента`
```
# systemctl restart zabbix-server zabbix-agent apache2
# systemctl enable zabbix-server zabbix-agent apache2
```
8. `Переходим в браузере http://192.168.1.144/zabbix`

![2](https://github.com/Foxbeerxxx/zabbix/blob/main/img/img2.png)`

9. `Переходим к настройке через ВебМорду`

![3](https://github.com/Foxbeerxxx/zabbix/blob/main/img/img3.png)`
---

### Задание 2

`Установите Zabbix Agent на два хоста.`

1. `Добавляю новый хост для мониторинга`

![4](https://github.com/Foxbeerxxx/zabbix/blob/main/img/img4.png)`

2. `Опрос не проходит так как есть проблема в виде`
![5](https://github.com/Foxbeerxxx/zabbix/blob/main/img/img5.png)`

3. `Статус zabbix`
![6](https://github.com/Foxbeerxxx/zabbix/blob/main/img/img6.png)`

4. `Есть одно замечание если я  конфигурационном файле раскомментирую  пароль, то у меня служба не работает, не перезапускается ,если данная строчка в коментарии то все работает`
![6](https://github.com/Foxbeerxxx/zabbix/blob/main/img/img6.png)`






