srcdir=.
top_srcdir=..
top_builddir=..

MODULES_DIR = ../modules

COREOBJ  = SS5Main.o 		\
         SS5Core.o 		\
         SS5Server.o 		\
         SS5Utils.o 		\
         SS5Thread.o		\
         SS5Debug.o		\
         SS5GSSApi.o		\
         SS5Modules.o

COMMONOBJ = ../common/SS5OpenLdap.o ../common/SS5Radius.o ../common/SS5MySql.o

SRV     = ss5srv
SRVOBJ  = SS5Srv.o


CFLAGS=-g -O2 -DLINUX -D_FILE_OFFSET_BITS=64 -I . -I ../include   
SRVCFLAGS=-g -O2 -DLINUX -D_FILE_OFFSET_BITS=64 -I . -I ../include 

LIBS = -lpthread -rdynamic -ldl -lssl -lldap -lpam -lpam_misc -lcrypto  

CC = gcc

all: ss5 $(SRV)

ss5:	$(COREOBJ)
	$(CC) $(CFLAGS) -o ss5 $(COREOBJ) $(COMMONOBJ) $(LIBS)

$(SRV):	$(SRVOBJ)
	$(CC) $(SRVCFLAGS) -o $(SRV) $(SRVOBJ) $(LIBS)



clean:
	rm -f $(COREOBJ)
	rm -f $(SRVOBJ)
	rm -f ss5
	rm -f ss5srv

distclean: clean
	rm -f Makefile
