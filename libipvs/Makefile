# Makefile for libipvs

CC		= gcc
INCLUDE		= -I/usr/src/linux/include
CFLAGS		= -Wall -Wunused -Wstrict-prototypes -g -O2

INCLUDE		+= $(shell if [ -f ../../ip_vs.h ]; then	\
		     echo "-I../../."; fi;)
DEFINES		= $(shell if [ ! -f ../../ip_vs.h ]; then	\
		    echo "-DHAVE_NET_IP_VS_H"; fi;)

.PHONY		= all clean install dist distclean rpm rpms
STATIC_LIB	= libipvs.a

all:		$(STATIC_LIB)

$(STATIC_LIB):	libipvs.o
		ar rv $@ $^

%.o:		%.c
		$(CC) $(CFLAGS) $(INCLUDE) $(DEFINES) -c -o $@ $<

clean:
		rm -f *.[ao] *~ *.orig *.rej core

distclean:	clean
