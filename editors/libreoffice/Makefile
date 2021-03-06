# $OpenBSD: Makefile,v 1.171 2017/08/13 17:12:48 robert Exp $

USE_WXNEEDED=	Yes

ONLY_FOR_ARCHS= amd64 i386

COMMENT-main=	multi-platform productivity suite
COMMENT-kde=	optional integration of LibreOffice to the KDE environment
COMMENT-java=	optional integration of LibreOffice java features

BV=		5.2
VERSION=	${BV}.7.2
REVISION=	1
REVISION-main=	5
DISTNAME=	libreoffice-${VERSION}
WRKDIST=	${WRKDIR}/libreoffice-${VERSION}
PKGNAME=	libreoffice-${VERSION}
PKGNAME-main=	libreoffice-${VERSION}
PKGNAME-kde=	libreoffice-kde-${VERSION}
PKGNAME-java=	libreoffice-java-${VERSION}
CATEGORIES=	editors productivity
DPB_PROPERTIES=	parallel tag:kde4

EPOCH=		0

MAINTAINER=	Robert Nagy <robert@openbsd.org>

HOMEPAGE=	http://www.libreoffice.org/

MASTER_SITES=	http://download.documentfoundation.org/libreoffice/src/${VERSION:C/^([0-9]+\.[0-9]+\.[0-9]+).*/\1/}/ \
		http://humppa.hu/libreoffice/ \
		http://download.go-oo.org/src/
MASTER_SITES0=	http://dev-www.libreoffice.org/src/ \
		http://hg.services.openoffice.org/binaries/ \
		http://download.go-oo.org/src/ \
		http://download.go-oo.org/extern/ \
		http://www.numbertext.org/linux/ \
		http://ooo.itc.hu/oxygenoffice/download/libreoffice/
MASTER_SITES1=	http://dev-www.libreoffice.org/src/libgltf/

TAR=		${LOCALBASE}/bin/gtar
EDISTFILES=	libreoffice-${VERSION}.tar.xz

COMPONENTS=	dictionaries help translations

