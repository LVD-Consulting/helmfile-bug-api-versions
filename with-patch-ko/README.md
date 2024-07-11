# Render without overriding api-versions

```shell
❯ helmfile template .
Building dependency release=foo, chart=/var/folders/kf/vwr6x12s6j1_6v0j44v300800000gn/T/chartify2255888247/foo
Templating release=foo, chart=/var/folders/kf/vwr6x12s6j1_6v0j44v300800000gn/T/chartify2255888247/foo
---
# Source: foo/templates/patched_resources.yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  annotations:
    patch: ok
  name: foo
  namespace: bar
spec:
  maxUnavailable: 30%
  selector:
    matchLabels:
      app: foo
```

# Render with overriding api-versions

```shell
❯ helmfile template . --args --api-versions="v1/myApi"
Building dependency release=foo, chart=/var/folders/kf/vwr6x12s6j1_6v0j44v300800000gn/T/chartify3019248657/foo
Templating release=foo, chart=/var/folders/kf/vwr6x12s6j1_6v0j44v300800000gn/T/chartify3019248657/foo
---
# Source: foo/templates/patched_resources.yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  annotations:
    patch: ok
  name: foo
  namespace: bar
spec:
  maxUnavailable: 30%
  selector:
    matchLabels:
      app: foo
```
