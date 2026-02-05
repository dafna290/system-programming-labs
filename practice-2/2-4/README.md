Задание 2-4: Отладка с strace<br>
Требования:<br>
•Используйте strace для анализа системных вызовов<br>
•Сохраните команды и результаты в analysis.txt<br>

Вариант 6: Использовать strace cat /etc/passwd. Найти вызовы read() и write().<br>
Подсчитать байты. Сравнить с размером файла ls -l /etc/passwd<br>

Инициализация файла анализа - создание файла analysis.txt<br>
Определение размера файла - использование ls -l /etc/passwd<br>
Трассировка системных вызовов - strace -e trace=read,write<br>
Анализ вызовов read() - фильтрация, извлечение и подсчет байт<br>
Анализ вызовов write() - аналогично для write<br>
Сравнение с фактическим размером - использование stat или ls<br>
Вывод результатов - отображение содержимого analysis.txt<br>
Запуск: chmod +x script.sh && ./script.sh<br>

Пример вывода:<br>
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\243\2\0\0\0\0\0"..., 832) = 832<br>
read(3, "# Locale name alias data base.\n#"..., 4096) = 2996<br>
read(3, "", 4096)                       = 0<br>
read(3, "root:x:0:0:root:/root:/bin/bash\n"..., 131072) = 1424<br>
write(1, "root:x:0:0:root:/root:/bin/bash\n"..., 1424) = 1424<br>
read(3, "", 131072)                     = 0<br>
+++ exited with 0 +++<br>
Анализ системных вызовов cat /etc/passwd<br>
Размер файла /etc/passwd:<br>
-rw-r--r-- 1 root root 1424 Feb  3 13:37 /etc/passwd<br>

Системные вызовы read() и write():<br>
root:x:0:0:root:/root:/bin/bash<br>
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin<br>
bin:x:2:2:bin:/bin:/usr/sbin/nologin<br>
sys:x:3:3:sys:/dev:/usr/sbin/nologin<br>
sync:x:4:65534:sync:/bin:/bin/sync<br>
games:x:5:60:games:/usr/games:/usr/sbin/nologin<br>
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin<br>
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin<br>
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin<br>
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin<br>
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin<br>
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin<br>
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin<br>
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin<br>
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin<br>
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin<br>
_apt:x:42:65534::/nonexistent:/usr/sbin/nologin<br>
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin<br>
systemd-network:x:998:998:systemd Network Management:/:/usr/sbin/nologin<br>
systemd-timesync:x:996:996:systemd Time Synchronization:/:/usr/sbin/nologin<br>
dhcpcd:x:100:65534:DHCP Client Daemon,,,:/usr/lib/dhcpcd:/bin/false<br>
messagebus:x:101:101::/nonexistent:/usr/sbin/nologin<br>
syslog:x:102:102::/nonexistent:/usr/sbin/nologin<br>
systemd-resolve:x:991:991:systemd Resolver:/:/usr/sbin/nologin<br>
uuidd:x:103:103::/run/uuidd:/usr/sbin/nologin<br>
landscape:x:104:105::/var/lib/landscape:/usr/sbin/nologin<br>
polkitd:x:990:990:User for polkitd:/:/usr/sbin/nologin<br>
dafna:x:1000:1000:,,,:/home/dafna:/bin/bash<br>

Подсчет байтов в вызовах read():<br>
read: 832 байт<br>
read: 2996 байт<br>
read: 1424 байт<br>

Подсчет байтов в вызовах write():<br>

Сравнение с размером файла:<br>
Размер /etc/passwd: 1424 байт
