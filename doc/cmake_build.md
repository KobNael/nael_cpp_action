
# Build with conan and cmake

Call `conan build . -pr:a ${{runner.os}}-latest --build missing` with the required build_type.

Inputs are :
 * BUILD_TYPE (required) : eg. *"Release"* | *"Debug"*
 * ARGS : additional settings or option, eg. *"-s compiler.cppstd=gnu20"*

Example:

```yaml
    # Release Build
    - name: Release conan build
      uses: KobNael/nael_cpp_action/cmake_build
      with:
        build_type: Release
        args: -s compiler.cppstd=gnu20 -o '&:coverage=ON' -o '&:cppcheck=ON' -o '&:valgrind=ON'
```

Back to [Main page](../README.md)
