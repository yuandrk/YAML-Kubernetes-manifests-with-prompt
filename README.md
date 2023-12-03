Table's YAML Kubernetes manifests with prompt
-----

| NAME | PROMPT | DESCRIPTION | EXAMPLE |
|------|--------|-------------|---------|
|Redis|"Create deployment Redis with pod.Include an environment variable named CONFIGMAP_PARAM sourced from a key in a ConfigMap named app-config. Also, mount a volume from the same ConfigMap at /config inside the container"|This prompt requests the creation of a Kubernetes deployment for a Redis application, featuring a single pod. It specifies the inclusion of an environment variable named CONFIGMAP_PARAM, which should be sourced from a key in a ConfigMap named app-config. Additionally, it asks for a volume to be mounted from the same ConfigMap at the /config path inside the container. This setup is designed to configure the Redis pod with specific parameters and data from the ConfigMap, allowing for a tailored deployment.| [app.yaml](app.yaml) |
|Mysql dump |"Create CronJob, should run every  week. It must execute a single container named MySQL The container should run the command echo "mysqldump -u root -p --datebase data"|This prompt requests the creation of a Kubernetes CronJob that is scheduled to run weekly. The job involves executing a single container named "MySQL". Within this container, the specified command to run is echo "mysqldump -u root -p --database data". This command essentially prints the command line for a MySQL database dump, typically used for backing up the database. The focus of the CronJob is to schedule this print command (which represents a database dump operation) on a weekly basis| [app-cronjob.yaml](app-cronjob.yaml)
|Synchronizes with GCS bucket | "Create a Kubernetes Job named app-job-sync. It should run a container using the latest Google Cloud SDK Alpine image to perform a data synchronization from a specified Google Cloud Storage bucket to a volume. The volume should be backed by a Google Compute Engine persistent disk"|The prompt requests the creation of a Kubernetes Job named app-job-sync. It specifies using a container with the latest Google Cloud SDK Alpine image to synchronize data from a Google Cloud Storage bucket to a volume backed by a Google Compute Engine persistent disk. Additionally, the Job is configured not to retry on failure. This setup is intended for a one-time data sync operation within a Kubernetes environment.|[app-job.yaml](app-job.yaml)|
|app-livenessprobe|"Create a Kubernetes Pod named app-livenessprobe in the demo namespace. The Pod should have a container using the image gcr.io/k8s-k3s/demo:v1.0.0 with a liveness probe configured for HTTP GET requests to the root path (/) on port 8000. Set the initial delay for the probe to 5 seconds, a timeout of 1 second, a check period of 10 seconds, and a failure threshold of 3. The container should also expose port 8080."|This prompt instructs the creation of a Kubernetes Pod with specific liveness probe settings. The probe checks the container's health by making HTTP GET requests to the root path. The container exposes port 8080 and uses a specified image.|[app-livenessProbe.yaml](app-livenessProbe.yaml)|
|app-multi-containers|"Create a Kubernetes Pod named app-multi-containers. The Pod should contain two containers named 1st and 2nd. The 1st container should use the nginx image and mount a volume at /usr/share/nginx/html. The 2nd container, using the debian image, should mount the same volume at /html. This container should continuously update an index.html file in this volume with the current date every second."|This prompt is for a Kubernetes Pod with two containers sharing a volume. The first container runs nginx and serves content from a shared volume. The second container, running Debian, continuously updates an HTML file in the shared volume with the current date, demonstrating a simple dynamic content generation.| [app-multicontainer.yaml](app-multic
ontainer.yaml)|
|app-readinessprobe|"Create a Kubernetes Pod named app-readinessprob with a single container named app using the image gcr.io/k8s-k3s/demo:v2.0.0. Configure a liveness probe to make HTTP GET requests to the root path (/) on port 8000 with a 5-second initial delay, 1-second timeout, 10-second period, and a failure threshold of 3. Additionally, set up a readiness probe to check the /ready endpoint on port 8000 every 2 seconds, starting immediately, with a failure threshold of 3 and a success threshold of 1. The container should expose port 8000."|This prompt describes the creation of a Kubernetes Pod featuring a single container configured with both liveness and readiness probes. The liveness probe checks the root path for container health, while the readiness probe targets a specific /ready endpoint to determine if the container is ready to handle traffic. The container runs a specific image and exposes port 8000.|[app-readinessprobe.yaml](app-readinessprobe.yaml)|
|app-resource|"Create a Kubernetes Pod named app-resource with a single container named app. Use the image gcr.io/kuar-demo/kuard-amd64:1. Set up liveness and readiness probes; the liveness probe should check the /healthy path on port 8080 and the readiness probe the /ready path on the same port. Define resource requests of 100m CPU and 128Mi memory, with limits of 100m CPU and 256Mi memory. The container should expose port 8080."|This prompt is for a Kubernetes Pod with a specific focus on resource management and health checking. It involves setting up a container with defined CPU and memory requests and limits, ensuring efficient resource utilization. The container also includes liveness and readiness probes for health checking, targeting specific paths to ensure the application's proper functioning and readiness to handle traffic.|[app-resource.yaml](app-resource.yaml)|
|app-secret-env|"Create a Kubernetes Pod named app-secret-env with a single container named mycontainer using the Redis image. The container should have two environment variables, SECRET_USERNAME and SECRET_PASSWORD, sourced from a Kubernetes secret named mysecret1 with keys username and password respectively. Set the restart policy of the Pod to never."|This prompt describes setting up a Kubernetes Pod with a Redis container that utilizes Kubernetes secrets for sensitive data. The container is configured to pull specific data (username and password) from a secret named mysecret1, ensuring secure handling of confidential information.|[app-secret-env.yaml](app-secret-env.yaml)|
|app-secret|"Create a Kubernetes Pod named app-secret with a single container named mypod using the Redis image. Mount a volume named foo at /etc/foo in read-only mode. This volume should be backed by a secret named simple-secret."|This prompt instructs the creation of a Kubernetes Pod with a Redis container, where a specific secret is mounted as a volume. The secret, simple-secret, is used to provide sensitive data to the container, mounted at a specific path and configured as read-only for security.||