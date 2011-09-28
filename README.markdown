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

* When you change any of your `CMakeLists.txt` files, re-run `cmake ..` and `cmake-flymake-generate bin`.
* To remove the Flymake Makefiles, run `cmake-flymake-remove`.
