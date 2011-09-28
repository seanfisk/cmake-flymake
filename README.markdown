Flymake for the CMake build system
==================================

These are scripts for using the [CMake build system](http://www.cmake.org/) with [Flymake](http://flymake.sourceforge.net/), an on-the-fly syntax checker for GNU Emacs. I've found these [scripts](http://wiki.opencog.org/w/Flymake_help) written by Nil Geisweiller on the OpenCog Wiki, but they didn't work immediately for me. I'm hoping that the modified versions now work rather reliably out of the box. I was linked to them by [Flymake with CMake on the EmacsWiki](http://www.emacswiki.org/emacs/FlyMake#toc6).

Dependencies
------------

These scripts require a few obvious dependencies.

* [Emacs 23](http://www.gnu.org/software/emacs/), which includes Flymake (this is not necessary to run the script, but to use the results)
* [GNU bash](http://www.gnu.org/software/bash/)
* [CMake](http://www.cmake.org/)

Installation
------------

	cd your_projects_dir
	git clone git://github.com/seanfisk/cmake-flymake.git
	cd cmake-flymake
	ln -s "$PWD"/cmake-flymake-{generate,remove} ~/bin # or wherever you put your scripts

Use
---

1. Follow these project setup instructions:

		cd your_cmake_project
		mkdir bin # your build directory
		cd bin
		cmake .. # create the CMake configs
		cd ..
		cmake-flymake-generate bin # or whatever you named the build directory
	
2. Open your file in Emacs.
3. `M-x flymake-mode`
4. Enjoy the incremental compilation!

Other Notes
-----------

* When you change any of your `CMakeLists.txt` files, re-run `cmake ..` and `cmake-flymake-generate bin`.
* To remove the Flymake Makefiles, run `cmake-flymake-remove`.
* These scripts are configured to use the GNU make variables ${CXX}, ${CXX\_FLAGS}, and ${CXX\_DEFINES} in the actual Makefiles. This means that the scripts will require editing to work with pure C projects (when using CC, CFLAGS, etc.) or any other language besides C++. This should be quite easy to figure out. Look at the actual Makefiles which get generated for more information.
* I haven't tested this on Windows, but I doubt it will work (it is bash, after all). UNIX-like operating systems (including GNU/Linux, Mac OS X) should be fine.
