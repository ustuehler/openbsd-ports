# $OpenBSD: Makefile,v 1.10 2017/07/26 22:45:23 sthen Exp $

COMMENT =	color correction utility for digital images
DISTNAME =	delaboratory-0.8
CATEGORIES =	graphics x11
REVISION =	3

HOMEPAGE =	https://code.google.com/p/delaboratory/

# GPLv3+
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += c iconv lzma m pthread ${COMPILER_LIBCXX} tiff wx_base wx_base_net wx_base_odbc
WANTLIB += wx_base_xml wx_gtk2_adv wx_gtk2_aui wx_gtk2_core wx_gtk2_dbgrid
WANTLIB += wx_gtk2_html wx_gtk2_qa wx_gtk2_richtext wx_gtk2_xrc xml2 z

MASTER_SITES =	${MASTER_SITE_GOOGLECODE:=delaboratory/}

LIB_DEPENDS =	converters/libiconv \
		textproc/libxml \
		x11/wxWidgets,-main

RUN_DEPENDS =	graphics/dcraw

USE_GMAKE =	Yes
MAKE_FLAGS =	CXX="${CXX}" OPTFLAGS="${CXXFLAGS}"

NO_TEST =	Yes

post-patch:
	sed -i "s,-Ofast,,g" ${WRKSRC}/Makefile

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/delaboratory ${PREFIX}/bin

.include <bsd.port.mk>
