# Download and install C++ Tools

Install usefull tools :
 * gcc, gcovr, lcov, libncurses5-dev and valgrind : using apt.
 * conan (2.11) using [get-conan](https://github.com/turtlebrowser/get-conan)

Also :
 * cache the local conan repository with a key

Example:

```yaml
    # Get c++ tools
    - name: Get C++ Tools
      uses: KobNael/nael_cpp_action/setup_cpp
      with:
        key: ${{ hashFiles('./conanfile.py') }}-${{ hashFiles('./CMakeLists.txt') }}
```
Back to [Main page](README.md)
