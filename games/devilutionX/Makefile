# $FreeBSD$

PORTNAME=	devilutionX
PORTVERSION=	0.4.0
CATEGORIES=	games

MAINTAINER=	benny.goemans@gmail.com
COMMENT=	Open-source implementation of Diablo Game engine

LICENSE=	UNLICENSE

ONLY_FOR_ARCHS=	amd64 i386
ONLY_FOR_ARCHS_REASON=	Uses inline x86 assembly

LIB_DEPENDS=	libsodium.so:security/libsodium

USES=		cmake dos2unix sdl
USE_GCC=	yes
USE_SDL=	mixer2 sdl2 ttf2

PLIST_FILES=	bin/devilutionx

USE_GITHUB=	yes
GH_ACCOUNT=	diasurgical
GH_PROJECT=	devilutionX

OPTIONS_DEFAULT=	RELEASE

OPTIONS_SINGLE=		TYPE
OPTIONS_SINGLE_TYPE=	NIGHTLY RELEASE

RELEASE_DESC=	Build a release build
NIGHTLY_DESC=	Build a debug build

RELEASE_CMAKE_BOOL=	BINARY_RELEASE
NIGHTLY_CMAKE_BOOL=	NIGHTLY_BUILD

DESKTOP_ENTRIES=	"DevilutionX" \
			"" \
			"" \
			"devilutionx" \
			"Game;AdventureGame;" \
			false

.include <bsd.port.mk>
