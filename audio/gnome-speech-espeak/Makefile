# $NetBSD: Makefile,v 1.17 2020/03/08 16:48:40 wiz Exp $
#

.include "../../audio/gnome-speech/Makefile.common"

PKGNAME=	${DISTNAME:S/speech/speech-espeak/}
PKGREVISION=	7
MAINTAINER=	pkgsrc-users@NetBSD.org
COMMENT=	GNOME 2 text-to-speech API

BUILD_DIRS=		drivers/espeak
INSTALL_DIRS=		drivers/espeak
CONFIGURE_ARGS+=	--with-espeak-dir=${LOCALBASE}

.include "../../audio/espeak/buildlink3.mk"
.include "../../audio/gnome-speech/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
