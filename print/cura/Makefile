# $OpenBSD: Makefile.template,v 1.71 2014/07/10 12:33:17 sthen Exp $

COMMENT =		3d printing and slicing application

VERSION =		15.04.5-RC5
DISTNAME =		Cura-${VERSION}
PKGNAME =		cura-${VERSION}

CATEGORIES =		print

HOMEPAGE =		http://wiki.ultimaker.com/Cura

MAINTAINER =		Aaron Bieber <abieber@openbsd.org>

# AGPLv3
PERMIT_PACKAGE_CDROM =	Yes

GH_ACCOUNT =		daid
GH_PROJECT =		LegacyCura
GH_TAGNAME =		${VERSION}

MODULES =		lang/python

NO_BUILD =		Yes

BUILD_DEPENDS =		graphics/py-opengl \
			math/py-numpy \
			devel/py-serial \
			sysutils/py-power

RUN_DEPENDS =		print/curaengine \
			x11/py-wxPython

pre-configure:
	@echo ${VERSION} > ${WRKSRC}/resources/version

do-install:
	${INSTALL_DATA_DIR} \
		${PREFIX}/lib/python${MODPY_VERSION}/site-packages/Cura
	${INSTALL_DATA_DIR} \
		${PREFIX}/lib/python${MODPY_VERSION}/site-packages/Cura/resources
	cp -Rp ${WRKSRC}/Cura/* \
		${PREFIX}/lib/python${MODPY_VERSION}/site-packages/Cura
	cp -Rp ${WRKSRC}/resources/* \
		${PREFIX}/lib/python${MODPY_VERSION}/site-packages/Cura/resources
	${SUBST_CMD} -m 666 -c ${FILESDIR}/cura ${WRKSRC}/Cura/cura
	${INSTALL_SCRIPT} ${WRKSRC}/Cura/cura ${PREFIX}/bin/cura
	chown -R ${BINOWN}:${BINGRP} \
		${PREFIX}/lib/python${MODPY_VERSION}/site-packages/Cura

post-install:
	${MODPY_BIN} ${MODPY_LIBDIR}/compileall.py \
		${PREFIX}/lib/python${MODPY_VERSION}/site-packages/Cura

.include <bsd.port.mk>