.for _dfile in ${COMPONENTS}
EDISTFILES+=	libreoffice-${_dfile}-${VERSION}.tar.xz
.endfor
EXTRACT_ONLY=	${EDISTFILES:C/:[0-9]$//}

DISTFILES+=	${EDISTFILES} \
		boost_1_60_0.tar.bz2:0 \
		0168229624cfac409e766913506961a8-ucpp-1.3.2.tar.gz:0 \
		0279a21fab6f245e85a6f85fea54f511-source-code-font-1.009.tar.gz:0 \
		907d6e99f241876695c19ff3db0b8923-source-code-pro-2.030R-ro-1.050R-it.tar.gz:0 \
		048751f3271906db5126ab76870444c4-commons-codec-1.9-src.zip:0 \
		134d8262145fc793c6af494dcace3e71-liberation-fonts-ttf-1.07.4.tar.gz:0 \
		17410483b5b5f267aa18b7e00b65e6e0-hsqldb_1_8_0.zip:0 \
		ce12af00283eb90d9281956524250d6e-xmlsec1-1.2.20.tar.gz:0 \
		libcmis-0.5.1.tar.gz:0 \
		26b3e95ddf3d9c077c480ea45874b3b8-lp_solve_5.5.tar.gz:0 \
		2c9b0f83ed5890af02c0df1c1776f39b-commons-httpclient-3.1-src.tar.gz:0 \
		3404ab6b1792ae5f16bbd603bd1e1d03-libformula-1.1.7.zip:0 \
		35c94d2df8893241173de1d16b6034c0-swingExSrc.zip:0 \
		35efabc239af896dfb79be7ebdd6e6b9-gentiumbasic-fonts-1.10.zip:0 \
		368f114c078f94214a308a74c7e991bc-crosextrafonts-20130214.tar.gz:0 \
		39bb3fcea1514f1369fcfc87542390fd-sacjava-1.3.zip:0 \
		3bdf40c0d199af31923e900d082ca2dd-libfonts-1.1.6.zip:0 \
		a8c2c5b8f09e7ede322d5c602ff6a4b6-mythes-1.2.4.tar.gz:0 \
		5c781723a0d9ed6188960defba8e91cf-liberation-fonts-ttf-2.00.1.tar.gz:0 \
		7681383be6ce489d84c1c74f4e7f9643-liborcus-0.7.0.tar.bz2:0 \
		798b2ffdc8bcfe7bca2cf92b62caf685-rhino1_5R5.zip:0 \
		7a15edea7d415ac5150ea403e27401fd-open-sans-font-ttf-1.10.tar.gz:0 \
		8ab049135b2d15313da5d9f0656894a1-commons-lang3-3.3.1-src.tar.gz:0 \
		8ce2fcd72becf06c41f7201d15373ed9-librepository-1.1.6.zip:0 \
		97b2d4dba862397f446b217e2b623e71-libloader-1.1.6.zip:0 \
		5ade6ae2a99bc1e9e57031ca88d36dad-hyphen-2.8.8.tar.gz:0 \
		d8b5214d35bcd2bfcb2cffa7795b351d-dejavu-fonts-ttf-2.35.zip:0 \
		a7983f859eafb2677d7ff386a023bc40-xsltml_2.1.2.zip:0 \
		mdds-1.2.2.tar.bz2:0 \
		aa899eff126216dafe721149fbdb511b-liblangtag-0.5.8.tar.bz2:0 \
		language-subtag-registry-2016-07-19.tar.bz2:0 \
		cb4207cb913c7a5a8bfa5b91234618ee-mdds_0.11.2.tar.bz2:0 \
		ace6ab49184e329db254e454a010f56d-libxml-1.1.7.zip:0 \
		10d61fbaa6a06348823651b1bd7940fe-libexttextcat-3.4.4.tar.bz2:0 \
		ba2930200c9f019c2d93a8c88c651a0f-flow-engine-0.9.4.zip:0 \
		bae83fa5dc7f081768daace6e199adc3-glm-0.9.4.6-libreoffice.zip:0 \
		c3c1a8ba7452950636e871d25020ce0d-pt-serif-font-1.0000W.tar.gz:0 \
		c74b7223abe75949b4af367942d96c7a-crosextrafonts-carlito-20130920.tar.gz:0 \
		d62650a6f908e85643e557a236ea989c-vigra1.6.0.tar.gz:0 \
		d8bd5eed178db6e2b18eeed243f85aa8-flute-1.1.6.zip:0 \
		db60e4fde8dd6d6807523deb71ee34dc-liblayout-0.2.10.zip:0 \
		e7a384790b13c29113e22e596ade9687-LinLibertineG-20120116.zip:0 \
		commons-logging-1.2-src.tar.gz:0 \
		beeca87be45ec87d241ddd0e1bad80c1-bsh-2.0b6-src.zip:0 \
		edc4d741888bc0d38e32dbaa17149596-source-sans-pro-2.010R-ro-1.065R-it.tar.gz:0 \
		eeb2c7ddf0d302fba4bfc6e97eac9624-libbase-1.1.6.zip:0 \
		f94d9870737518e3b597f9265f4e9803-libserializer-1.1.6.zip:0 \
		4311dd9ace498b57c85f611e0670df64-graphite2-minimal-1.3.8.tgz:0 \
		libabw-0.1.1.tar.bz2:0 \
		libcdr-0.1.2.tar.bz2:0 \
		libe-book-0.1.2.tar.bz2:0 \
		libetonyek-0.1.6.tar.bz2:0 \
		libfreehand-0.1.1.tar.bz2:0 \
		libgltf-0.0.2.tar.bz2:1 \
		libmspub-0.1.2.tar.bz2:0 \
		libmwaw-0.3.7.tar.bz2:0 \
		libodfgen-0.1.6.tar.bz2:0 \
		libpagemaker-0.0.3.tar.bz2:0 \
		librevenge-0.0.4.tar.bz2:0 \
		libvisio-0.1.5.tar.bz2:0 \
		libwpd-0.10.0.tar.bz2:0 \
		libwpd-0.10.1.tar.bz2:0 \
		libwpg-0.3.1.tar.bz2:0 \
		libwps-0.4.3.tar.bz2:0

DIST_SUBDIR=	libreoffice

PERMIT_PACKAGE_CDROM=	Yes

MULTI_PACKAGES=		-main -java -kde

PSEUDO_FLAVORS=	parallel no_lang
FLAVORS=	debug no_java
FLAVOR?=

.if !${FLAVOR:Mno_lang}
LANGS=			ar bg ca de es fa fi fr hu it \
			kk lt lv nl pl pt-BR ru sl sv

CONFIGURE_ARGS+=	--with-lang="en-US ${LANGS}"
.for l in ${LANGS:L}
MULTI_PACKAGES+=	-i18n-$l
PKGNAME-i18n-$l=	libreoffice-i18n-$l-${VERSION}
COMMENT-i18n-$l=	$l language pack for LibreOffice
RUN_DEPENDS-i18n-$l=	editors/libreoffice
WANTLIB-i18n-$l=
LIB_DEPENDS-i18n-$l=
.endfor
.endif

BUILD_DEPENDS+=	archivers/zip \
		archivers/unzip \
		archivers/gtar \
		databases/db/v4 \
		devel/bison \
		devel/cppunit \
		devel/gpatch \
		devel/gperf \
		devel/libexecinfo \
		graphics/glew \
		shells/bash \
		archivers/p5-Archive-Zip \
		misc/findutils \
		print/poppler \
		security/nss \
		sysutils/coreutils \
		textproc/clucene \
		x11/gtk+3 \
		${MODGNU_AUTOCONF_DEPENDS} \
		${MODGNU_AUTOMAKE_DEPENDS}

# configure checks for librsvg support; no LIB/RUN_DEPENDS because libcups
# and librsvg is only dlopen()ed if found
BUILD_DEPENDS +=	x11/gnome/librsvg

COMPILER =	gcc

MODULES+=	lang/python \
		devel/gettext

# XXX can't use ${MODPY_DEFAULT_VERSION_3}, it specifically wants 3.3 and
# will try (and fail) to build its own copy if not available.
MODPY_VERSION=	${MODPY_DEFAULT_VERSION_3}


LIB_DEPENDS-main=x11/gtk+2 \
		${MODPY_LIB_DEPENDS} \
		databases/openldap \
		databases/postgresql \
		devel/harfbuzz,-icu \
		graphics/lcms2 \
		${MODGCC4_CPPLIBDEP} \
		print/cups,-libs \
		print/poppler \
		textproc/libxslt \
		textproc/raptor \
		net/curl \
		net/neon \
		textproc/icu4c \
		textproc/redland \
		textproc/hunspell

WANTLIB-main=	${COMPILER_LIBCXX} gdk-x11-2.0>=400.14 gtk-x11-2.0>=400.14 \
		xslt>=3 curl>=7 neon>=24 pq>=2 \
		icuuc>=0 icui18n \
		rdf>=0
WANTLIB-main+=	ICE SM X11 Xcomposite Xcursor Xdamage \
		Xext Xfixes Xi Xinerama Xrandr Xrender atk-1.0 c cairo \
		crypto expat fontconfig freetype gio-2.0 glib-2.0 \
		gobject-2.0 gthread-2.0 \
		jpeg m pango-1.0 pangocairo-1.0 pangoft2-1.0 \
		pthread ssl xml2 z gdk_pixbuf-2.0 \
		util ${MODGETTEXT_WANTLIB}
WANTLIB-main+=	hunspell-1.6
WANTLIB-main+=	${MODPY_WANTLIB}
WANTLIB-main+=	clucene-contribs-lib clucene-core clucene-shared
WANTLIB-main+=	cups exslt lcms2
WANTLIB-main+=	nspr4 nss3 plc4 plds4 smime3 softokn3 ssl3
WANTLIB-main+=	png raptor2
WANTLIB-main+=	lber ldap
WANTLIB-main+=	GLEW
WANTLIB-main+=	GL GLU harfbuzz harfbuzz-icu
WANTLIB-main+=	lzma
WANTLIB-main+=	cairo-gobject gmodule-2.0
WANTLIB-main+=	dconf gdk-3 gtk-3
WANTLIB-main+=	poppler

RUN_DEPENDS-main=	devel/desktop-file-utils \
			devel/libexecinfo \
			devel/xdg-utils \
			graphics/glew \
			misc/shared-mime-info \
			security/nss \
			textproc/clucene \
			x11/gtk+3 \
			x11/gtk+3,-guic

MODULES+=		x11/qt4
RUN_DEPENDS-kde=	editors/libreoffice
LIB_DEPENDS-kde=	x11/kde4/libs \
			${MODQT_LIB_DEPENDS} \
			${MODGCC4_CPPLIBDEP}
WANTLIB-kde+=		ICE SM Xext icuuc
WANTLIB-kde+=		GL GLEW GLU
WANTLIB-kde+=		X11 ${COMPILER_LIBCXX} glib-2.0 intl m pthread
WANTLIB-kde+=		QtCore QtGui QtNetwork kdecore kdeui kfile kio

.include <bsd.port.arch.mk>

.if ${BUILD_PACKAGES:M-java}
MODULES+=		java
MODJAVA_VER=		1.7+
MODJAVA_JRERUN=		Yes
.endif
LIB_DEPENDS-java=	${MODGCC4_CPPLIBDEP}
RUN_DEPENDS-java=	${MODJAVA_RUN_DEPENDS} \
			databases/db/v4,-java \
			editors/libreoffice \
			java/javaPathHelper
WANTLIB-java=		c ${COMPILER_LIBCXX} m pthread

USE_GMAKE=	Yes
NO_TEST=	Yes

PATCHORIG=	.orig.port

CONFIGURE_STYLE=	gnu

AUTOCONF_VERSION=	2.68
AUTOMAKE_VERSION=	1.12

CONFIGURE_ENV=	CPPFLAGS="-I${LOCALBASE}/include -I${X11BASE}/include" \
		LDFLAGS="-L${LOCALBASE}/lib -L${X11BASE}/lib" \
		KDE4INC="${LOCALBASE}/include/kde4" KDE4LIB="${LOCALBASE}/lib/kde4/libs"\
		QT4DIR="${LOCALBASE}/lib/qt4" QT4LIB="${LOCALBASE}/qt4" \
		QT4INC="${LOCALBASE}/include/X11/qt4"

CONFIGURE_ARGS+=\
		--disable-coinmp \
		--disable-collada \
		--disable-ccache \
		--disable-dbus \
		--disable-epm \
		--disable-fetch-external \
		--disable-odk \
		--disable-firebird-sdbc \
		--disable-mergelibs \
		--disable-dependency-tracking \
		--disable-online-update \
		--disable-orcus \
		--enable-gio \
		--enable-kde4 \
		--enable-systray \
		--enable-release-build \
		--enable-cairo-canvas \
		--with-alloc=system \
		--with-compat-oowrappers \
		--with-external-tar=${DISTDIR}/libreoffice \
		--with-fonts \
		--with-myspell-dicts \
		--with-system-harfbuzz \
		--with-system-glew \
		--with-system-clucene \
		--with-system-libxml \
		--without-system-boost \
		--with-system-cairo \
		--with-system-curl \
		--with-system-expat \
		--with-system-hunspell \
		--with-system-icu \
		--with-system-jars \
		--with-system-jpeg \
		--with-system-lcms2 \
		--with-system-libpng \
		--with-system-neon \
		--with-system-nss \
		--with-system-openldap \
		--with-system-openssl \
		--with-system-poppler \
		--with-system-postgresql \
		--with-system-redland \
		--with-system-zlib \
		--with-vendor="The OpenBSD project" \
		--without-junit \
		--without-krb5 \
		--without-gssapi \
		--without-system-apache-commons \
		--without-system-beanshell \
		--with-system-cppunit \
		--without-system-hsqldb \
		--without-system-jfreereport \
		--without-system-libwpd

.if ${BUILD_PACKAGES:M-java}
BUILD_DEPENDS+=	devel/apache-ant

CONFIGURE_ARGS+=--enable-ext-wiki-publisher \
		--with-java \
		--with-jdk-home=${JAVA_HOME} \
		--with-ant-home=${LOCALBASE}/ant
.else
CONFIGURE_ARGS+=--without-java
.endif

# XXX libreoffice has its own way to build things in parallel
PARALLEL_BUILD = No
.if defined(MAKE_JOBS)
NCPU=		${MAKE_JOBS}
.elif ${FLAVOR:Mparallel}
NCPU!=		echo $$((`sysctl -n hw.ncpu` + 1))
.else
NCPU=		1
.endif
CONFIGURE_ARGS+=--with-parallelism=${NCPU}

.if ${FLAVOR:Mdebug}
CONFIGURE_ARGS+=--enable-debug
.endif

MAKE_ENV+=	PYTHON="${MODPY_BIN}" verbose=f \
		AUTOCONF_VERSION=${AUTOCONF_VERSION} \
		AUTOMAKE_VERSION=${AUTOMAKE_VERSION}

.if ${MACHINE_ARCH} == "i386"
OA=		x86
.elif ${MACHINE_ARCH} == "amd64"
OA=		x86_64
.endif

SUBST_VARS+=	BV OA MODPY_DEFAULT_VERSION_3

pre-patch:
	@ln -fs /bin/md5 ${WRKDIR}/bin/md5sum
	@ln -fs /usr/local/bin/gfind ${WRKDIR}/bin/find
	@ln -fs /usr/local/bin/gpatch ${WRKDIR}/bin/patch
	@ln -fs /usr/local/bin/gcat ${WRKDIR}/bin/cat
	@ln -fs /usr/local/bin/gtouch ${WRKDIR}/bin/touch
	touch ${WRKSRC}/src.downloaded ${WRKSRC}/autogen.lastrun

pre-configure:
	${SUBST_CMD} ${WRKSRC}/configure ${WRKSRC}/shell/source/unix/exec/shellexec.cxx \
		${WRKSRC}/shell/source/unix/misc/senddoc.sh

post-install:
	${INSTALL_SCRIPT} ${FILESDIR}/soffice.sh ${PREFIX}/bin/soffice
	${SUBST_CMD} ${PREFIX}/bin/soffice
	rm ${PREFIX}/bin/soffice.beforesubst

	cd ${PREFIX}/bin && \
	for _a in sbase scalc sdraw simpress smath swriter \
		lobase localc lodraw loimpress lomath lowriter \
		oobase oocalc oodraw ooimpress oomath oowriter \
		libreoffice libreoffice${BV} soffice${BV} unopkg; do \
		ln -sf soffice $${_a}; done

	${INSTALL_DATA_DIR} ${PREFIX}/share/applications \
				${PREFIX}/share/icons \
				${PREFIX}/share/mime/packages

	for _d in calc draw impress math \
		qstart startcenter writer; do \
		sed -i "s,Icon=libreoffice${BV}-,Icon=libreoffice-,g" \
			${PREFIX}/lib/libreoffice/share/xdg/$${_d}.desktop && \
		ln -sf ${TRUEPREFIX}/lib/libreoffice/share/xdg/$${_d}.desktop \
			${PREFIX}/share/applications/$${_d}.desktop; done

	cp -R ${WRKSRC}/sysui/desktop/icons/hicolor ${PREFIX}/share/icons
	for _f in `find ${PREFIX}/share/icons/*/*/apps -type f`; \
		do mv $${_f} `echo $${_f} | sed "s,apps/,apps/libreoffice-,g"`; done

	${INSTALL_DATA} ${WRKSRC}/workdir/CustomTarget/sysui/share/libreoffice/openoffice.org.xml \
		${PREFIX}/share/mime/packages

# If the -java package does not get build use stub libraries for
# libjvmaccesslo.so and libjvmfwklo.so so that they can get included
# in the -main package because they are needed even if the -java
# subpackage is not installed.
.if !${BUILD_PACKAGES:M-java}
	echo "int main(void) { return 0; }" > ${WRKSRC}/stub.c
	${CC} -shared -o ${WRKBUILD}/stub.o ${WRKSRC}/stub.c
.  for i in jvmaccess jvmfwk
	${INSTALL_PROGRAM} ${WRKBUILD}/stub.o \
		${PREFIX}/lib/libreoffice/ure/lib/lib${i}lo.so
.  endfor
.endif

.include <bsd.port.mk>
