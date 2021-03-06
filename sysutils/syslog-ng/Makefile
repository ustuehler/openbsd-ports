# $OpenBSD: Makefile,v 1.57 2017/06/13 00:22:33 schwarze Exp $

COMMENT=	syslogd replacement

V =		3.9.1
REL =		3.9
DISTNAME =	syslog-ng-$V
REVISION =	0
CATEGORIES =	sysutils

MAINTAINER =	Steven Mestdagh <steven@openbsd.org>

HOMEPAGE =	https://syslog-ng.org/

# GPL v2
PERMIT_PACKAGE_CDROM =		Yes

MASTER_SITES =	http://github.com/balabit/syslog-ng/releases/download/${DISTNAME}/

SHARED_LIBS =	syslog-ng		4.0 \
		syslog-ng-${REL}	4.0

MODULES =	devel/gettext

WANTLIB =	c m pcre crypto ssl evtlog dbi ivykis pthread \
		glib-2.0 gmodule-2.0 gthread-2.0 json-c \
		curl nghttp2 z GeoIP

LIB_DEPENDS =	devel/glib2 \
		devel/json-c \
		devel/libivykis \
		sysutils/eventlog \
		databases/libdbi>=0.9.0 \
		net/curl \
		net/GeoIP

CONFIGURE_STYLE =	gnu
CONFIGURE_ARGS +=	--disable-tcp-wrapper \
			--with-pidfile-dir=/var/run \
			--enable-json \
			--with-mongoc=no \
			--with-librabbitmq-client=no \
			--disable-python \
			--disable-mongodb \
			--disable-amqp \
			--disable-stomp \
			--enable-geoip \
			--without-libnet \
			--with-ivykis=system \
			--with-libcurl=${LOCALBASE} \
			--enable-sql \
			--enable-manpages
CONFIGURE_ENV +=	OPENSSL_CFLAGS="-I/usr/include/openssl" \
			OPENSSL_LIBS="-lssl -lcrypto" 
# json-c only installs libjson-c.pc; syslog-ng checks for libjson.pc
CONFIGURE_ENV +=	JSON_C_CFLAGS="`pkg-config json-c --cflags`" \
			JSON_C_LIBS="`pkg-config json-c --libs`"
USE_GMAKE =	Yes

SYSCONFDIR =	${BASESYSCONFDIR}/syslog-ng
CFLAGS +=	-I${LOCALBASE}/include

SUBST_VARS +=	V

DOC =		${PREFIX}/share/doc/syslog-ng/
EXAMPLES =	${PREFIX}/share/examples/syslog-ng/

pre-install:
	cd ${WRKSRC}/doc/man && perl -pi -e 's@/opt/syslog\\-ng/etc/syslog\\-ng/@${SYSCONFDIR:S/-/\\-/g}/@g' *.[158]

post-install:
	mv ${WRKINST}/etc/syslog-ng ${EXAMPLES}
	${INSTALL_DATA} ${FILESDIR}/syslog-ng.conf \
		${EXAMPLES}/syslog-ng.conf.openbsd
	rm -rf ${PREFIX}/share/{include,tools,xsd}
	rm -f ${PREFIX}/lib/syslog-ng/*.{a,la}

.include <bsd.port.mk>
