# Render without overriding api-versions

```shell
❯ helmfile template .
Building dependency release=foo, chart=.
Templating release=foo, chart=.
---
# Source: foo/templates/foo.yaml
apiVersion:: policy/v1beta1
kind: PodDisruptionBudget
metadata:
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
Building dependency release=foo, chart=.
Templating release=foo, chart=.
---
# Source: foo/templates/foo.yaml
apiVersion:: policy/v1
kind: PodDisruptionBudget
metadata:
  name: foo
  namespace: bar
spec:
  maxUnavailable: 30%
  selector:
    matchLabels:
      app: foo
```
