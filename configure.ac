### Process this file with autoconf to produce a configure script

AC_PREREQ([2.54])

m4_define([package_version], 0.1)

AC_INIT([MESS Desktop Entries], [package_version],
        [mbarnes@redhat.com], mess-desktop-entries)

AC_CONFIG_HEADER(config.h)

AM_INIT_AUTOMAKE
AM_MAINTAINER_MODE

# Automake 1.11 - Silent Build Rules
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

# Program Checks
AC_PROG_INSTALL
IT_PROG_INTLTOOL

# MIME Database
SHARED_MIME_INFO_MODULES="shared-mime-info >= 0.19"
PKG_CHECK_MODULES(SHARED_MIME_INFO, $SHARED_MIME_INFO_MODULES)

# MESS Program
AC_ARG_VAR([MESS], [MESS command])
AC_PATH_PROGS([MESS], [mess],, [$PATH:/usr/local/games:/usr/games])
if test "x$MESS" = "x"; then
        AC_MSG_ERROR([

        Unable to find the Multi Emulator Super System (MESS).

        Please install MESS, or specify the MESS command with
        a MESS environment variable.

        e.g. MESS=/path/to/program/mess ./configure
])
fi
AC_SUBST(MESS)

# Localization
AH_TEMPLATE(GETTEXT_PACKAGE, [Package name for gettext])
GETTEXT_PACKAGE=mess-desktop-entries
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE")
AC_SUBST(GETTEXT_PACKAGE)

AC_CONFIG_FILES([
        Makefile
        mess-dc.desktop.in
        mess-gameboy.desktop.in
        mess-gba.desktop.in
        mess-genesis.desktop.in
        mess-msx.desktop.in
        mess-n64.desktop.in
        mess-nes.desktop.in
        mess-sms.desktop.in
        mess-snes.desktop.in
        po/Makefile.in
])
AC_OUTPUT

echo
echo "    Configuration Summary"
echo "    ---------------------"
echo "    MESS Program : $MESS"
echo
