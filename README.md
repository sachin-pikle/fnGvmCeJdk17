# fnGvmCeJdk17
Java function with Oracle GraalVM 22.3.2 Native Image JDK 17

Generated using Shaun Smith's [GraalVM Native Image-based function init-images](https://github.com/shaunsmith/graalvm-fn-init-images).

## Prerequisites

Oracle GraalVM container images are stored in `https://container-registry.oracle.com`. You will need an Oracle account (doesn't require a credit card!) to accept the Oracle GraalVM license on `container-registry.oracle.com >> GraalVM >> native-image-ee`.

1. Go to https://container-registry.oracle.com.

2. Go to `GraalVM >> native-image-ee`.

3. Click `Sign in`.

4. You will see the Oracle Login screen. If you have an account, enter your user and password to login. If you don't have an account scroll down to the `Create a new Account` section and create you free account (no credit card required).

5. Once you've signed in, view and accept the license.

## Deploy your function

1. From a terminal like OCI Cloud Shell (or on local), login to Oracle Container Registry (OCR). Oracle GraalVM container images are pulled from OCR.

    ```shell
    docker login container-registry.oracle.com -u <YOUR_ORACLE_ACCOUNT_USER_NAME>
    ```
    When prompted, enter your password and hit enter.

2. From the same terminal window, login to OCI Container Registry (OCIR). Your function image will be pushed to your OCIR repo.

    ```shell
    docker login -u '<tenancy-namespace>/<your-OCI-user-name>' <region-key>.ocir.io
    ```
    When prompted for a password, enter your OCI auth token and hit enter.
    
3. Once you've logged in to both OCR and OCIR, run `fn deploy`.

    ```shell
    fn -v deploy --app <app-name>
    ```
    This will use a multistage docker build as per the steps in the [Dockerfile](./Dockerfile) to generate an ahead-of-time compiled native executable for the function and deploy it to OCI.

4. (Optional) From the OCI console, go to the function application and enable function logs and traces. Go to the function and enable traces.

5. Invoke the function and check the time it takes to run. 

    ```shell
    fn invoke <app-name> fngvm2232jdk17
    ```

6. (Optional) From the OCI console, check the function's logs and traces and see the time it took to run.