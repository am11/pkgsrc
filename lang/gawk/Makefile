# $NetBSD: Makefile,v 1.71 2020/01/18 23:32:42 rillig Exp $

DISTNAME=	gawk-5.0.1
CATEGORIES=	lang
MASTER_SITES=	${MASTER_SITE_GNU:=gawk/}
EXTRACT_SUFX=	.tar.xz

MAINTAINER=	bouyer@NetBSD.org
HOMEPAGE=	https://www.gnu.org/software/gawk/gawk.html
COMMENT=	GNU awk
LICENSE=	gnu-gpl-v3

CONFLICTS=	ja-gawk-[0-9]*

USE_LIBTOOL=		yes
USE_PKGLOCALEDIR=	yes
USE_TOOLS+=		msgfmt msgmerge xgettext
GNU_CONFIGURE=		yes
TEST_TARGET=		check
INFO_FILES=		yes

MAKE_ENV+=		PKGLOCALEDIR=${PKGLOCALEDIR}

LDFLAGS.IRIX+=		-lgen
CPPFLAGS.OSF1+=		-D_OSF_SOURCE

.include "../../mk/bsd.prefs.mk"

.include "options.mk"

.if !empty(MACHINE_PLATFORM:MDarwin-*-x86_64)
CFLAGS+=	-Dvm_region=vm_region_64
.endif

PLIST_VARS+=		extension
.if "${OPSYS}" != "MirBSD"
PLIST.extension=	yes
.endif

INSTALLATION_DIRS+=	${PKGGNUDIR}bin ${PKGGNUDIR}${PKGMANDIR}/man1

post-install:
	${LN} -fs ${PREFIX}/bin/gawk ${DESTDIR}${PREFIX}/${PKGGNUDIR}bin/awk
	${LN} -fs ${PREFIX}/${PKGMANDIR}/man1/gawk.1 ${DESTDIR}${PREFIX}/${PKGGNUDIR}${PKGMANDIR}/man1/awk.1

BUILDLINK_API_DEPENDS.gettext+=	gettext-lib>=0.10.36

.include "../../devel/gettext-lib/buildlink3.mk"
.include "../../devel/gmp/buildlink3.mk"
.include "../../math/mpfr/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
