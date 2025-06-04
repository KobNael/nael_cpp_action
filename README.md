# Github Action scripts for C++ projects

Full github actions reusable pipeline for C++ project.
For details see the [Complete Pipeline](doc/cpp-workflow.md)

One can also directly use only some part, dee :
 * [Install tools](doc/setup_cpp.md)
 * [Build with conan](doc/cmake_build.md)
 * [Run tests](doc/tests_cpp.md)
 * [Install and uplad](doc/install.md)

Exemple :

```yaml
# Workflow for C++ project
name: dev-pipeline

# Only for dev
on:
  push:
    branches: [ "dev", "main" ]
  pull_request:
    branches: [ "dev", "main" ]
    types: [opened, synchronize, reopened]

# List of actions
jobs:
  # Call pipeline
  cpp_pipeline:
    uses: KobNael/nael_cpp_action/.github/workflows/cpp-workflow.yml@v1
    with:
      WITH_COVERAGE: false
      RUN_SONAR: false
      CHECK_QUALITY_GATE: false
      UPLOAD_ARTIFACT: true
    secrets:
      GH_PAT: "${{ secrets.GH_PAT }}"
      SONAR_TOKEN: "${{ secrets.SONAR_TOKEN }}"
      SONAR_HOST_URL: "${{ secrets.SONAR_HOST_URL }}"

```