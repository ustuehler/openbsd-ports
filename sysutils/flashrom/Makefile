# $OpenBSD: Makefile,v 1.5 2017/05/18 15:29:35 sthen Exp $

ONLY_FOR_ARCHS=	i386 amd64

COMMENT=	flash-ROM programmer for BIOS etc

DISTNAME=	flashrom-0.9.9
REVISION=	1
EXTRACT_SUFX=	.tar.bz2

CATEGORIES=	sysutils

HOMEPAGE=	http://www.flashrom.org/

MAINTAINER=	Stuart Henderson <sthen@openbsd.org>

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB=	c ftdi usb-1.0 usb z

MASTER_SITES=	http://download.flashrom.org/releases/

# pciutils' libpci.a is linked statically; a patched version is required.
BUILD_DEPENDS=	sysutils/pciutils:patch
RUN_DEPENDS=	sysutils/dmidecode
LIB_DEPENDS=	devel/libusb-compat \
		devel/libftdi
MAKE_FLAGS=	LDFLAGS="-L./pciutils/lib" WARNERROR=no
FAKE_FLAGS=	PREFIX="${TRUEPREFIX}" MANDIR="${TRUEPREFIX}/man"

USE_GMAKE=	Yes
NO_TEST=	Yes

pre-patch:
	mv ${WRKDIR}/sysutils/pciutils/pciutils-* ${WRKSRC}/pciutils

do-configure:
	cd ${WRKSRC}/pciutils; ${MAKE_PROGRAM} CC="${CC}" OPT="${CFLAGS}"

.include <bsd.port.mk>
