# Variables
CXX = g++
CXXFLAGS = -Wall -Wextra
SRCDIR = src
BUILDDIR = build
TARGET = my_project
TEST_TARGET = test_my_project

# Source files
SRC = $(SRCDIR)/main.cpp
TEST_SRC = tests/test_main.cpp

# Build directories
all: $(BUILDDIR)/$(TARGET) $(BUILDDIR)/$(TEST_TARGET)

$(BUILDDIR):
	mkdir -p $(BUILDDIR)

# Compile main project
$(BUILDDIR)/$(TARGET): $(SRC) | $(BUILDDIR)
	$(CXX) $(CXXFLAGS) $^ -o $@

# Compile test project
$(BUILDDIR)/$(TEST_TARGET): $(TEST_SRC) | $(BUILDDIR)
	$(CXX) $(CXXFLAGS) $^ -o $@

# Test the project
test: $(BUILDDIR)/$(TEST_TARGET)
	./$(BUILDDIR)/$(TEST_TARGET)

# Install the project
install: $(BUILDDIR)/$(TARGET)
	cp $(BUILDDIR)/$(TARGET) /usr/local/bin/

# Create a distributable tarball
dist: clean
	tar -czvf my_project.tar.gz src tests docs scripts README.md Makefile configure.ac Makefile.am

# Create documentation
docs:
	cat docs/manual.txt > manual_combined.txt

# Clean up
clean:
	rm -rf $(BUILDDIR)

distclean: clean
	rm -f my_project.tar.gz manual_combined.txt

# Help
help:
	@echo "Usage:"
	@echo "  make            - Build the project"
	@echo "  make test       - Run tests"
	@echo "  make install    - Install the project"
	@echo "  make dist       - Create a distributable tarball"
	@echo "  make docs       - Create documentation"
	@echo "  make clean      - Clean up build files"
	@echo "  make distclean  - Clean up all files"
	@echo "  make help       - Show this help message"

# Run external script
run_script:
	./scripts/my_script.sh

# Default target
.DEFAULT_GOAL := all
