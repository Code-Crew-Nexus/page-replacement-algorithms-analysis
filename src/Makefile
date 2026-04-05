CC = gcc
CFLAGS = -Wall -std=c11 -D_GNU_SOURCE=1 -D__USE_MINGW_ANSI_STDIO=0

# Detect OS: Windows_NT vs Linux/Unix
ifeq ($(OS),Windows_NT)
	TARGET = page_replacement.exe
	RM = del
	RUN = $(TARGET)
else
	TARGET = page_replacement
	RM = rm -f
	RUN = ./$(TARGET)
endif

SRCS = main.c fifo.c lru.c optimal.c lfu.c utils.c
OBJS = $(SRCS:.c=.o)

all: $(TARGET)

$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) -o $(TARGET) $(OBJS)

clean:
	$(RM) $(OBJS) $(TARGET)

run: $(TARGET)
	$(RUN)
