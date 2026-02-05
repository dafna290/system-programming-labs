Задание 1-4: Диагностика процессов<br>
Требования:<br>
•Используйте утилиты: ps, top, lsof, /proc, kill<br>
•Сохраните команды и результаты<br>

Вариант 6:<br>
1 Найти процессы systemd: ps aux | grep systemd<br>
2 Выбрать PID<br>
3 Вывести дерево: pstree -p [PID]<br>
4 Вывести /proc/[PID]/cmdline<br>
5 Сохранить в analysis.txt<br>

Используемые команды:<br>
ps aux | grep systemd - поиск процессов systemd<br>
pstree -p [PID] - отображение дерева процессов<br>
/proc/[PID]/ - виртуальная файловая система с информацией о процессах<br>
cat /proc/[PID]/cmdline - аргументы командной строки процесса<br>
head -10 /proc/[PID]/status - основные параметры статуса процесса<br>

Используемые утилиты:<br>
ps - отображение процессов<br>
pstree - отображение дерева процессов<br>
grep - поиск текста<br>
cat - вывод содержимого файлов<br>
head - вывод первых строк файла<br>

Пример вывода:<br>
Введите PID процесса systemd: 1<br>

Результаты сохранены в analysis.txt<br>

Содержимое analysis.txt:<br>
Процессы systemd:<br>
root          42  0.0  0.1  50428 15104 ?        S<s  15:29   0:00 /usr/lib/systemd/systemd-journald<br>
root          89  0.0  0.0  25276  6272 ?        Ss   15:29   0:02 /usr/lib/systemd/systemd-udevd<br>
systemd+     107  0.0  0.1  21460 12160 ?        Ss   15:29   0:00 /usr/lib/systemd/systemd-resolved<br>
systemd+     114  0.0  0.0  91028  7424 ?        Ssl  15:29   0:00 /usr/lib/systemd/systemd-timesyncd<br>
message+     169  0.0  0.0   9632  4608 ?        Ss   15:29   0:00 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only <br>   
root         179  0.0  0.1  17968  8320 ?        Ss   15:29   0:00 /usr/lib/systemd/systemd-logind<br>
dafna        349  0.0  0.1  20108 10880 ?        Ss   15:29   0:00 /usr/lib/systemd/systemd --user<br>
dafna       2715  0.0  0.0   2800  1664 pts/0    S+   18:06   0:00 sh -c -- ps aux | grep systemd<br>
dafna       2717  0.0  0.0   4088  1920 pts/0    S+   18:06   0:00 grep systemd<br>

Анализируем процесс с PID: 1<br>

Дерево процессов для PID 1:<br>
systemd(1)-+-agetty(192)<br>
           |-agetty(201)<br>
           |-cron(168)<br>
           |-dbus-daemon(169)<br>
           |-init-systemd(Ub(2)-+-SessionLeader(303)---Relay(305)(304)---bash(305)---task(2714)---sh(2718)---pstree(2719)<br>
           |                    |-init(6)---{init}(7)<br>
           |                    |-login(306)---bash(374)<br>
           |                    `-{init-systemd(Ub}(8)<br>
           |-polkitd(2307)-+-{polkitd}(2309)<br>
           |               |-{polkitd}(2310)<br>
           |               `-{polkitd}(2311)<br>
           |-rsyslogd(202)-+-{rsyslogd}(215)<br>
           |               |-{rsyslogd}(216)<br>
           |               `-{rsyslogd}(217)<br>
           |-systemd(349)---(sd-pam)(350)<br>
           |-systemd-journal(42)<br>
           |-systemd-logind(179)<br>
           |-systemd-resolve(107)<br>
           |-systemd-timesyn(114)---{systemd-timesyn}(164)<br>
           |-systemd-udevd(89)<br>
           |-unattended-upgr(209)---{unattended-upgr}(259)<br>
           `-wsl-pro-service(2673)-+-{wsl-pro-service}(2674)<br>
                                   |-{wsl-pro-service}(2675)<br>
                                   |-{wsl-pro-service}(2676)<br>
                                   |-{wsl-pro-service}(2677)<br>
                                   |-{wsl-pro-service}(2678)<br>
                                   |-{wsl-pro-service}(2679)<br>
                                   `-{wsl-pro-service}(2681)<br>

Содержимое /proc/1/cmdline:<br>
/sbin/init<br>

Статус процесса :<br>
Name:   systemd<br>
Umask:  0000<br>
State:  S (sleeping)<br>
Tgid:   1<br>
Ngid:   0<br>
Pid:    1<br>
PPid:   0<br>
TracerPid:      0<br>
Uid:    0       0       0       0<br>
Gid:    0       0       0       0
