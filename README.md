# Лабораторная работа №4
## Аксентьев Максим ИУ8-22
## CI Status
![CI](https://github.com/maksnn78/lab4/actions/workflows/ci.yml/badge.svg)
## Подготовка репозитория
```bash
git clone https://github.com/maksnn78/lab4.git
cd lab4
cp -r ~/lab3/* .
```
```bash
ls
```
```bash
CMakeLists.txt    hello_world_application  README.md
formatter_ex_lib  LICENSE                  solver_application
formatter_lib     preview.png              solver_lib
```
```bash
git add .
git commit -m "initial import from lab3"
```
```bash
[main (root-commit) d6fc47c] initial import from lab3
 17 files changed, 549 insertions(+)
 create mode 100644 CMakeLists.txt
 create mode 100644 LICENSE
 create mode 100644 README.md
 create mode 100644 formatter_ex_lib/CMakeLists.txt
 create mode 100644 formatter_ex_lib/formatter_ex.cpp
 create mode 100644 formatter_ex_lib/formatter_ex.h
 create mode 100644 formatter_lib/CMakeLists.txt
 create mode 100644 formatter_lib/formatter.cpp
 create mode 100644 formatter_lib/formatter.h
 create mode 100644 hello_world_application/CMakeLists.txt
 create mode 100644 hello_world_application/hello_world.cpp
 create mode 100644 preview.png
 create mode 100644 solver_application/CMakeLists.txt
 create mode 100644 solver_application/equation.cpp
 create mode 100644 solver_lib/CMakeLists.txt
 create mode 100644 solver_lib/solver.cpp
 create mode 100644 solver_lib/solver.h
```
```bash
git push -u origin main
```
```bash
Username for 'https://github.com': maksnn78
Password for 'https://maksnn78@github.com': 
Enumerating objects: 24, done.
Counting objects: 100% (24/24), done.
Delta compression using up to 4 threads
Compressing objects: 100% (24/24), done.
Writing objects: 100% (24/24), 1.01 MiB | 3.40 MiB/s, done.
Total 24 (delta 3), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (3/3), done.
To https://github.com/maksnn78/lab4.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```
## Настройка GitHub Actions
```bash
mkdir -p .github/workflows
nano .github/workflows/ci.yml
```
## CI конфигурация
```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Install dependencies
        run: sudo apt-get update && sudo apt-get install -y cmake g++

      - name: Configure project
        run: cmake -S . -B build

      - name: Build project
        run: cmake --build build
```
## Добавление CI в репозиторий
```bash
git add .github/workflows/ci.yml
git commit -m "add GitHub Actions CI"
```
```bash
[main 04dba28] add GitHub Actions CI
 1 file changed, 22 insertions(+)
```
```bash
git push origin main
```
```bash
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 566 bytes | 188.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/maksnn78/lab4.git
   d6fc47c..04dba28  main -> main
```
## Проверка локальной сборки
```bash
cmake -S . -B build
```
```bash
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 13.3.0
-- The CXX compiler identification is GNU 13.3.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
CMake Deprecation Warning at formatter_lib/CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Deprecation Warning at formatter_ex_lib/CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Deprecation Warning at solver_lib/CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Deprecation Warning at hello_world_application/CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Deprecation Warning at solver_application/CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (1.1s)
-- Generating done (0.0s)
-- Build files have been written to: /home/vboxuser/lab4/build
```
```bash
cmake --build build
```
```bash
[ 10%] Building CXX object formatter_lib/CMakeFiles/formatter.dir/formatter.cpp.o
[ 20%] Linking CXX static library libformatter.a
[ 20%] Built target formatter
[ 30%] Building CXX object formatter_ex_lib/CMakeFiles/formatter_ex.dir/formatter_ex.cpp.o
[ 40%] Linking CXX static library libformatter_ex.a
[ 40%] Built target formatter_ex
[ 50%] Building CXX object solver_lib/CMakeFiles/solver_lib.dir/solver.cpp.o
[ 60%] Linking CXX static library libsolver_lib.a
[ 60%] Built target solver_lib
[ 70%] Building CXX object hello_world_application/CMakeFiles/hello_world_application.dir/hello_world.cpp.o
[ 80%] Linking CXX executable hello_world_application
[ 80%] Built target hello_world_application
[ 90%] Building CXX object solver_application/CMakeFiles/solver_application.dir/equation.cpp.o
[100%] Linking CXX executable solver_application
[100%] Built target solver_application
```
