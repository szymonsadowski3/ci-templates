# helm-lint

This action will lint Helm charts inside the `charts` folder of your repository.

## Prerequisites

You need to create the lint configuration file `.github/lint-config.yaml` and configure it to your liking.
A minimal configuration could look like this:

```yaml
# check https://github.com/helm/chart-testing/blob/main/pkg/config/test_config.yaml for possible configurations
target-branch: "main"
```

## Input Parameters

| Name                    | Required |       Default Value        |  Type  | Description                                                                                                                              |
| ----------------------- | :------: | :------------------------: | :----: | ---------------------------------------------------------------------------------------------------------------------------------------- |
| ref                     |    ❌    |     The current branch     | string | The ref name to checkout the repository                                                                                                  |
| lint-config-path        |    ❌    | ".github/lint-config.yaml" | string | The path to the lint configuration file (For an example see https://github.com/helm/chart-testing/blob/main/pkg/config/test_config.yaml) |
| helm-version            |    ❌    |         "v3.10.1"          | string | The Helm version                                                                                                                         |
| check-version-increment |    ❌    |           "true"           | string | Activates a check for chart version increments.                                                                                          |

## Usage

```yaml
steps:
  - name: Lint helm charts
    uses: bakdata/ci-templates/actions/helm-lint@main
    with:
      ref: "my-awesome-ref" # (Optional)
      lint-config-path: "my-lint-config.yaml" # (Optional)
      helm-version: "v3.10.1" # (Optional)
```
