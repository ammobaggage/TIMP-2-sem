## Homework

1. Скачайте библиотеку *boost* с помощью утилиты **wget**. Адрес для скачивания `https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz`.

Комманда: ```wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz```

Вывод:
```
-2025-03-10 12:19:42--  https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABnzq6sI8W-Q-E5pZ9lM3Fc9o4hreI29RTs79rbD-cHjlTES1pnOmZQmWAJB_TXVE0vhA6fYfQVkMqMao-VfzSMzLP2ZQ%3D%3D&use_mirror=deac-riga&r=
Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 104.18.13.149, 104.18.12.149, 2606:4700::6812:d95, ...
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|104.18.13.149|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://deac-riga.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1 [following]
--2025-03-10 12:19:43--  https://deac-riga.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1
Resolving deac-riga.dl.sourceforge.net (deac-riga.dl.sourceforge.net)... 89.111.52.100
Connecting to deac-riga.dl.sourceforge.net (deac-riga.dl.sourceforge.net)|89.111.52.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 111710205 (107M) [application/x-gzip]
Saving to: ‘boost_1_69_0.tar.gz’

boost_1_69_0.tar.gz             2%[>                                                 ]   2.48M  3.19KB/s    eta 27m 24s 
```


2. Разархивируйте скаченный файл в директорию `~/boost_1_69_0`

Комманда: `tar -xf boost_1_69_0.tar.gz -C ~/boost_1_69_0`


3. Подсчитайте количество файлов в директории `~/boost_1_69_0` **не включая** вложенные директории.

Комманда: `find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l`

Вывод: `12`


4. Подсчитайте количество файлов в директории `~/boost_1_69_0` **включая** вложенные директории.

Комманда: `find ~/boost_1_69_0 -type f | wc -l`

Вывод: `61191`


5. Подсчитайте количество заголовочных файлов, файлов с расширением `.cpp`, сколько остальных файлов (не заголовочных и не `.cpp`).
#Заголовочные файлы имеют расширения .h и .hpp 

Комманда: `find ~/boost_1_69_0 -type f \( -name "*.h" -o -name "*.hpp" \) | wc -l`

Вывод: `15208`

#Количество файлов с разрешением .cpp

Комманда: `find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l`

Вывод: `13774`

#Остальные файлы (то-есть все, кроме тех, что имеют расширения: .cpp, .h, .hpp)

Комманда: `find ~/boost_1_69_0 -type f \( ! -name "*.h" -a ! -name "*.hpp" -a ! -name "*.cpp" \) | wc -l`

Вывод: `32209`


6. Найдите полный пусть до файла `any.hpp` внутри библиотеки *boost*.

Команда: `find ~/boost_1_69_0 -name "any.hpp"`

Вывод:
``` 
/home/opiates/boost_1_69_0/boost/any.hpp
/home/opiates/boost_1_69_0/boost/fusion/include/any.hpp
/home/opiates/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/opiates/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/opiates/boost_1_69_0/boost/type_erasure/any.hpp
/home/opiates/boost_1_69_0/boost/hana/any.hpp
/home/opiates/boost_1_69_0/boost/hana/fwd/any.hpp
/home/opiates/boost_1_69_0/boost/proto/detail/any.hpp
/home/opiates/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
/home/opiates/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
```


7. Выведите в консоль все файлы, где упоминается последовательность `boost::asio`.
Комманда: `grep -r "boost::asio" ~/boost_1_69_0 > result.txt`

