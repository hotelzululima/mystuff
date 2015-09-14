# $OpenBSD: Makefile,v 1.2 2015/05/28 19:59:29 ajacoutot Exp $

DISTNAME =		yosys-0.0.1

COMMENT =		open synthesis suite
CATEGORIES =		devel

HOMEPAGE =		https://github.com/cliffordwolf/yosys

GH_COMMIT =		e7c018e5d14c3c609669ab514a7e9111ff006022
GH_ACCOUNT =		cliffordwolf
GH_PROJECT =		yosys

# ISC
PERMIT_PACKAGE_CDROM =	Yes

USE_GMAKE =		Yes

MAKE_ENV =		PYTHON="${MODPY_BIN}" \
			CXX="eg++"

MODULES =		gcc4 \
			lang/tcl

MODGCC4_ARCHS =		*
MODGCC4_LANGS =		c c++

SUBST_VARS +=		MODTCL_INCDIR

pre-configure:
	perl -pi -e s,'tclsh',${MODTCL_BIN},g ${WRKSRC}/Makefile
do-configure:
	cd ${WRKSRC} && gmake config-gcc

.include <bsd.port.mk>