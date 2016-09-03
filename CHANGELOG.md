Only significant changes to FindICU.cmake figure here:

* 2016-09-03: move genrb/pkgdata checks to icu_generate_resource_bundle function to avoid unnecessary failure
   on systems where ICU are splitted in several packages (headers/libraries/tools) when you only want to find
   ICU libraries (#4 - @tepperly)
* 2016-05-31:
  + add support to build resource bundles
  + no longer initialize ICU_FOUND to TRUE
  + dependencies fixed through pkg-config now emits a warning to ensure portability and consistency
  + follow at best cmake-developer(7) guidelines (see commit message for a complete list of changes)
    * add support for imported target (ICU::ICU) (CMake >= 3)
    * deprecates ICU_ROOT for ICU_ROOT_DIR
    * deprecates ICU_(MAJOR|MINOR|PATCH)_VERSION for ICU_VERSION_$1
  + various cleanup (see commit message for details)
* 2015-06-05: ICU_FOUND variable stay valued to TRUE if include dirs are not found (#2 - @nixprime)
* 2013-09-01: icu-config was never found (find_program arguments inverted)
* 2013-06-11: revert previous translation of new ICU versions (ICU >= 49) into old format, keep it as is
* 2012-12-10: support for ICU_*_FLAGS (empty if icu-config is not found)
* 2012-09-22: version header not found was not fatal
* 2012-07-29:
  + distinguish release and debug ICU builds (win32)
  + io component library was named ustdio in version 2.4
* 2012-06-25:
  + ~~consider amd64 architectures (bin64 and lib64 as PATH_SUFFIXES) (not tested)~~ (removed by 2016-05-31)
  + detection improved for versions older than 4
  + i18n component mapped to the wrong library (on uc - due to cache ?)
* 2012-05-31: ~~workaround to handle new release numbering since 4.9.1 (still version 4)~~ (reverted by 2013-06-11)
* 2012-04-28: support for ICU_ROOT: allow user to set the root installation of ICU
* 2011-11-04: fix mix of ICU_INCLUDE_DIR and ICU_INCLUDE_DIRS to (only) ICU_INCLUDE_DIRS
* 2011-06-24: add i18n library name on windows (msvc)
