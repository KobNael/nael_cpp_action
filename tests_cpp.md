# Launch tests

Call specific cmake targets :
 * `make run_unit_tests` (on Release and Debug)
 * `make run_coverage` (only on Debug)
 * `make run_memcheck` (only on Debug)

Inputs are :
 * build_type (required) : *"Release"* | *"Debug"*
 * root_dir : the working directory
 (default value being `${{github.workspace}}/builds/Linux/gcc/13/x86_64/`)

The working directory for these calls will be `${{inputs.root_dir}}/${{inputs.build_type}}/`.

Example:

```yaml
    # Test
    - name: Debug analysis
      uses: KobNael/nael_cpp_action/tests_cpp
      with:
        build_type: Debug
```

Back to [Main page](README.md)
