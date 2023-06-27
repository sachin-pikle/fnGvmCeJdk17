# fnGvmCeJdk17
Java function with GraalVM Community Edition for JDK 17 Native Image

Generated using Shaun Smith's [GraalVM Native Image-based function init-images](https://github.com/shaunsmith/graalvm-fn-init-images).

## Prerequisites

GraalVM Community Edition Native Image container images are stored in `https://github.com/graalvm/container/pkgs/container/graalvm-community`. 

Your function images are pushed to OCI Container Registry (OCIR).

## Deploy your function

1. From the same terminal window, login to OCI Container Registry (OCIR). Your function image will be pushed to your OCIR repo.

    ```shell
    docker login -u '<tenancy-namespace>/<your-OCI-user-name>' <region-key>.ocir.io
    ```
    When prompted for a password, enter your OCI auth token and hit enter.
    
2. Once you've logged in to OCIR, run `fn deploy`.

    ```shell
    fn -v deploy --app <app-name>
    ```
    This will use a multistage docker build as per the steps in the [Dockerfile](./Dockerfile) to generate an ahead-of-time compiled native executable for the function and deploy it to OCI.

3. (Optional) From the OCI console, go to the function application and enable function logs and traces. Go to the function and enable traces.

4. Invoke the function and check the time it takes to run. 

    ```shell
    fn invoke <app-name> fngvmcejdk17
    ```

5. (Optional) From the OCI console, check the function's logs and traces and see the time it took to run.