[Вывод](https://gist.github.com/ammobaggage/19ee1d4695161a8dcf11cf6c995070ca)


8. Скомпилируйте *boost*. Можно воспользоваться [инструкцией](https://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html#or-build-custom-binaries) или [ссылкой](https://codeyarns.com/2017/01/24/how-to-build-boost-on-linux/).

Комманды:
```
cd boost_1_69_0
./bootstrap.sh
./b2 --prefix=boost install >> ~/ammobaggage/workspace/reports/lab01/zxc.txt
```
[Вывод](https://gist.github.com/ammobaggage/99e1b40229089e0ef27b8cc334f275e9)


9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`.

Комманды:
```
mkdir ~/boost-libs
cp lib/*.a ~/boost-libs
ls ~/boost-libs
```
Вывод:
```
libboost_atomic.a     libboost_filesystem.a  libboost_math_tr1l.a             libboost_stacktrace_basic.a
libboost_chrono.a     libboost_graph.a       libboost_prg_exec_monitor.a      libboost_stacktrace_noop.a
libboost_container.a  libboost_iostreams.a   libboost_program_options.a       libboost_system.a
libboost_context.a    libboost_math_c99.a    libboost_random.a                libboost_test_exec_monitor.a
libboost_contract.a   libboost_math_c99f.a   libboost_regex.a                 libboost_timer.a
libboost_date_time.a  libboost_math_c99l.a   libboost_serialization.a         libboost_unit_test_framework.a
libboost_exception.a  libboost_math_tr1.a    libboost_stacktrace_addr2line.a  libboost_wave.a
libboost_fiber.a      libboost_math_tr1f.a   libboost_stacktrace_backtrace.a  libboost_wserialization.a
```


10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.

Комманда: `du -ah ~/boost-libs`

Вывод:
```
544K    /home/opiates/boost-libs/libboost_math_c99.a
4.0K    /home/opiates/boost-libs/libboost_system.a
212K    /home/opiates/boost-libs/libboost_prg_exec_monitor.a
1.2M    /home/opiates/boost-libs/libboost_serialization.a
416K    /home/opiates/boost-libs/libboost_filesystem.a
356K    /home/opiates/boost-libs/libboost_iostreams.a
796K    /home/opiates/boost-libs/libboost_wserialization.a
4.0K    /home/opiates/boost-libs/libboost_stacktrace_noop.a
232K    /home/opiates/boost-libs/libboost_fiber.a
152K    /home/opiates/boost-libs/libboost_date_time.a
2.7M    /home/opiates/boost-libs/libboost_math_tr1l.a
2.7M    /home/opiates/boost-libs/libboost_math_tr1.a
20K     /home/opiates/boost-libs/libboost_stacktrace_backtrace.a
24K     /home/opiates/boost-libs/libboost_context.a
2.3M    /home/opiates/boost-libs/libboost_unit_test_framework.a
80K     /home/opiates/boost-libs/libboost_random.a
2.6M    /home/opiates/boost-libs/libboost_math_tr1f.a
3.2M    /home/opiates/boost-libs/libboost_regex.a
2.3M    /home/opiates/boost-libs/libboost_test_exec_monitor.a
464K    /home/opiates/boost-libs/libboost_math_c99l.a
56K     /home/opiates/boost-libs/libboost_timer.a
4.0K    /home/opiates/boost-libs/libboost_atomic.a
848K    /home/opiates/boost-libs/libboost_graph.a
448K    /home/opiates/boost-libs/libboost_math_c99f.a
24K     /home/opiates/boost-libs/libboost_stacktrace_addr2line.a
236K    /home/opiates/boost-libs/libboost_chrono.a
332K    /home/opiates/boost-libs/libboost_contract.a
16K     /home/opiates/boost-libs/libboost_stacktrace_basic.a
4.0K    /home/opiates/boost-libs/libboost_exception.a
148K    /home/opiates/boost-libs/libboost_container.a
1.6M    /home/opiates/boost-libs/libboost_program_options.a
4.5M    /home/opiates/boost-libs/libboost_wave.a
28M     /home/opiates/boost-libs
```


11. Найдите *топ10* самых "тяжёлых".

Комманда: `du -ah --apparent-size | sort -rh | head -n 10`

Вывод:
```
4.5M    ./libboost_wave.a
3.2M    ./libboost_regex.a
2.7M    ./libboost_math_tr1l.a
2.7M    ./libboost_math_tr1.a
2.6M    ./libboost_math_tr1f.a
2.3M    ./libboost_unit_test_framework.a
2.3M    ./libboost_test_exec_monitor.a
1.6M    ./libboost_program_options.a
1.2M    ./libboost_serialization.a
```


[Карев Георгий](https://github.com/ammobaggage)
ИУ8-21
