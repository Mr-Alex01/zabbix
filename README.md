# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Столяренко Александр`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

`Приведите ответ в свободной форме........`

`apt install postgresql postgresql-contrib # установил из репозитория`
`systemctl enable postgresql` # добавил в автозагрузку
`sudo -u postgres psql -c "SELECT usename FROM pg_user;"`# проверил созданного пользователя

`wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.2+ubuntu24.04_all.deb` # добавил репозиторий zabbix последней версии

`dpkg -i zabbix-release_latest_7.2+ubuntu24.04_all.deb` # установил репозиторий zabbix

`apt update`

`apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent` # установил zabbix-сервер, апач, агент

`su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD'\'123456789\'';"'` # скрипт для создания пользователя zabbix

`su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'` # скрипт для создания базы данных zabbix

`sed -i 's/# DBPassword=/DBPassword=123456789/g' /etc/zabbix/zabbix_server.conf` # добавил пароль на вход в конфиг zabbix

`systemctl restart zabbix-server apache2` # ребут zabbix и апач

`systemctl enable zabbix-server apache2` # добавил их в автозагрузку

=== После входа на веб-интерефейс ===

`locale -a` # посмотрел существующие локали

`locale-gen en_US.UTF-8` # добавил отсутствующую локаль (при первой настройке zabbix была ошибка)

`systemctl restart apache2` # ребут апача


```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты`

![1](https://github.com/Mr-Alex01/zabbix/blob/main/img/Сохраненное%20изображение%202025-3-19_4-5-44.724.jpg)


---

### Задание 2

`Приведите ответ в свободной форме........`

`Разлил ubuntu на вторую машину для установки агента`

`sudo -s` # повышаю права

`wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.2+ubuntu24.04_all.deb` # добавил репозиторий zabbix-агента последней версии

`dpkg -i zabbix-release_latest_7.2+ubuntu24.04_all.deb` # установил репозиторий zabbix-агента

`apt update`

`apt install zabbix-agent` # установил zabbix-агент

`systemctl restart zabbix-agent` # запуск и перезапуск агента

`systemctl enable zabbix-agent` # добавление агента в автозагрузку

`cat /var/log/zabbix/zabbix_agentd.log` # просмотр логов агента

`nano /etc/zabbix/zabbix_agentd.conf` # правка файла, изменение сервера zabbix на нужный

`systemctl restart zabbix-agent` # ребут агента

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты

`Раздел Configuration > Hosts:`

![01](https://github.com/Mr-Alex01/zabbix/blob/main/img/1.jpg)

`Раздел Monitoring > Latest data для обоих хостов:`

![02](https://github.com/Mr-Alex01/zabbix/blob/main/img/2.jpg)

`Логи агента (там их миллион, выбрал где видно соединение):`

![03](https://github.com/Mr-Alex01/zabbix/blob/main/img/3.jpg)

`Логи агента (дополнительно):`

![04](https://github.com/Mr-Alex01/zabbix/blob/main/img/4.jpg)

`Логи агента (дополнительно):`

![05](https://github.com/Mr-Alex01/zabbix/blob/main/img/5.jpg)


---

### Задание 3

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`

### Задание 4

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`
