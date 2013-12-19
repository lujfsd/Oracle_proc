#/bin/make
CC=/usr/bin/gcc
PROC=/usr/bin/proc

PROC_FLAGS= code=ANSI_C line=yes 
PROC_LIB=/usr/lib/oracle/11.2/client64/lib
PROC_INCLUDE=/usr/include/oracle/11.2/client64/
PROC_CFLAGS= -I$(PROC_INCLUDE) -L$(PROC_LIB)
LIBFLAGS= -lpthread -lclntsh 
DEBUGFLAGS=-DDEBUG
CFLAGS=-O2 -Wall $(DEBUGFLAGS) 

TARGET=test
OBJS=operate_data.o

$(TARGET):$(OBJS)
	$(CC) -o $@ $(OBJS) $(PROC_CFLAGS) $(LIBFLAGS) 

.SUFFIXES:.pc .c .o
.pc.c:
	$(PROC) iname=$< $(PROC_FLAGS)
.c.o:
	$(CC) -c $(PROC_CFLAGS) $(CFLAGS) $<

clean:
	rm $(OBJS) $(TARGET) *.lis
