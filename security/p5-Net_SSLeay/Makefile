# $OpenBSD: Makefile,v 1.65 2017/03/28 23:56:44 bluhm Exp $

COMMENT =		perl module for using OpenSSL

DISTNAME =		Net-SSLeay-1.81

CATEGORIES =		security

HOMEPAGE =		http://alioth.debian.org/projects/net-ssleay

MAINTAINER =		Alexander Bluhm <bluhm@openbsd.org>

# Perl
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB =		c crypto perl ssl z

MODULES =		cpan
TEST_DEPENDS =		devel/p5-Test-Exception \
			devel/p5-Test-Warn \
			devel/p5-Test-NoWarnings \
			devel/p5-Test-Pod \
			devel/p5-Test-Pod-Coverage

MODCPAN_EXAMPLES =	Yes
SRCDIR = 		${WRKSRC}/${MODCPAN_EXAMPLES_DIST}

post-install:
	${MODCPAN_POST_INSTALL}
	${INSTALL_DATA} ${SRCDIR}/*.conf ${SRCDIR}/*.pem ${MODCPAN_EXAMPLES_DIR}

.include <bsd.port.mk>
