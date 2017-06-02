INSTALL=/usr/bin/install
JAVA=java
TAR=tar
TARGET=shibboleth-embedded-ds-1.0.2
prefix=
sysconfdir=${prefix}/etc

all:

install:	index.html
	${INSTALL} -d $(DESTDIR)${sysconfdir}/shibboleth-ds
	${INSTALL} -m 644 *.txt *.html *.css *.js *.conf $(DESTDIR)${sysconfdir}/shibboleth-ds

clean:
	rm -rf ${TARGET}

kit:	clean
	mkdir ${TARGET}
	cat src/javascript/json2.js src/javascript/typeahead.js src/javascript/idpselect.js | ${JAVA} -jar build/yuicompressor-2.4.2.jar -o ${TARGET}/idpselect.js --type js
	cp Makefile shibboleth-embedded-ds.spec LICENSE.txt doc/*.txt src/resources/index.html src/resources/idpselect.css src/javascript/idpselect_config.js src/apache/*.conf ${TARGET}

dist:	kit
	${TAR} czf ${TARGET}.tar.gz ${TARGET}/*; rm -rf ${TARGET}
