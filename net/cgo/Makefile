# $OpenBSD: Makefile,v 1.7 2015/09/18 19:35:05 jasper Exp $

COMMENT =	simple terminal based gopher client
DISTNAME =	cgo-20170313

CATEGORIES =	net

GH_ACCOUNT =	kieselsteini
GH_PROJECT =	cgo
GH_COMMIT =	c1ed33645f4c2ee1d731258d8a2dc6cedb35eb90

HOMEPAGE =	https://github.com/kieselsteini/cgo/

# ISC
PERMIT_PACKAGE_CDROM =	Yes

WANTLIB += c

MAKE_FLAGS =	CC="${CC}" CFLAGS="${CFLAGS}"

ALL_TARGET =	default

NO_TEST =	Yes

pre-configure:
	sed -i "s,/etc,${SYSCONFDIR},g" ${WRKSRC}/cgo.1

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/cgo ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/cgo.1 ${PREFIX}/man/man1
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/cgo
	${INSTALL_DATA} ${WRKSRC}/cgorc ${PREFIX}/share/examples/cgo

.include <bsd.port.mk>
