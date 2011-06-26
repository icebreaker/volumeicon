# Process this file with autoconf to produce a configure script
AC_INIT([volumeicon], [0.4.1], [http://www.softwarebakery.com/maato/volumeicon.html])

AM_INIT_AUTOMAKE

# Check for programs
AC_LANG([C])
AC_PROG_CC

# Check for functions and types
AC_CHECK_HEADERS([stdlib.h])
AC_C_CONST
AC_FUNC_MALLOC
AC_TYPE_PID_T
AC_TYPE_SIGNAL
AC_FUNC_FORK

# Checks for command line options
AC_ARG_ENABLE([oss],
  [  --disable-oss    disable oss],
  [oss=${enableval}],
  [oss=no])
AC_ARG_ENABLE([notify],
  [  --disable-notify    disable notify],
  [notify=${enableval}],
  [notify=no])

# Check for gtk
PKG_CHECK_MODULES([GTK], [gtk+-2.0 >= 2.16])
AC_SUBST(GTK_CFLAGS)
AC_SUBST(GTK_LIBS)

if test "x${oss}" = xno; then
# Check for alsa
PKG_CHECK_MODULES([ALSA], [alsa])
AC_SUBST(ALSA_CFLAGS)
AC_SUBST(ALSA_LIBS)
OSS_CFLAGS=""
else
AC_CHECK_FILE([/usr/lib/oss/include/sys/soundcard.h], [], [AC_MSG_ERROR([The file /usr/lib/oss/include/sys/soundcard.h does not exist.])])
OSS_CFLAGS="-DCOMPILEWITH_OSS"
fi

if test "x${notify}" = xyes; then
# Check for libnotify
AC_CHECK_FILE([/usr/include/libnotify/notify.h], [], [AC_MSG_ERROR([The file /usr/include/libnotify/notify.h does not exist.])])
NOTIFY_CFLAGS="-DCOMPILEWITH_NOTIFY"
NOTIFY_LIBS="-lnotify"
fi

AC_SUBST(OSS_CFLAGS)
AC_SUBST(NOTIFY_CFLAGS)
AC_SUBST(NOTIFY_LIBS)

AM_CONDITIONAL(ENABLE_OSS, test "$oss" = "yes")
AM_CONDITIONAL(ENABLE_NOTIFY, test "$notify" = "yes")

AC_CONFIG_FILES(Makefile \
		src/Makefile \
		data/Makefile)

AC_OUTPUT
