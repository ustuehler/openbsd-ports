# $OpenBSD: Makefile,v 1.3 2016/03/20 19:56:45 naddy Exp $

COMMENT =		parse an email Received: header

MODULES =		cpan
PKG_ARCH =		*

DISTNAME =		Email-Received-1.00
CATEGORIES =		mail

MAINTAINER =		Marcus Glocker <marcus@nazgul.ch>

# Perl
PERMIT_PACKAGE_CDROM =	Yes

RUN_DEPENDS =		textproc/p5-Regexp-Common
BUILD_DEPENDS =		${RUN_DEPENDS}
TEST_DEPENDS =		mail/p5-Email-Simple

MAKE_ENV =		TEST_POD=Yes

.include <bsd.port.mk>
