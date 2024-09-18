bin_PROGRAMS = my_project
my_project_SOURCES = src/main.cpp src/my_project.h

prefix = /usr/local
bindir = $(prefix)/bin

# Тесты
TESTS = tests/test_main.cpp

# Цель для тестирования
check-local:
    @echo "Running tests..."
    g++ -o test_main tests/test_main.cpp
    ./test_main  # Запуск тестов

# Правила для создания дистрибутива
dist-hook:
    @echo "Creating distributable tarball..."
    $(MAKE) dist

# Правила для установки
install-exec-hook:
    @echo "Installing the project..."
    $(INSTALL_PROGRAM) my_project $(DESTDIR)$(bindir)

# Цель для создания документации
docs:
    @echo "Creating documentation..."
    @cat docs/manual.txt > combined_manual.txt

# Очистка проекта
clean-local:
    @echo "Cleaning up build files..."
    rm -rf *.o my_project

# Полная очистка проекта
distclean-local:
    @echo "Cleaning up all files..."
    rm -rf *.o *.tar.gz my_project build/* combined_manual.txt

# Запуск внешнего скрипта
run-script:
    @echo "Running external script..."
    ./scripts/my_script.sh

# Помощь (help)
help:
    @echo "Usage:"
    @echo "  make            - Build the project"
    @echo "  make test       - Run tests"
    @echo "  make install    - Install the project"
    @echo "  make dist       - Create a distributable tarball"
    @echo "  make docs       - Create documentation"
    @echo "  make clean      - Clean up build files"
    @echo "  make distclean  - Clean up all files"
    @echo "  make run-script - Run external script"
    @echo "  make help       - Show this help message"
