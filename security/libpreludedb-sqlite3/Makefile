# $NetBSD: Makefile,v 1.37 2020/03/08 16:51:09 wiz Exp $
#

PKGNAME=		libpreludedb-sqlite3-${VERSION}
PKGREVISION=		34
COMMENT=		Sqlite3 plugin for LibPreludeDB

.include "../../security/libpreludedb/Makefile.common"

CONFIGURE_ARGS+=	--with-perl=no
CONFIGURE_ARGS+=	--with-python=no
CONFIGURE_ARGS+=	--with-mysql=no
CONFIGURE_ARGS+=	--with-postgresql=no

BUILD_DIRS=		plugins/sql

CONFIGURE_ARGS+=	--with-sqlite3=${BUILDLINK_PREFIX.sqlite3}

.include "../../databases/sqlite3/buildlink3.mk"
.include "../../security/libpreludedb/buildlink3.mk"
.include "../../mk/pthread.buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
