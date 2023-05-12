# Target library
lib := libuthread.a

# Compiler and flags
CC := gcc
CFLAGS := -Wall -Wextra -Werror -MMD -D_XOPEN_SOURCE
CFLAGS += -g

# Source files
SRCS := queue.c
OBJS := $(SRCS:.c=.o)

# Default target
all: $(lib)
deps := $(OBJS:.o=.d)
-include $(deps)

# Library target
$(lib): $(OBJS)
    @echo "Creating archive $@"
    $(Q)ar rcs $@ $^

# Object file targets
%.o: %.c
    @echo "CC    $@"
    $(Q)$(CC) $(CFLAGS) -c $< -o $@

# Clean target
clean:
    @echo "CLEAN"
    $(Q)rm -f $(OBJS) $(lib) $(OBJS:.o=.d)

Message @Realm2
