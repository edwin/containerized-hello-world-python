# A Dockerized Python Flask app on top of Openshift 4

Create a very simple hello world Python app with Flask framework, containerized it, and deploy it into Openshift 4.

## Build and Push to Docker Hub from Openshift 4
```
$ oc new-build --strategy docker --binary --name=containerized-hello-world-python 

$ oc start-build containerized-hello-world-python  --from-dir=. --follow --wait
```

## Deploy to OpenShift 4
```
$ oc new-app containerized-hello-world-python  --name=containerized-hello-world-python 
```

## Expose a Secure URL for this Flask app
```
$ oc create route edge --service=containerized-hello-world-python 
```