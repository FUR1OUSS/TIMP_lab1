**Лабораторная работа №1**

**1. Скачайте библиотеку boost с помощью утилиты wget.**

wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz

**2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0.**

tar -xvf boost_1_69_0.tar.gz

**3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.**

1. сменить директорию: cd ~/boost_1_69_0

2. tree -L 1

<img width="682" alt="Снимок экрана 2023-05-18 в 16 25 41" src="https://github.com/FUR1OUSS/TIMP_lab1/assets/82472327/f882c058-5697-46f3-9469-4f32836ef300">

**_7 директории и 12 файлов_**

**4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.**

tree

<img width="682" alt="Снимок экрана 2023-05-18 в 16 26 24" src="https://github.com/FUR1OUSS/TIMP_lab1/assets/82472327/ae1a42b7-8676-4e49-8479-ab2d78f01214">

**_5638 директорий и 61191 файлов_**

**5 Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).**

Для заголовочных файлов .h и .hpp, получим: find . -name "*.h" -o -name "*.hpp" | wc -l

<img width="567" alt="Снимок экрана 2023-05-18 в 16 29 21" src="https://github.com/FUR1OUSS/TIMP_lab1/assets/82472327/92403daa-9484-4fce-bd8f-4871be4556aa">

**_15208_**

Для файлов с расширением .cpp получим: find . -name "*.cpp" | wc -l

<img width="569" alt="Снимок экрана 2023-05-18 в 16 29 32" src="https://github.com/FUR1OUSS/TIMP_lab1/assets/82472327/375aa065-52f0-4eca-a37d-c8b6ecd899ec">

**_13774_**

Для остальных файлов получим: find . -not -name "*.h" -not -name "*.hpp" -not -name "*.cpp" | wc -l

<img width="570" alt="Снимок экрана 2023-05-18 в 16 29 59" src="https://github.com/FUR1OUSS/TIMP_lab1/assets/82472327/7340a590-f571-4db7-b2b6-bca1190105f0">

**_37847_**

**6. Найдите полный пусть до файла any.hpp внутри библиотеки boost.**

Сменить директорию на boost: cd boost

С помощью команды readlink -f any.hpp получим: **_/Users/admin/boost_1_69_0/boost/any.hpp_**

<img width="598" alt="Снимок экрана 2023-05-18 в 13 42 52" src="https://github.com/FUR1OUSS/TIMP_lab1/assets/82472327/08e57810-0fe7-405d-b28b-ab85883eabf4">

**7 Выведите в консоль все файлы, где упоминается последовательность boost::asio.**

grep -rl "boost::asio"

<img width="682" alt="Снимок экрана 2023-05-18 в 16 31 30" src="https://github.com/FUR1OUSS/TIMP_lab1/assets/82472327/98cedd04-217e-48c1-949b-00b62e07501d">

**8 Скомпилирутйе boost.**

Перейдем в директорию: cd boost_1_69_0/tools/build

Запустим файл bootstrap.sh: sh bootstrap.sh

Создадим файл куда установим bootstrap: mkdir output

Установим bootstrap: ./b2 install --prefix=output

**9 Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.**

mv output boost-libs

**10 Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.**

Перейдем в директорию: cd boost_1_69_0/tools/build/boost-libs

Найдем размер каждого файла: du -a

<img width="682" alt="Снимок экрана 2023-05-18 в 16 43 50" src="https://github.com/FUR1OUSS/TIMP_lab1/assets/82472327/12975eff-ebde-4443-ab6b-6a777e165a10">

**11 Найдите топ10 самых "тяжёлых".**

Воспользуемся предыдущей командой, но добавим sort по числовому значению: du -a | sort -n

<img width="682" alt="Снимок экрана 2023-05-18 в 16 44 33" src="https://github.com/FUR1OUSS/TIMP_lab1/assets/82472327/5950cd04-312a-4439-8f72-12722f0babc7">
