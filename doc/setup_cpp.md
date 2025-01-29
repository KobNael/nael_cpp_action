# Download and install C++ Tools

Install usefull tools according to the runner system :
 * gcc, gcovr, lcov, libncurses5-dev and valgrind : using apt. for linux
 * conan (2.11) using [get-conan](https://github.com/turtlebrowser/get-conan) for both linux and windows
 * apply the conan configuration provided by the repository (see profiles directory).

Also :
 * cache the local conan repository with a key

Example:

```yaml
    # Get c++ tools
    - name: Get C++ Tools
      uses: KobNael/nael_cpp_action/setup_cpp
      with:
        KEY: nux-${{ hashFiles('./conanfile.py') }}-${{ hashFiles('./CMakeLists.txt') }}
```
Back to [Main page](../README.md)
