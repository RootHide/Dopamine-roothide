TARGET = systemhook.dylib
CC = clang

CFLAGS = -Werror -I../_shared -I./src -isysroot $(shell xcrun --sdk iphoneos --show-sdk-path) -arch arm64e -miphoneos-version-min=15.0 -Wno-deprecated-declarations -Os -moutline
LDFLAGS = -dynamiclib

sign: $(TARGET)
	@strip -N $^
	@ldid -S $^

$(TARGET): $(wildcard src/*.c)
	$(CC) $(CFLAGS) $(LDFLAGS) -o $@ $^

clean:
	@rm -f $(TARGET)