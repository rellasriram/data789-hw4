# HW4 — Short Answers

Answer each question in 2–3 sentences.

## 1. Rolling-update safety
Why does the Deployment use `maxUnavailable: 0`, and what would change if it were `maxUnavailable: 1`?

> Using maxUnavailable: 0 and maxSurge: 1 will cause the deployment to create one new pod at a time, and once it becomes available, delete an old pod. This will guarantee that there are always at least 3 replicas running during the deployment. Using maxUnavailable: 1 means that we may only have 2 replicas running at a point in the deployment meaning less service is being provided. The number of requests lost during the v1 to v2 deployment was 0.

## 2. Health probes
Why do the liveness/readiness probes target `/health` instead of `/predict`?

> GET /health is a lightweight endpoint. It is used by readiness probes to determine if traffic should be sent to the pod, and in liveness probes to determine if the container should be restarted. Using /predict for probes will require payloads to be sent for inference which may cause issues with redis to be seen as an issue with the API container.

## 3. Autoscaling under load
Your HPA scales at 40% CPU up to 8 pods. If request volume doubled, what would you expect to happen — and what happens once it reaches the maximum?

> When the CPU usage of pods rises above 40% of requested capacity due to increased requests, the HPA will increase the number of pods. However, twice as much traffic may not result in twice as many pods. Once we have 8 pods in our deployment, the HPA cannot scale further. If it continues to be under sustained high demand, increased latency may occur, and requests may also fail.


## 4. AI Assistance

> I ran the deployment commands and captured the evidence in my own environments.