# dwm - dynamic window manager
# See LICENSE file for copyright and license details.

include config.mk



# SET YOUR PATH OR SET ../
DWM_PATH = ../


SRC = ${DWM_PATH}/src/drw.c ${DWM_PATH}/src/dwm.c ${DWM_PATH}/src/util.c

OBJ_PATH = ${DWM_PATH}/make/object-files
OBJ = ${OBJ_PATH}/drw.o ${OBJ_PATH}/dwm.o ${OBJ_PATH}/util.o


all: config.h obj dwm

obj:
	[ -e object-files ] || mkdir object-files
	${CC} -c ${CFLAGS} ${SRC} 
	mv -v drw.o object-files/ 
	mv -v dwm.o object-files/ 
	mv -v util.o object-files/ 

${OBJ}: ${DWM_PATH}/config/config.h config.mk

config.h:
	[ -e ${DWM_PATH}/config/config.h ] || cp ${DWM_PATH}/config/config.def.h ${DWM_PATH}/config/$@

dwm: ${OBJ}
	[ -e bin ] || mkdir bin
	${CC} -o bin/$@ ${OBJ} ${LDFLAGS}

clean:
	rm -rf bin ${OBJ_PATH}

dist: clean
	echo '[skip] dist: clean '

install: all
	mkdir -p ${DESTDIR}${PREFIX}/bin
	cp -f bin/dwm ${DESTDIR}${PREFIX}/bin
	chmod 755 ${DESTDIR}${PREFIX}/bin/dwm

uninstall:
	rm -f ${DESTDIR}${PREFIX}/bin/dwm

.PHONY: all clean dist install uninstall
