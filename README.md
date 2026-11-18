# HW4 Model Deployment and Scaling

Deployed the TrustBank fraud service with three replicas, health probes, resource limits, and autoscaling at 40% CPU up to eight pods.

Start Kubernetes and check status:

```bash
bash scripts/local_up.sh
kubectl get pods,svc,hpa
```

Run the v1-to-v2 rolling-update demo from the initial v1 deployment:

```bash
bash scripts/rolling_update_demo_incluster.sh ghcr.io/rfsalas/trustbank-fraud:v2
```

The in-cluster demo sent requests throughout the rollout and recorded zero dropped requests. The screenshot below provides the rolling-update evidence.

[View rolling-update results](screenshots/04-v1-to-v2-rollout-zero-dropped-requests.png)

Also demonstrated pod self-healing, blue-green cutover and rollback, and a public Azure /predict response with HTTP 200. Azure resources were deleted afterward, with teardown confirmation captured.

Screenshots are in screenshots/, Kubernetes manifests are in k8s/, and short answers are in ANSWERS.md.