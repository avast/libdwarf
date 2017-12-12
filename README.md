## Libdwarf

Libdwarf meta repository that combines [libdwarf](https://www.prevanders.net/dwarf.html) with its dependency [libelf](https://github.com/WolfgangSt/libelf).

## Use

Target named `libdwarf` is exposed. It can be used as follows:
```cmake
target_link_libraries(project-that-needs-libdwarf libdwarf)
```

Because of the LGPL license used in both `libdwarf` and `libelf` projects, the libraries are build as shared (on Linux) or dynamically linked (on Windows).

## Status

The repository is meant to be used by the `retdec` project. Versions of both `libdwarf` and `libelf` used here are pretty old. Both are also used pre-configured. In the future we could do some of the following:
* Update both libraries.
* Run proper configuration from CMake.
* Use official repositories instead of this meta repository.
* Do not use `libdwarf` and `libelf` at all. Use LLVM to parse DWARF debugging information.

## Requirements

* A compiler supporting C++14
 * On Windows, only Microsoft Visual C++ is supported (version >= Visual Studio 2015).
* CMake (version >= 3.6)

## License

* `libdwarf` is licensed under the GNU Lesser General Public license. See files `libdwarf/libdwarf/COPYING`, `libdwarf/libdwarf/LGPL.txt`, and `libdwarf/libdwarf/LIBDWARFCOPYRIGHT` for more details.
* `libelf` is licensed under the GNU Library General Public license. See the `libelf/COPYING.LIB` file for more details.
