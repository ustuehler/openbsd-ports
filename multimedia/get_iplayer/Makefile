# $OpenBSD: Makefile,v 1.106 2017/05/18 13:27:14 sthen Exp $

COMMENT=		download/stream programmes from BBC iPlayer

GH_ACCOUNT=		get-iplayer
GH_PROJECT=		get_iplayer
GH_TAGNAME=		v3.01

CATEGORIES=		multimedia

HOMEPAGE=		http://www.infradead.org/get_iplayer/

# GPLv3+
PERMIT_PACKAGE_CDROM=	Yes

MAINTAINER=		Stuart Henderson <sthen@openbsd.org>

RUN_DEPENDS=		graphics/ffmpeg \
			multimedia/atomicparsley \
			textproc/p5-XML-LibXML \
			textproc/p5-XML-Simple \
			www/p5-HTML-Parser>=3.71 \
			www/p5-LWP-Protocol-https \
			www/p5-Mojo \
			www/p5-libwww>=6.0

BUILD_DEPENDS=		${RUN_DEPENDS}

NO_TEST=		Yes
PKG_ARCH=		*

pre-configure:
	${SUBST_CMD} ${WRKSRC}/get_iplayer

do-build:
	-cd ${WRKSRC}; env -i HOME=${WRKSRC} ./get_iplayer --manpage get_iplayer.1

do-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/get_iplayer/plugins
	${SUBST_DATA} -m 644 \
	   ${FILESDIR}/options.sample ${PREFIX}/share/get_iplayer/options.sample
	${INSTALL_SCRIPT} ${WRKSRC}/get_iplayer ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/get_iplayer.1 ${PREFIX}/man/man1

#sed -i 's,2.95-dev,2.95-dev-${GH_COMMIT:C/(.{9}).*/\1/},' ${PREFIX}/bin/get_iplayer

.include <bsd.port.mk>
