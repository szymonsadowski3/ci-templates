# helm-package

This composite action packages a Helm chart. Afterwards, it creates an index file for the chart repository. If `index.yaml` exists, it is merged in the new index.

## Input Parameters

| Name         | Required | Default Value | Description                             |
| ------------ | :------: | :-----------: | --------------------------------------- |
| helm-version |    ❌    |   "v3.10.1"   | The Helm version                        |
| charts-dir   |    ❌    |      "."      | The directory containing the Helm chart |

## Usage

```yaml
steps:
  # ...

  - name: Helm package
    uses: bakdata/ci-templates/actions/helm-package@main
    with:
      helm-version: "v3.10.1" # (Optional)
      charts-dir: "helm-chart" # (Optional) if not set the repository root will be used


  # Rest of the workflow steps
```
