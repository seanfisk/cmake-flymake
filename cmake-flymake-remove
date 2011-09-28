#!/bin/bash
#
# removeMakefiles.sh by Nil Geisweiller
#
# That script remove recursively all Makefile.flymake
# (or rather Makefile for now) from the CMake project.
 
#MAKEFILE_NAME="Makefile.flymake"
MAKEFILE_NAME="Makefile"
 
# For each CMakeLists.txt found from the current directory and descendants
# it removes the associated Makefile.flymake (or rather Makefile for now).
while read -r -d $'\0' FILEPATH
do
    RELATIVE_MAKEFILE_DIR=${FILEPATH%/*}
    rm "${RELATIVE_MAKEFILE_DIR}/${MAKEFILE_NAME}"
done < <( find . -name "CMakeLists.txt" -print0 )