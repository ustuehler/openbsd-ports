# $OpenBSD: Makefile,v 1.23 2017/07/26 22:45:30 sthen Exp $

COMMENT=		implementation of the iCalendar protocols and data units

GH_ACCOUNT=		libical
GH_PROJECT=		libical
GH_TAGNAME=		v2.0.0
REVISION=		0

SHARED_LIBS +=  ical                 3.0
SHARED_LIBS +=  icalss               3.0
SHARED_LIBS +=  icalvcal             2.0
SHARED_LIBS +=  ical_cxx             0.0
SHARED_LIBS +=  icalss_cxx           0.0

CATEGORIES=		textproc

HOMEPAGE=		https://libical.github.io/libical/

# MPL/LGPLv2.1
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += icui18n icuuc m pthread ${COMPILER_LIBCXX}

MODULES=		devel/cmake

BUILD_DEPENDS=		devel/gobject-introspection

LIB_DEPENDS=		textproc/icu4c

CONFIGURE_ARGS=		-DGOBJECT_INTROSPECTION=true \
			-DUSE_INTEROPERABLE_VTIMEZONES=true

# the cmake MODULE sets it to Yes
SEPARATE_BUILD=		No

.include <bsd.port.mk>
