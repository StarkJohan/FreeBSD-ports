# $FreeBSD$

PORTNAME=	knewstuff
DISTVERSION=	${KDE_FRAMEWORKS_VERSION}
PORTREVISION=	2
CATEGORIES=	devel kde kde-frameworks

MAINTAINER=	kde@FreeBSD.org
COMMENT=	KF5 library for downloading application assets from the network

USES=		cmake compiler:c++11-lib gettext kde:5 qt:5 tar:xz
USE_KDE=	archive attica5 auth codecs completion config \
		configwidgets coreaddons ecm i18n iconthemes itemviews \
		jobwidgets kio kirigami2 service sonnet textwidgets widgetsaddons \
		xmlgui
USE_QT=		buildtools_build concurrent core dbus declarative gui network \
		qmake_build widgets xml

.include <bsd.port.mk>
