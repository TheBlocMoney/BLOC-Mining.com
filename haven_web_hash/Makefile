TARGET = prog
LIBS = -lm
CC = emcc -O3 -s SINGLE_FILE=1  -s NO_FILESYSTEM=1  -s 'EXTRA_EXPORTED_RUNTIME_METHODS=["ccall", "cwrap"]'  --llvm-lto 1 -s TOTAL_MEMORY=67108864  -s WASM=1 -s "BINARYEN_TRAP_MODE='allow'"  -s EXPORTED_FUNCTIONS="['_hash_cn']"  --shell-file html_template/shell_minimal.html
CFLAGS =  -Wall -msse2


# SINGLE_FILE=1

# -s ASSERTIONS=1
#  -s SINGLE_FILE=1
.PHONY: default all clean

default: $(TARGET)
all: default

OBJECTS = $(patsubst %.cpp, %.o, $(wildcard *.cpp))
HEADERS = $(wildcard *.h)

%.o: %.cpp $(HEADERS) $(CC) $(CFLAGS) -c $< -o $@

.PRECIOUS: $(TARGET) $(OBJECTS)

$(TARGET): $(OBJECTS)
	$(CC) $(OBJECTS) -Wall $(LIBS) -o cn.html

clean:
	-rm -f *.o
	-rm -f $(TARGET)

