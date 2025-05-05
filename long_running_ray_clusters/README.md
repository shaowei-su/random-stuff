## Long Running Ray Cluster (LRRC)

### Context

BigQueue Ray cluster is already ephemeral: it starts up when you run a job and shuts down when the job is done. However, there are some use cases where you want to keep the cluster running for a long time, such as: fast prototypes, remote access to A100 GPUs etc..

### Initialize Remote Service Connection

Ray Head expose the port number 10001 for the remote Ray client gRPC access. So in this POC, we use kubectl port forwarding to achieve this.

```bash
kc port-forward -n bigqueue-service-jobs-production pod/rb95-4826-91b7-da4809c2acd0-raycluster-pc2qg-head-nz74g 10001:10001
```

In this case, you can find the actual head pod name by clicking on the RayJob k8s dashbaord view.

### Start Local Ray Client

```python
ray.init(address="ray://localhost:10001")
```

Note that: you'll need to launch the local Python interpreter using the same Python and preferably the same Ray version, otherwise Ray Client will complains and you may see Cloudpickle errors.

### Start Ray Workloads

Here we have two example notebooks:

- remote_ray_cluster.ipynb: establish client and run basic @ray.remote task to utilize remote GPUs.
- remote_torch.ipynb: establish client and run Ray Train workloads.

```

```
