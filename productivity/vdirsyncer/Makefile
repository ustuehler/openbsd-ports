# $OpenBSD: Makefile,v 1.3 2017/07/17 00:09:56 danj Exp $

COMMENT =		synchronize calendars and contacts

MODPY_EGG_VERSION =	0.16.0
DISTNAME =		vdirsyncer-${MODPY_EGG_VERSION}
CATEGORIES =		productivity

HOMEPAGE =		https://vdirsyncer.pimutils.org/

MAINTAINER =		Remi Locherer <remi.locherer@relo.ch>

# BSD3
PERMIT_PACKAGE_CDROM =	Yes

MODULES =		lang/python

MODPY_VERSION=		${MODPY_DEFAULT_VERSION_3}
MODPY_PI =		Yes
MODPY_SETUPTOOLS =	Yes

BUILD_DEPENDS =		textproc/py-sphinx${MODPY_FLAVOR} \
			devel/py-setuptools_scm${MODPY_FLAVOR} \
			${RUN_DEPENDS}

RUN_DEPENDS =		devel/py-atomicwrites${MODPY_FLAVOR} \
			devel/py-click-log${MODPY_FLAVOR} \
			devel/py-click-threading${MODPY_FLAVOR} \
			www/py-requests-toolbelt${MODPY_FLAVOR}

post-build:
	cd ${WRKSRC}/docs; ${MAKE_ENV} PYTHONPATH=${WRKSRC} \
		sphinx-build${MODPY_BIN_SUFFIX} -b html -d _build/doctrees . _build/html

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/vdirsyncer
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/vdirsyncer
	cd ${WRKSRC}; ${INSTALL_DATA} AUTHORS.rst CHANGELOG.rst CONTRIBUTING.rst \
		ISSUE_TEMPLATE.md LICENSE README.rst ${PREFIX}/share/doc/vdirsyncer
	cd ${WRKSRC}/docs/_build/html && pax -rw * ${PREFIX}/share/doc/vdirsyncer
	${INSTALL_DATA} ${WRKSRC}/config.example \
		${PREFIX}/share/examples/vdirsyncer

.include <bsd.port.mk>
