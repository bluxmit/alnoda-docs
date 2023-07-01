# Kubernetes 

You can install Alnoda workspaces in your Kubernetes cluster using the helm chart. 

Add Helm repository:

```
helm repo add alnoda https://bluxmit.github.io/alnoda-charts/
```

Update your Helm chart list:

```
helm repo update
```

Create Helm values file, for example file `values.yaml`:

```yaml

ingress:
  enabled: true
  className: nginx
  host: example.com
```

Install the workspace:

```
helm install my-workspace alnoda/alnoda-workspace -f values.yaml
```

!!! note 
    You can find out information about the chart defaults and values in the [__alnoda-charts repository__](https://github.com/bluxmit/alnoda-charts) 