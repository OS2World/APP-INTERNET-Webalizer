#
# Makefile for webalizer - a web server log analysis program
#
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details (file "COPYING").
#

ETCDIR	= \"/mptn/etc\"
CC	= gcc
O	= -s -Os -mpentium -Zcrtdll -Zomf
INCDIRS	= -I../lpng108 -I../zlib -I../gd-1.8.3
LIBS	= -llibgd -lpng -lz -lm -lsocket -ldb
DEFS	= -DETCDIR=${ETCDIR}	\
	-DHAVE_ERRNO_H=1	\
	-DHAVE_SYS_SOCKET_H=1	\
	-DHAVE_GETOPT_H=1	\
	-DHAVE_MATH_H=1		\
	-DUSE_DNS		\
	-DOS2
#	-DOS2_RU
LDFLAGS= -L../gd-1.8.3 -L../lpng108 -L../zlib\
	-Zomf -Zsys -Zmap		\
	-Zlinker /ALIGN:1		\
	-Zlinker /NOIGNORECASE		\
	-Zlinker /EXEPACK:2		\
	-Zlinker /PACKCODE		\
	-Zlinker /PACKDATA		\
	-Zlinker /NOSECTORALIGNCODE	\
	-Zlinker /MAP

SRCS	= webalizer.c hashtab.c linklist.c preserve.c	\
	parser.c output.c graphs.c dns_resolv.c WebAlizer.Def
INCS	= webalizer.h hashtab.h linklist.h preserve.h parser.h	\
	output.h graphs.h lang.h webalizer_lang.h
OBJS=	${SRCS:.c=.obj}


# Shouldn't have to touch below here!

all: WebAlizer.Exe

WebAlizer.Exe:	${OBJS} ${INCS}
#	$(CC) -o WebAlizer ${OBJS} ${LDFLAGS} ${LIBS}
	$(CC) -o $@ ${OBJS} ${LDFLAGS} ${LIBS}

%.obj: %.c ${INCS}
	${CC} ${O} ${DEFS} ${INCDIRS} -c -o $@ $<
