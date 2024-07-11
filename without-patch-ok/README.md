# Render without overriding api-versions

```shell
❯ helmfile template .
Building dependency release=foo, chart=../chart
Templating release=foo, chart=../chart
---
# Source: foo/templates/foo.yaml
apiVersion: policy/v1
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
❯ helmfile template . --args --api-versions="v1/myApi"
Building dependency release=foo, chart=../chart
Templating release=foo, chart=../chart
---
# Source: foo/templates/foo.yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: foo
  namespace: bar
  annotations:
    capability: ok
spec:
  maxUnavailable: 30%
  selector:
    matchLabels:
      app: foo
```
