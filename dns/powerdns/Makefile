# $FreeBSD$

PORTNAME=	powerdns
DISTVERSION=	4.1.10
CATEGORIES=	dns ipv6
MASTER_SITES=	http://downloads.powerdns.com/releases/
DISTNAME=	pdns-${DISTVERSION}

MAINTAINER=	tremere@cainites.net
COMMENT=	Advanced DNS server with multiple backends including SQL

LICENSE=	GPLv2

BROKEN_powerpc64=	Does not build: undefined reference to std::__throw_out_of_range_fmt
BROKEN_sparc64=		Does not compile: error: to_string is not a member of std

LIB_DEPENDS=	libboost_serialization.so:devel/boost-libs

USES=		compiler:c++11-lib cpe gmake libtool localbase:ldflags pathfix \
		pkgconfig ssl tar:bzip2

USE_LDCONFIG=	YES
USE_RC_SUBR=	pdns
USE_SUBMAKE=	YES

GNU_CONFIGURE=	YES
CONFIGURE_ARGS=	--disable-static \
		--docdir="${PREFIX}/share/doc/powerdns" \
		--sysconfdir="${PREFIX}/etc/pdns" \
		--with-boost="${LOCALBASE}" \
		--with-dynmodules="pipe bind ${MODULES}" \
		--with-modules=""

INSTALL_TARGET=	install-strip
SCRIPTS_ENV=	CURDIR2="${.CURDIR}" DISTNAME="${DISTNAME}" MKDIR="${MKDIR}" \
		POWERDNS_OPTIONS="${POWERDNS_OPTIONS}" \
		WRKDIRPREFIX="${WRKDIRPREFIX}"

SUB_FILES=	pkg-message

OPTIONS_DEFINE=		DOCS EXAMPLES LUAJIT MYDNS MYSQL OPENDBX OPENLDAP \
			OPTALGO PGSQL PROTOBUF REMOTE SQLITE3 TINYDNS TOOLS \
			UNIXODBC
OPTIONS_DEFAULT=	MYSQL PGSQL SQLITE3

OPTIONS_GROUP=			EXPERIMENTAL REMOTEOPT
OPTIONS_GROUP_EXPERIMENTAL=	LUABACKEND
OPTIONS_GROUP_REMOTEOPT=	ZEROMQ

OPTIONS_SUB=	yes

LUABACKEND_DESC=	Lua backend
LUAJIT_DESC=		Use LuaJIT instead of Lua
MYDNS_DESC=		MyDNS backend
MYSQL_DESC=		MySQL backend
OPENDBX_DESC=		OpenDBX backend
OPENLDAP_DESC=		OpenLDAP backend
OPTALGO_DESC=		Enable optional algorithms (12, 15 & 16)
PGSQL_DESC=		PostgreSQL backend
PROTOBUF_DESC=		Protobuf support
REMOTEOPT_DESC=		Remote backend connectors
REMOTE_DESC=		Remote backend
SQLITE3_DESC=		SQLite 3 backend
TINYDNS_DESC=		TinyDNS backend
TOOLS_DESC=		Build extra tools
ZEROMQ_DESC=		Enable ZeroMQ connector (Implies REMOTE enabled)

LUABACKEND_VARS=	MODULES+=lua

LUAJIT_LIB_DEPENDS=	libluajit-5.1.so.2:lang/luajit
LUAJIT_USES_OFF=	lua
LUAJIT_CONFIGURE_WITH=	luajit

MYDNS_USES=		mysql
MYDNS_CONFIGURE_ON=	--with-mysql=${LOCALBASE}
MYDNS_VARS=		MODULES+=mydns

MYSQL_USES=		mysql
MYSQL_CONFIGURE_OFF=	--without-mysql
MYSQL_CONFIGURE_ON=	--with-mysql=${LOCALBASE}
MYSQL_VARS=		MODULES+=gmysql

OPENDBX_LIB_DEPENDS=	libopendbx.so:databases/opendbx
OPENDBX_VARS=		MODULES+=opendbx

OPENLDAP_USE=		OPENLDAP=YES
OPENLDAP_CXXFLAGS=	-DLDAP_DEPRECATED=1
OPENLDAP_VARS=		MODULES+=ldap

OPTALGO_LIB_DEPENDS=	libbotan-2.so:security/botan2 \
			libdecaf.so:security/libdecaf \
			libsodium.so:security/libsodium
OPTALGO_CONFIGURE_ON=	--enable-botan \
			--enable-libdecaf \
			--enable-libsodium

PGSQL_USES=		pgsql
PGSQL_CONFIGURE_ON=	--with-pg-config=${LOCALBASE}/bin/pg_config
PGSQL_VARS=		MODULES+=gpgsql

PROTOBUF_LIB_DEPENDS=		libprotobuf.so:devel/protobuf
PROTOBUF_CONFIGURE_WITH=	protobuf

REMOTE_VARS=	MODULES+=remote

SQLITE3_USES=	sqlite:3
SQLITE3_VARS=	MODULES+=gsqlite3

TINYDNS_LIB_DEPENDS=	libcdb.so:databases/tinycdb
TINYDNS_CONFIGURE_ON=	CDB_CFLAGS="-I${LOCALBASE}/include" \
			CDB_LIBS="-L${LOCALBASE}/lib -lcdb"
TINYDNS_VARS=		MODULES+=tinydns

TOOLS_CONFIGURE_ENABLE=	tools

UNIXODBC_LIB_DEPENDS=	libodbc.so:databases/unixODBC
UNIXODBC_VARS=		MODULES+=godbc

ZEROMQ_IMPLIES=		REMOTE
ZEROMQ_LIB_DEPENDS=	libzmq.so:net/libzmq4
ZEROMQ_CONFIGURE_ON=	--enable-remotebackend-zeromq

post-install::
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	@${STAGEDIR}${LOCALBASE}/sbin/pdns_server --module-dir=${STAGEDIR}${LOCALBASE}/lib/pdns --launch="pipe bind ${MODULES}" --config > ${STAGEDIR}${EXAMPLESDIR}/pdns.conf
	@${REINPLACE_CMD} -e 's;${STAGEDIR};;' -i '' ${STAGEDIR}${EXAMPLESDIR}/pdns.conf

.include <bsd.port.mk>
