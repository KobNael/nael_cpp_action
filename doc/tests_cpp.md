# Launch tests

Call specific cmake targets :
 * `make run_unit_tests` (on Release and Debug)
 * `make run_coverage` (only on Debug)
 * `make run_memcheck` (only on Debug)

Inputs are :
 * BUILD_TYPE (required) : *"Release"* | *"Debug"*
 * ROOT_DIR : the working directory
 (default value being `${{github.workspace}}/builds/Linux/gcc/13/x86_64/`)
 * WITH_COVERAGE : Should the coverage target run (default value True)

The working directory for these calls will be `${{inputs.ROOT_DIR}}${{inputs.BUILD_TYPE}}/`.

Example:

```yaml
    # Test
    - name: Debug analysis
      uses: KobNael/nael_cpp_action/tests_cpp@v1
      with:
        BUILD_TYPE: Debug
        WITH_COVERAGE: false
        ROOT_DIR: ${{github.workspace}}\builds\Windows\gcc\12\x86_64\
```

Back to [Main page](../README.md)
