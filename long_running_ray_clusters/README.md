## Long Running Ray Cluster (LRRC)

### Context

BigQueue Ray cluster is already ephemeral: it starts up when you run a job and shuts down when the job is done. However, there are some use cases where you want to keep the cluster running for a long time, such as: fast prototypes, remote access to A100 GPUs etc..

### Initialize Remote Service Connection

````python
Ray Head expose the port number 10001 for the remote Ray client gRPC access. So in this POC, we use kubectl port forwarding to achieve this.

```bash
kc port-forward -n bigqueue-service-jobs-production pod/rb95-4826-91b7-da4809c2acd0-raycluster-pc2qg-head-nz74g 10001:10001
```

In this case, you can find the actual head pod name by clicking on the RayJob k8s dashbaord view.

### Start Local Ray Client
```python

````
