# $OpenBSD: Makefile,v 1.32 2017/06/16 20:45:23 schwarze Exp $

COMMENT=	dropping jewels game for X11

DISTNAME=	xjewel-1.6
REVISION =	5
CATEGORIES=	games

MASTER_SITES=	ftp://ftp.warwick.ac.uk/pub/x11/
EXTRACT_SUFX=	.tar.z

PERMIT_PACKAGE_CDROM=	Yes

WANTLIB=		X11 Xau Xdmcp Xext c pthread-stubs xcb

MAKE_FLAGS=		HSCORE_FILE=/var/games/xjewel.scores \
			USERDEFS='-DICON_WINDOW -DUSE_SELECT -DGETPWENT' \
			BINDIR='${PREFIX}/bin' \
			MANDIR='${PREFIX}/man/man6' \
			MANSUFFIX=6 \
			FFILE=pcf.gz

CONFIGURE_STYLE=imake
NO_TEST=	Yes

pre-install:
	${INSTALL_DATA_DIR} ${PREFIX}/lib/xjewel.font
	@cd ${WRKSRC}/bitmaps; ${INSTALL_DATA} seven_seg.pcf.gz \
		${PREFIX}/lib/xjewel.font

post-install:
	@mv ${PREFIX}/bin/xjewel ${PREFIX}/bin/xjewel_; \
	  echo "#!/bin/sh"				>  ${PREFIX}/bin/xjewel; \
	  echo "xset +fp ${TRUEPREFIX}/lib/xjewel.font"	>> ${PREFIX}/bin/xjewel; \
	  echo "xjewel_"				>> ${PREFIX}/bin/xjewel; \
	  chmod ugo+x ${PREFIX}/bin/xjewel
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/xjewel
	${INSTALL_DATA} /dev/null ${PREFIX}/share/examples/xjewel/xjewel.scores

.include <bsd.port.mk>
