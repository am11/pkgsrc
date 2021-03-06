# $NetBSD: Makefile,v 1.8 2019/10/21 22:11:34 adam Exp $

DISTNAME=		pelican-3.7.1
PKGREVISION=		1
GITHUB_PROJECT=		pelican
PKGNAME=		${PYPKGPREFIX}-${DISTNAME}
CATEGORIES=		www textproc
MASTER_SITES=		${MASTER_SITE_GITHUB:=getpelican/}
EXTRACT_SUFX=		.zip

MAINTAINER=		nils@NetBSD.org
HOMEPAGE=		https://blog.getpelican.com/
COMMENT=		Static site generator that supports Markdown and reST syntax
LICENSE=		gnu-agpl-v3

DEPENDS+=		${PYPKGPREFIX}-docutils-[0-9]*:../../textproc/py-docutils
DEPENDS+=		${PYPKGPREFIX}-markdown-[0-9]*:../../textproc/py-markdown
DEPENDS+=		${PYPKGPREFIX}-jinja2>=2.7:../../textproc/py-jinja2
DEPENDS+=		${PYPKGPREFIX}-pygments>=1.4:../../textproc/py-pygments
DEPENDS+=		${PYPKGPREFIX}-feedgenerator>=1.9:../../www/py-feedgenerator
DEPENDS+=		${PYPKGPREFIX}-pytz>=0a:../../time/py-pytz
DEPENDS+=		${PYPKGPREFIX}-blinker-[0-9]*:../../devel/py-blinker
DEPENDS+=		${PYPKGPREFIX}-Unidecode-[0-9]*:../../textproc/py-Unidecode
DEPENDS+=		${PYPKGPREFIX}-six>=1.4:../../lang/py-six
DEPENDS+=		${PYPKGPREFIX}-dateutil-[0-9]*:../../time/py-dateutil

PYTHON_VERSIONED_DEPENDENCIES=	sphinx:build

USE_TOOLS+=		bash:run make:build sed:build

REPLACE_PYTHON+=	pelican/tools/pelican_import.py
REPLACE_PYTHON+=	pelican/tools/pelican_quickstart.py
REPLACE_PYTHON+=	pelican/tools/pelican_themes.py
REPLACE_PYTHON+=	pelican/tools/templates/pelicanconf.py.in
REPLACE_PYTHON+=	pelican/tools/templates/publishconf.py.in

REPLACE_INTERPRETER+=	bash
REPLACE.bash.old=	/usr/bin/env bash
REPLACE.bash.new=	${TOOLS_PATH.bash}
REPLACE_FILES.bash=	pelican/tools/templates/develop_server.sh.in

SUBST_CLASSES+=		version
SUBST_STAGE.version=	pre-build
SUBST_MESSAGE.version=	Removing useless import of pelican.
SUBST_FILES.version=	docs/conf.py
SUBST_SED.version=	-e 's,from pelican,\#from pelican,g'
SUBST_SED.version+=	-e 's,release = __version__,release = "${PKGVERSION_NOREV}",g'

DOCDIR=			${PREFIX}/share/doc/pelican
INSTALLATION_DIRS+=	${PKGMANDIR}/man1/ ${DOCDIR}
MANPAGES=		pelican-themes.1 pelican-theming.1 pelican.1

TXTDOCFILES=		changelog.txt content.txt contribute.txt faq.txt \
			importer.txt index.txt install.txt internals.txt \
			pelican-themes.txt plugins.txt publish.txt quickstart.txt \
			report.txt settings.txt themes.txt tips.txt

AUTO_MKDIRS=		yes

post-build:
	cd ${WRKSRC}/docs/ && make SPHINXBUILD=${PREFIX}/bin/sphinx-build-${PYVERSSUFFIX} text man

post-install:
.for f in ${MANPAGES}
	${INSTALL_DATA} ${WRKSRC}/docs/_build/man/${f} ${DESTDIR}${PREFIX}/${PKGMANDIR}/man1/
.endfor
.for i in ${TXTDOCFILES}
	${INSTALL_DATA} ${WRKSRC}/docs/_build/text/${i} ${DESTDIR}${DOCDIR}/
.endfor

.include "../../lang/python/application.mk"
.include "../../lang/python/egg.mk"
.include "../../lang/python/versioned_dependencies.mk"
.include "../../mk/bsd.pkg.mk"
