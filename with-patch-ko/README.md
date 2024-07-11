# Render without overriding api-versions

```shell
❯ helmfile template .
Building dependency release=foo, chart=/var/folders/kf/vwr6x12s6j1_6v0j44v300800000gn/T/chartify1679892145/foo
Templating release=foo, chart=/var/folders/kf/vwr6x12s6j1_6v0j44v300800000gn/T/chartify1679892145/foo
---
# Source: foo/templates/patched_resources.yaml
'apiVersion:': policy/v1beta1
kind: PodDisruptionBudget
metadata:
  labels:
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
❯ helmfile template . --args --api-versions="policy/v1/PodDisruptionBudget"
Building dependency release=foo, chart=/var/folders/kf/vwr6x12s6j1_6v0j44v300800000gn/T/chartify4171484006/foo
Templating release=foo, chart=/var/folders/kf/vwr6x12s6j1_6v0j44v300800000gn/T/chartify4171484006/foo
---
# Source: foo/templates/patched_resources.yaml
'apiVersion:': policy/v1beta1
kind: PodDisruptionBudget
metadata:
  labels:
    patch: ok
  name: foo
  namespace: bar
spec:
  maxUnavailable: 30%
  selector:
    matchLabels:
      app: foo
```
