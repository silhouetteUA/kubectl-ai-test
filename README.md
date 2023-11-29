# kubectl-ai-test
compose k8s manifests using kubectl-ai plugin and OpenAI


| NAME      | PROMPT              | DESCRIPTION                               | EXAMPLE                        |
|-----------|---------------------|-------------------------------------------|--------------------------------|
| pod  |create pod with name=app, labels app=demo and image gcr.io/devops-course-prometheus/kbot and container port 8080| create a pod|[link](yaml/app.yaml)                                |
| liveness  |create a pod with app-livenessprob as name, demo as namespace, container name app, container image=gcr.io/k8s-k3s/demo:v1.0.0, liveness probe path=/ and port=8000| pod with liveness probe       |[link](yaml/app-livenessProbe.yaml)                                |
| readiness |add readinessProbe with path /ready port 8000, periodSeconds=2, initialDelaySeconds=2,successThreshold=1, failureThreshold=3| readiness probe added to previous result    |[link](yaml/app-readinessProbe.yaml)                                |
|volumeMounts|add volumeMounts with name=data and mountPath as /data, create a volumes reference with name=data and hostPath=/var/lib/app|pod with a volume mounts|[link](yaml/app-volumeMounts.yaml)|
|cronJob|create a cronjob with schedule=*/5 * * * * with container name=hello image=bash and command=echo Hello world, set restartPolicy = OnFailure|example of a cronJob|[link](yaml/app-cronjob.yaml)|
|Job|create a Job with name=app-job-rsync with init container name=init image google/cloud-sdk:275.0.0-alpine and command /bin/sh -c gsutil -m rsync -dr gs://glow-sportradar/ /data/input|example of Job|[link](yaml/app-job.yaml)|
|multicontainer|create pod with two conatiners, first container name is 1st and image is nginx while second container name is 2nd with image=busybox which executes command sleep 3600|pod with two containers|[link](yaml/app-multicontainer.yaml)|
|resources|create a pod with name mypod using image=nginx and set request cpu=100m, memory=128Mi while set limits to cpu=100m and memory 256Mi| resources example: allocate and limit|[link](yaml/app-resources.yaml)|
|secret|create pod with name=my-secret with container name=mypod and image=redis, also inject readOnly secret with name=simple-secret located on volume name=foo mountPath=/etc/foo| secret injection|[link](yaml/app-secret-env.yaml)|

