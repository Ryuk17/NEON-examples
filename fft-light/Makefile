TARGET = fft_test

CC = arm-linux-gnueabihf-gcc

SRCDIR = src
OBJDIR = obj
BINDIR = bin

SRCS_c = $(wildcard $(SRCDIR)/*.c)
SRCS_cpp = $(wildcard $(SRCDIR)/*.cpp)
SRCS_S = $(wildcard $(SRCDIR)/*.s)

OBJS = $(SRCS_c:$(SRCDIR)/%.c=$(OBJDIR)/%_c.o) $(SRCS_cpp:$(SRCDIR)/%.cpp=$(OBJDIR)/%_cpp.o) $(SRCS_S:$(SRCDIR)/%.s=$(OBJDIR)/%_S.o)
rm = rm -f

CFLAGS = -Wall -g -O3 -march=armv7-a -mfpu=neon-vfpv4 -ffast-math -lm


$(BINDIR)/$(TARGET): $(OBJS)
	$(CC) $(OBJS) $(CFLAGS) -o $@

$(OBJDIR)/%_c.o : $(SRCDIR)/%.c
	$(CC) $(CFLAGS) -c $< -o $@
	
$(OBJDIR)/%_cpp.o : $(SRCDIR)/%.cpp
	$(CC) $(CFLAGS) -c $< -o $@

$(OBJDIR)/%_S.o : $(SRCDIR)/%.s
	$(CC) $(CFLAGS) -c $< -o $@

.PHONY: clean
clean:
	$(rm) $(OBJS)

.PHONY: remove
remove:
	$(rm) $(BINDIR)/$(TARGET)
	

