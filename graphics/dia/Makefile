# $NetBSD: Makefile,v 1.106 2020/03/10 22:10:04 wiz Exp $

PKGREVISION= 15
.include "Makefile.common"

.include "options.mk"

# just to convert the manpage
BUILD_DEPENDS+=	docbook-xsl-[0-9]*:../../textproc/docbook-xsl

.include "../../sysutils/desktop-file-utils/desktopdb.mk"
.include "../../graphics/hicolor-icon-theme/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
