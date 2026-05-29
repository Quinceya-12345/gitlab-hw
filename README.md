# Домашнее задание к занятию "`Резервное копирование`" - `Локтева И.С.`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. В личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

**Команда для создания зеркальной копии с подсчетом хэш-суммы и исключением скрытых файлов:**
```bash
rsync -avc --delete --exclude=".*" ~/ /tmp/backup/
```

![Скриншот Latest Data](img/komanda.png)

![Скриншот Latest Data](img/rsync_result.png)




---

### Задание 2


---

## Задание 2. Скрипт и автоматизация через cron

**1. Код написанного скрипта (`backup_script.sh`):**
```bash
#!/bin/bash
rsync -ac --delete --exclude=".*" ~/ /tmp/backup/

if [ \$? -eq 0 ]; then
    logger "Backup successful: user home directory mirrored to /tmp/backup"
else
    logger "Backup failed: rsync encountered an error"
fi
```

**2. Настройка планировщика crontab (`crontab -l`):**
![Настройка crontab](img/crontab_config.png)

**3. Результат работы скрипта и запись в системном логе:**
![Запись в syslog](img/cron_log_result.png)


![Скриншот Latest Data](img/cron_log_result.png)
![Скриншот Latest Data](img/crontab_config.png)

