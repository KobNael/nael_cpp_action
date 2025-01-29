# Install and upload

Call install target, then upload an artifact using [upload-artifact](https://github.com/actions/upload-artifact).

Inputs are :
 * BUILD_DIR : the build directory
 (default value being `${{github.workspace}}/builds/Linux/gcc/13/x86_64/Release/`)
 * PATH : A file, directory or wildcard pattern that describes what to upload.

The resuting artifact will be named `${{runner.os}}-binaries`.

Example:

```yaml
    - name: Install & upload
      uses: KobNael/nael_cpp_action/install@v1
      with:
        BUILD_DIR: ${{github.workspace}}\builds\Windows\gcc\12\x86_64\Release\
        PATH: "bin/ps_scheduling*"
```

Back to [Main page](../README.md)
