## Process this file with autoconf to produce a configure script.
m4_include([m4/gsl.m4])
m4_include([m4/m4_ax_lib_gdal.m4])


# The version set here will propagate to other files from here
AC_INIT([gedisimulator], 0.0.1)

# Checks for common programs using default macros
AC_PROG_CC


##################
## GSL
##################
AX_PATH_GSL(0.1,,
	    AC_MSG_ERROR(could not find GSL:
			 Debian: sudo apt install libgsl-dev
			 RPM-based: sudo yum install gsl-devel
			 MacOS: brew install gsl))


##################
## GDAL
##################
AX_LIB_GDAL2()


##################
## HDF5
##################
AX_LIB_HDF5()


##################
## GEOTIFF
##################

GEOTIFF_INCLUDE=

dnl Now seach for headers
if test -r /usr/include/geotiff.h ; then
	GEOTIFF_INCLUDE=
dnl Debian
elif test -r /usr/include/geotiff/geotiff.h ; then
	GEOTIFF_INCLUDE="-I/usr/include/geotiff"
dnl Fedore and OpenSuse
elif test -r /usr/include/libgeotiff/geotiff.h ; then
	GEOTIFF_INCLUDE="-I/usr/include/libgeotiff"
else
	AC_CHECK_HEADERS([geotiff.h])
	if test "$ac_cv_header_geotiff_h" = "no" ; then
		AC_MSG_ERROR([cannot find geotiff.h])
	fi
fi


AC_SUBST(GEOTIFF_INCLUDE,$GEOTIFF_INCLUDE)

##################
## END
##################


AC_OUTPUT(src/Makevars)
