# $OpenBSD: Makefile,v 1.17 2017/07/18 18:48:18 ajacoutot Exp $

COMMENT=		unified interface for interacting with cloud services

MODPY_EGG_VERSION=	2.1.0
DISTNAME=		apache-libcloud-${MODPY_EGG_VERSION}
PKGNAME=		py-libcloud-${MODPY_EGG_VERSION}

CATEGORIES=		net

HOMEPAGE=		https://libcloud.apache.org/

MAINTAINER=		Antoine Jacoutot <ajacoutot@openbsd.org>

# Apache 2.0
PERMIT_PACKAGE_CDROM=	Yes

MASTER_SITES=		${MASTER_SITE_APACHE:=libcloud/}

MODULES=		lang/python

MODPY_SETUPTOOLS=	Yes

BUILD_DEPENDS=		devel/py-test-runner

RUN_DEPENDS=		sysutils/py-lockfile

# XXX needs https://pypi.python.org/pypi/requests-mock
TEST_DEPENDS=		devel/flake8 \
			devel/pep8 \
			devel/py-mock \
			devel/py-test-runner \
			sysutils/py-lockfile

# python2
RUN_DEPENDS +=		devel/py-backports-ssl-match-hostname
TEST_DEPENDS +=		devel/py-backports-ssl-match-hostname

post-install:
	rm -rf ${PREFIX}/lib/python${MODPY_VERSION}/site-packages/libcloud/test/

pre-test:
	cp ${WRKSRC}/libcloud/test/secrets.py-dist \
		${WRKSRC}/libcloud/test/secrets.py

.include <bsd.port.mk>
