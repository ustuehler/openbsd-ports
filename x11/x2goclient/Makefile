# $OpenBSD: Makefile,v 1.3 2017/07/26 22:45:34 sthen Exp $

COMMENT =	Qt4 client for the X2Go system

DISTNAME =	x2goclient-4.1.0.0
REVISION =	0

CATEGORIES =	x11

HOMEPAGE =	http://www.x2go.org

MAINTAINER =	Rafael Sadowski <rafael@sizeofvoid.org>

# GPLv2+
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += ICE QtGui QtNetwork QtSvg SM X11 Xext Xi Xinerama Xpm
WANTLIB += Xrender c cups fontconfig freetype ldap m pthread ssh
WANTLIB += ${COMPILER_LIBCXX}

MASTER_SITES =	http://code.x2go.org/releases/source/x2goclient/

MODULES +=	x11/qt4

LIB_DEPENDS +=	security/libssh \
		databases/openldap \
		print/cups,-libs

RUN_DEPENDS +=	x11/nx/nxcomp \
		x11/nx/nxproxy \
		shells/bash

DOCSDIR =	${PREFIX}/share/doc/x2goclient
EXAMPLESDIR =	${PREFIX}/share/examples/x2goclient

LRELEASE =	${LOCALBASE}/bin/lrelease4

do-configure:
	find ${WRKSRC} -type f -iname "*.cpp"  -exec \
		perl -pi -e 's,Q_OS_LINUX,Q_OS_UNIX,g;' \
		-e 's,#include <linux/fs.h>,,g;' {} \;
	find ${WRKSRC} -type f -iname "*.h" -exec \
		perl -pi -e 's,Q_OS_LINUX,Q_OS_UNIX,g;' \
		-e 's,#include <linux/fs.h>,,g;' {} \;
	sed -i -e 's,nxproxy -S nx,${LOCALBASE}/NX/bin/nxproxy -S nx,' \
		${WRKSRC}/src/onmainwindow.cpp
	cd ${WRKSRC} && ${LRELEASE} x2goclient.pro \
		&& ${MODQT4_QMAKE} x2goclient.pro

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/x2goclient ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/man/man1/x2goclient.1 ${PREFIX}/man/man1
	${INSTALL_DATA_DIR} ${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/LICENSE ${DOCSDIR}
	${INSTALL_DATA_DIR} ${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/examples/x2goclient-cli ${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/HOWTO.GPGCARD ${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/provider/etc/x2goplugin-apache.conf \
		${EXAMPLESDIR}

.include <bsd.port.mk>
