CC = gcc
TARGET_A = libtan90common.a
TARGET_O = log.o tcpmap.o config.o common.o leakcheck.o

ifeq ($(opt), debug)
	CFLAGS = -std=gnu99 -W -Wall -Wextra -O3 `pkg-config --cflags glib-2.0` -DDEBUG -g
	LDFLAGS = -ltan90common -luv `pkg-config --libs glib-2.0` -luv -L../common -g
else
	CFLAGS = -std=gnu99 -W -Wall -Wextra -O3 `pkg-config --cflags glib-2.0`
	LDFLAGS = -ltan90common -luv `pkg-config --libs glib-2.0` -luv -L../common
endif

.PHONY : all clean

all : $(TARGET_A)

$(TARGET_A) : $(TARGET_O)
	ar rcv $(TARGET_A) $(TARGET_O)

log.o : log.c log.h
tcpmap.o : tcpmap.c tcpmap.h log.h
config.o : config.c config.h log.h
common.o : common.c common.h config.h tcpmap.h log.h
leakcheck.o : leakcheck.c leakcheck.h

clean : 
	rm -f $(TARGET_O) $(TARGET_A)