
# Full pipeline

Full C++ pipeline.   
Runs on on ubuntu-latest and windows-latest.

Inputs are :
 * WITH_COVERAGE : should we launch the coverage target (default false)
 * RUN_SONAR : should we run the sonar analysis (default true)
 * CHECK_QUALITY_GATE : should we test the quality gate (if RUN_SONAR==true) (default true)
 * UPLOAD_ARTIFACT: should we install the project and then upload an artifact (default false)

Secrets are :
 * SONAR_TOKEN (required): authentification token for sonar server
 * SONAR_HOST_URL (required): sonar server url
 * GH_PAT (required): authentification for github

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
    uses: KobNael/nael_cpp_action/.github/workflows/cpp-workflow.yml@upload
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

Back to [Main page](../README.md)
