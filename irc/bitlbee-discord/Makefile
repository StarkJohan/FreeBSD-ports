# $FreeBSD$

PORTNAME=	bitlbee-discord
PORTVERSION=	0.4.2
CATEGORIES=	irc

MAINTAINER=	arfy32@gmail.com
COMMENT=	Discord plugin for bitlbee

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	bitlbee:irc/bitlbee
LIB_DEPENDS=	libjson-glib-1.0.so:devel/json-glib

USES=		autoreconf gettext-runtime gnome libtool pkgconfig
USE_GNOME=	glib20
USE_GITHUB=	yes
GH_ACCOUNT=	sm00th

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-plugindir=${PREFIX}/lib/bitlbee
INSTALL_TARGET=	install-strip

PLIST_FILES=	lib/bitlbee/discord.so \
		share/bitlbee/discord-help.txt

.include <bsd.port.mk>
