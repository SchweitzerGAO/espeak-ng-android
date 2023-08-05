# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.22.1)
#add_subdirectory (espeak-ng)

# Declares and names the project.

project("espeak_ng")

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.

add_library( # Sets the name of the library.
        espeak_ng

        # Sets the library as a shared library.
        SHARED

        # Provides a relative path to your source file(s).
        espeak-ng/src/libespeak-ng/common.c
        espeak-ng/src/libespeak-ng/mnemonics.c
        espeak-ng/src/libespeak-ng/error.c
        espeak-ng/src/libespeak-ng/ieee80.c
        espeak-ng/src/libespeak-ng/compiledata.c
        espeak-ng/src/libespeak-ng/compiledict.c
        espeak-ng/src/libespeak-ng/dictionary.c
        espeak-ng/src/libespeak-ng/encoding.c
        espeak-ng/src/libespeak-ng/intonation.c
        espeak-ng/src/libespeak-ng/langopts.c
        espeak-ng/src/libespeak-ng/numbers.c
        espeak-ng/src/libespeak-ng/phoneme.c
        espeak-ng/src/libespeak-ng/phonemelist.c
        espeak-ng/src/libespeak-ng/readclause.c
        espeak-ng/src/libespeak-ng/setlengths.c
        espeak-ng/src/libespeak-ng/soundicon.c
        espeak-ng/src/libespeak-ng/spect.c
        espeak-ng/src/libespeak-ng/ssml.c
        espeak-ng/src/libespeak-ng/synthdata.c
        espeak-ng/src/libespeak-ng/synthesize.c
        espeak-ng/src/libespeak-ng/tr_languages.c
        espeak-ng/src/libespeak-ng/translate.c
        espeak-ng/src/libespeak-ng/translateword.c
        espeak-ng/src/libespeak-ng/voices.c
        espeak-ng/src/libespeak-ng/wavegen.c
        espeak-ng/src/libespeak-ng/speech.c
        espeak-ng/src/libespeak-ng/espeak_api.c
        espeak-ng/src/ucd-tools/src/case.c
        espeak-ng/src/ucd-tools/src/categories.c
        espeak-ng/src/ucd-tools/src/proplist.c
        espeak-ng/src/ucd-tools/src/tostring.c
        espeak-ng/src/ucd-tools/src/scripts.c
        espeak-ng/src/ucd-tools/src/ctype.c)

# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++17")

find_library( # Sets the name of the path variable.
        log-lib

        # Specifies the name of the NDK library that
        # you want CMake to locate.
        log)

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
        espeak_ng

        # Links the target library to the log library
        # included in the NDK.
        ${log-lib})