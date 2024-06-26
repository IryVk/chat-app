# Compiler
CXX = g++

# Compiler flags
CXXFLAGS = -Wall -std=c++17 -Wno-deprecated-declarations -I../../include -I/usr/include/crypto++ -pthread

# Linker flags
LDFLAGS = -lcrypto -lcryptopp -lgtest -lgtest_main -pthread -L../../lib

# Google Test include directory
GTEST_INCLUDE = -I../../lib/googletest/include

# Source directories
SERVER_SRC_DIR = ../../src/server
COMMON_SRC_DIR = ../../src/common

# Object directories
SERVER_OBJ_DIR = ../../obj/server
COMMON_OBJ_DIR = ../../obj/common

# Source files for testing 
TEST_SOURCES = $(wildcard *.cpp)
TEST_OBJECTS = $(patsubst %.cpp,%.o,$(TEST_SOURCES))

# Object files from client, server, and common
SERVER_OBJECTS = $(wildcard $(SERVER_OBJ_DIR)/*.o)
COMMON_OBJECTS = $(wildcard $(COMMON_OBJ_DIR)/*.o)

# Exclude the main object file if it exists
SERVER_MAIN_OBJ = $(SERVER_OBJ_DIR)/main.o

SERVER_OBJECTS := $(filter-out $(SERVER_MAIN_OBJ), $(SERVER_OBJECTS))

# Target executable for tests
TARGET = run_server_tests.exe

# Default rule
all: $(TARGET)

$(TARGET): $(TEST_OBJECTS) $(SERVER_OBJECTS) $(COMMON_OBJECTS)
	$(CXX) $(CXXFLAGS) $(GTEST_INCLUDE) -o $@ $^ $(LDFLAGS)
	./$@

%.o: %.cpp
	$(CXX) $(CXXFLAGS) $(GTEST_INCLUDE) -c $< -o $@

clean:
	rm -f *.o $(TARGET)
