# hello-flask

Simple Flask HTTP service.

## Deploy into OpenShift

Run the following command:

    oc new-app https://github.com/leandroberetta/hello-flask.git

Expect the following output:

    --> Found image 292ed8d (5 months old) in image stream "dev/python" under tag "3-onbuild" for "python:3-onbuild"

    * A Docker build using source code from https://github.com/leandroberetta/hello-flask.git will be created
      * The resulting image will be pushed to image stream "hello-flask:latest"
      * Use 'start-build' to trigger a new build
    * This image will be deployed in deployment config "hello-flask"
    * Port 4000 will be load balanced by service "hello-flask"
      * Other containers can access this service through the hostname "hello-flask"
    * WARNING: Image "dev/python:3-onbuild" runs as the 'root' user which may not be permitted by your cluster administrator

    --> Creating resources ...
        imagestream "hello-flask" created
        buildconfig "hello-flask" created
        deploymentconfig "hello-flask" created
        service "hello-flask" created
    --> Success
        Build scheduled, use 'oc logs -f bc/hello-flask' to track its progress.
        Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
        'oc expose svc/hello-flask'
        Run 'oc status' to view your app.    

Next, create a route to expose the application:

    oc expose svc/hello-flask

Finally test it with curl:

    curl hello-flask-dev.192.168.64.109.nip.io

    Hello!