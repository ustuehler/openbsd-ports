# $OpenBSD: Makefile,v 1.53 2017/06/10 11:19:41 jasper Exp $

COMMENT=	monitoring and managing daemons utility

DISTNAME=	monit-5.23.0

CATEGORIES=	sysutils

HOMEPAGE=	http://www.mmonit.com/monit/

# AGPLv3+
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += c crypto m kvm pthread ssl z

MASTER_SITES=	${HOMEPAGE}/dist/

CONFIGURE_STYLE=gnu

SUBST_VARS=	LOCALSTATEDIR

pre-configure:
	${SUBST_CMD} ${WRKSRC}/monitrc

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/{doc,examples}/monit
	${INSTALL_DATA} ${WRKSRC}/README ${PREFIX}/share/doc/monit
	${INSTALL_DATA} ${WRKSRC}/monitrc ${PREFIX}/share/examples/monit

.include <bsd.port.mk>
