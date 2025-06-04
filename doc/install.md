# Install and upload

Call install target, then upload an artifact of the install directory using [upload-artifact](https://github.com/actions/upload-artifact).

Inputs are :
 * BUILD_DIR : the build directory
 (default value being `${{github.workspace}}/builds/Linux/gcc/13/x86_64/Release/`)

The resuting artifact will be named `${{runner.os}}-binaries`.

Example:

```yaml
    - name: Install & upload
      uses: KobNael/nael_cpp_action/install@upload
      with:
        BUILD_DIR: ${{github.workspace}}\builds\Windows\gcc\12\x86_64\Release\
```

Back to [Main page](../README.md)
