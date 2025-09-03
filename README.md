# Taskopenai
# Встановіть та налаштуйте kubectl-ai плагін для створення ШІ Recommended YAML manifests
## Task steps
1. Create an [API key](https://platform.openai.com/account/api-keys)  
`key name: name: kubectl-ai`

2. Install and configure [the kubectl-ai plugin](https://github.com/sozercan/kubectl-ai)
```sh
$ curl -sSL https://raw.githubusercontent.com/GoogleCloudPlatform/kubectl-ai/main/install.sh | bash

$ kubectl plugin list
export OPENAI_API_KEY="***************************"
export OPENAI_DEPLOYMENT_NAME="gpt-4.1"
kubectl-ai --llm-provider=openai --model=gpt-4.1
export REQUIRE_CONFIRMATION=false
```

3. Practice writing and testing prompts on a local cluster
```yaml
$ mkdir yaml
kubectl ai "create an nginx deployment with 3 replicas" > yaml/app.yaml
```
4. The resulting manifest in the yaml directory in the root of the repository.

| NAME                        | PROMPT                             | DESCRIPTION                                                              | EXAMPLE                                     |
|-----------------------------|------------------------------------|--------------------------------------------------------------------------|---------------------------------------------|
| app.yaml                    | Create Application Config          | YAML to define the basic schema of a Kubernetes application              | [app.yaml](yaml/app.yaml)                 |
| app-livenessProbe.yaml      | Add Liveness Probe                 | YAML to define a liveness probe for your application                    | [app-livenessProbe.yaml](yaml/app-livenessProbe.yaml) |
| app-readinessProbe.yaml     | Add Readiness Probe                | YAML to define a readiness probe for your application                   | [app-readinessProbe.yaml](yaml/app-readinessProbe.yaml) |
| app-volumeMounts.yaml       | Configure Volume Mounts            | YAML to define and configure storage volumes for your application       | [app-volumeMounts.yaml](yaml/app-volumeMounts.yaml) |
| app-cronjob.yaml            | Create Cron Job                    | YAML to define a cron job within your application                       | [app-cronjob.yaml](yaml/app-cronjob.yaml) |
| app-job.yaml                | Create a Job                       | YAML to define a job within your application                            | [app-job.yaml](yaml/app-job.yaml) |
| app-multicontainer.yaml     | Set Up Multi-container Pods        | YAML to define a pod that runs more than one container                  | [app-multicontainer.yaml](yaml/app-multicontainer.yaml) |
| app-resources.yaml          | Configure Resource Usage           | YAML to configure resource requests and limits for your application     | [app-resources.yaml](yaml/app-resources.yaml) |
| app-secret-env.yaml         | Set Up Secrets as Env Variables    | YAML to define environment variables using secrets                      | [app-secret-env.yaml](yaml/app-secret-env.yaml) |
