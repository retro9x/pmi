# Init process for 32bit fn-dos.

VERSION = 0
PATCHLEVEL = 1
SUBLEVEL = 0
EXTRAVERSION =
#NAME = Init

# Make variables (CC, etc...)
AS	= as
LD	= ld
CC	= gcc
AR	= ar
MAKE	= make
NASM	= nasm
OBJCOPY	= objcopy
OBJDUMP	= objdump
LEX	= flex
YACC	= bison
PERL	= perl
PYTHON	= python
PYTHON2	= python2
PYTHON3	= python3
RUBY	= ruby



#CFLAGS = -m32 \
#	--std=gnu89 \
#	-nodefaultlibs \
#	-nostdinc \
#	-nostdlib \
#	-static \
#	-fgnu89-inline \
#	-ffreestanding \
#	-fno-builtin \
#	-fno-pie \
#	-no-pie \
#	-fno-stack-protector \
#	-s
	

CFLAGS = -m32 \
	-std=gnu89 \
	-nodefaultlibs \
	-nostdinc \
	-nostdlib \
	-static \
	-fgnu89-inline \
	-ffreestanding \
	-fno-builtin \
	-fno-pie \
	-fleading-underscore \
	-fno-stack-protector \
	-s \
	-Werror=strict-prototypes    


LIBC    =  ../../landlib/rtl/include/
LIBCOBJ =  ../../landlib/rtl/obj


#
# Objects
#

myObjects = crt0.o main.o \
ctype.o stdio.o stdlib.o string.o conio.o unistd.o \
termios.o ioctl.o fcntl.o rtl.o    


.PHONY: all all-c shell-link finalize clean

all: crt0.o main.o all-c shell-link finalize clean
	@echo "Init Ok?"
head.o:
# Nothing.
crt0.o:
#	gcc  -c  crt0.c -I $(LIBC) -I $(API) $(CFLAGS) -o crt0.o
main.o:
	$(CC)  -c  main.c -I $(LIBC) $(CFLAGS) -o main.o
all-c:

# We need some api and libc objects.

#obs: estamos usando um crt0.o compilado aqui mesmo.
	cp $(LIBCOBJ)/crt0.o .
	cp $(LIBCOBJ)/rtl.o .
	
	cp $(LIBCOBJ)/ctype.o .
	cp $(LIBCOBJ)/stdio.o .
	cp $(LIBCOBJ)/stdlib.o .
	cp $(LIBCOBJ)/string.o .
	cp $(LIBCOBJ)/conio.o .
	cp $(LIBCOBJ)/unistd.o .

	cp $(LIBCOBJ)/termios.o .
	cp $(LIBCOBJ)/ioctl.o .
	cp $(LIBCOBJ)/fcntl.o .
	
	#cp $(APIOBJ)/api.o .


shell-link:
	$(LD) -m elf_i386 -T ../applink.ld -o INIT.BIN $(myObjects)    

finalize:
#	cp INIT.BIN ../../bin/

clean:
	-rm *.o
#	-rm INIT.BIN 
	

