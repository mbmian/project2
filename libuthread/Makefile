# Dependency tracking
# Target library
lib := libuthread.a

# Compiler and flags
CC := gcc
CFLAGS := -Wall -Wextra -Werror -MMD
CFLAGS += -g

# Source files
SRCS := queue.c
OBJS := $(SRCS:.c=.o)

# Test Source files
TEST_SRCS := queue_tester.c
TEST_OBJS := $(TEST_SRCS:.c=.o)
TEST_EXEC := queue_tester

# Default target
all: $(lib) $(TEST_EXEC)
deps := $(OBJS:.o=.d)
-include $(deps)

# Library target
$(lib): $(OBJS)
	@echo "Creating archive $@"
	$(Q)ar rcs $@ $^

# Object file targets
%.o: %.c
	@echo "CC	$@"
	$(Q)$(CC) $(CFLAGS) -c $< -o $@

# Test target
$(TEST_EXEC): $(TEST_OBJS) $(lib)
	@echo "LD	$@"
	$(Q)$(CC) $(CFLAGS) -o $@ $^

# Clean target
clean:
	@echo "CLEAN"
	$(Q)rm -f $(OBJS) $(lib) $(OBJS:.o=.d) $(TEST_OBJS) $(TEST_EXEC) $(TEST_OBJS:.o=.d)
