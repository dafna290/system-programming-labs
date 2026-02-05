Задание 2-2: Синхронизация с мьютексами<br>
Требования:<br>
•Используйте pthread_mutex_t<br>
•Функции: pthread_mutex_init(), pthread_mutex_lock(), pthread_mutex_unlock(), pt<br>
hread_mutex_destroy()<br>

Вариант 6: Глобальная переменная product=1. Создать 5 потоков. Каждый поток i<br>
умножает product*=i. С мьютексом результат 120 (5!)<br>

Используемые функции:<br>
pthread_mutex_init() - инициализация мьютекса<br>
pthread_mutex_lock() - блокировка мьютекса<br>
pthread_mutex_unlock() - разблокировка мьютекса<br>
pthread_mutex_destroy() - уничтожение мьютекса<br>

Инициализирует массив значений для потоков: {1, 2, 3, 4, 5}<br>
Инициализирует мьютекс с помощью pthread_mutex_init()<br>
Выводит начальное значение product<br>
В цикле создает 5 потоков с помощью pthread_create()<br>
В другом цикле ожидает завершения всех потоков с помощью pthread_join()<br>
Уничтожает мьютекс с помощью pthread_mutex_destroy()<br>
Выводит финальный результат<br>
Для запуска используется ./task<br>

Пример вывода:<br>
Начальное значение product = 1<br>

Поток для значения 1: product = 1<br>
Поток для значения 2: product = 2<br>
Поток для значения 3: product = 6<br>
Поток для значения 4: product = 24<br>
Поток для значения 5: product = 120<br>

Pезультат: product = 120
