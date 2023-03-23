# Лабораторная работа №2

### Цель - изучение систем автоматизации сборки проекта на примере CMake

Создам *fork* репозитория lab03 (https://github.com/tp-labs/lab03)<br />
Создам локальный репозиторий и сделаю **pull**<br />
Установлю **cmake**: ```$ sudo apt istall cmake```

## Задание 1

Перейду в дирректорию: ```$ cd formatter_lib```<br />
Создам файл: ```$ touch CMakeLists.txt```<br />
Отредактирую его:
```
cmake_minimum_required(VERSION 3.2)

project(formatter_lib)

add_library(formatter STATIC formatter.h formatter.cpp)
```
Создаю директорию сборки и перехожу в нее:
```
$ mkdir build
$ cd build
```
Генерирую и линкую:
```
$ cmake ..
$ cmake --build . --config Release
```

## Задание 2

Перейду в директорию: ```$ cd formatter_ex_lib```<br />
Создам файл: ```$ touch CMakeLists.txt```<br />
Отредактирую его:
```
cmake_minimum_required(VERSION 3.2)

project(formatter_ex)

add_library(formatter_lib STATIC ../formatter_lib/formatter.cpp)

target_include_directories(formatter_lib PUBLIC ../formatter_lib)

add_library(formatter_ex_lib STATIC formatter_ex.h formatter_ex.cpp)

target_link_libraries(formatter_ex_lib formatter_lib)
```
Создаю директорию сборки и перехожу в нее:
```
$ mkdir build
$ cd build
```
Генерирую и линкую:
```
$ cmake ..
$ cmake --build . --config Release
```

## Задание 3

###Hello world

Перейду в дирректорию: ```$ cd hello_world_application```<br />
Создам файл: ```$ touch CMakeLists.txt```<br />
Отредактирую его:
```
cmake_minimum_required(VERSION 3.2)

project(Hello_World)

add_library(formatter_lib STATIC ../formatter_lib/formatter.cpp)

target_include_directories(formatter_lib PUBLIC ../formatter_lib)

add_library(formatter_ex_lib STATIC ../formatter_ex_lib/formatter_ex.cpp)

target_include_directories(formatter_ex_lib PUBLIC ../formatter_ex_lib)

add_executable(hello_world hello_world.cpp)

target_link_libraries(formatter_ex_lib formatter_lib)

target_link_libraries(hello_world formatter_ex_lib)
```
Создаю директорию сборки и перехожу в нее:
```
$ mkdir build
$ cd build
```
Генерирую и линкую:
```
$ cmake ..
$ cmake --build . --config Release
```

###Solver

Перейду в дирректорию: ```$ cd solver_application```<br />
Создам файл: ```$ touch CMakeLists.txt```<br />
Отредактирую его:
```
cmake_minimum_required(VERSION 3.2)

project(Solver)

add_library(formatter_lib STATIC ../formatter_lib/formatter.cpp)

target_include_directories(formatter_lib PUBLIC ../formatter_lib)

add_library(solver STATIC ../solver_lib/solver.cpp)

target_include_directories(solver PUBLIC ../solver_lib)

add_library(formatter_ex_lib STATIC ../formatter_ex_lib/formatter_ex.cpp)

target_include_directories(formatter_ex_lib PUBLIC ../formatter_ex_lib)

add_executable(solver_app equation.cpp)

target_link_libraries(formatter_ex_lib formatter_lib)

target_link_libraries(solver_app formatter_ex_lib)

target_link_libraries(solver_app solver)
```
Отредактирую файл /home/alina/lab3/solver_lib/solver.cpp, добавив ```#include <cmath>```, убрав ```std``` из строчек 15 и 16

Создаю директорию сборки и перехожу в нее
```
$ mkdir build
$ cd build
```
Генерирую и линкую:
```
$ cmake ..
$ cmake --build . --config Release
```
