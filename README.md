# Stratos-buildpack
Custom buildpack for Stratos for Cloud Foundry.

Stratos (https://github.com/cloudfoundry-incubator/stratos) consists of a JavaScript front-end and a Go back-end. In order to build the UI when pushing to Cloud Foundry, this custom buildpack is used to build both the front-end and the back-end.

### Buildpack User Documentation
Buildpacks customization documentation can be found at [custom buildpack docs](https://docs.cloudfoundry.org/buildpacks/custom.html).

### Building the Buildpack

To build this buildpack, run the following commands from the buildpack's directory:

1. Source the .envrc file in the buildpack directory.

   ```bash
   source .envrc
   ```
   To simplify the process in the future, install [direnv](https://direnv.net/) which will automatically source .envrc when you change directories.

1. Install buildpack-packager

    ```bash
    go install github.com/cloudfoundry/libbuildpack/packager/buildpack-packager@latest
    ```

1. Build the buildpack

    ```bash
    buildpack-packager build [ --cached=(true|false) ]
    ```

1. Use in Cloud Foundry

   Upload the buildpack to your Cloud Foundry and optionally specify it by name

    ```bash
    cf create-buildpack [BUILDPACK_NAME] [BUILDPACK_ZIP_FILE_PATH] 1
    cf push my_app [-b BUILDPACK_NAME]
    ```