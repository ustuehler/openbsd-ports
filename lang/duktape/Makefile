# $OpenBSD: Makefile,v 1.3 2017/07/29 21:33:45 fcambus Exp $

COMMENT =	embeddable JavaScript engine

DISTNAME =	duktape-2.1.1
EXTRACT_SUFX =	.tar.xz

CATEGORIES =	lang

HOMEPAGE =	http://duktape.org/

MAINTAINER =	Frederic Cambus <fcambus@openbsd.org>

# MIT
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB +=	c m

MASTER_SITES =	${HOMEPAGE}

MAKE_FLAGS =	CC="${CC}"

MAKE_FILE =	Makefile.cmdline

ALL_TARGET =	duk

NO_TEST =	Yes

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/duk ${PREFIX}/bin
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/duktape
	${INSTALL_DATA} ${WRKSRC}/mandel.js ${PREFIX}/share/examples/duktape

.include <bsd.port.mk>
