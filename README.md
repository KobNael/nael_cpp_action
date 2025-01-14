# Github Action scripts for C++ projects

Simple github actions script for C++ project.

See :
 * [Install tools](doc/setup_cpp.md)
 * [Build with conan](doc/cmake_build.md)
 * [Run tests](doc/tests_cpp.md)

Exemple :

```yaml
# Workflow for C++ project
name: dev-pipeline
# Only for main and dev
on:
  push:
    branches: [ "dev", "main" ]
  pull_request:
    branches: [ "dev", "main" ]
    types: [opened, synchronize, reopened]
# List of actions
jobs:
  cpp_pipeline:
    runs-on: ubuntu-latest
    # Steps
    steps:
    # Checkout sources
    - name: checkout
      uses: actions/checkout@v4
      with:
         fetch-depth: 0
    # Get c++ tools
    - name: Get C++ Tools
      uses: KobNael/nael_cpp_action/setup_cpp
      with:
        # Set up cache id on recipe and CMakeLists
        key: ${{ hashFiles('./conanfile.py') }}-${{ hashFiles('./CMakeLists.txt') }}
    # Release Build
    - name: Release conan build
      uses: KobNael/nael_cpp_action/cmake_build
      with:
        build_type: Release
    # Release Tests
    - name: Release analysis
      uses: KobNael/nael_cpp_action/tests_cpp
      with:
        build_type: Release
    # Debug Build
    - name: Debug conan build
      uses: KobNael/nael_cpp_action/cmake_build
      with:
        build_type: Debug
    # Debug Tests
    - name: Debug analysis
      uses: KobNael/nael_cpp_action/tests_cpp
      with:
        build_type: Debug
```