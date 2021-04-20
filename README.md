# Run Python Tests and Code Analysis GitHub Action  1.0.0

The `github-action-devops-python-testing` Github Action will run your tests with **Tox and generate coverage, pylint and bandit reports.**

## Inputs

| Name | Description | Required |Default |
| --- | --- | --- | --- |
| `repository-name` | Pylint and Bandit analysis source code base path | :heavy_check_mark: | |
| `image-name` | Pylint and Bandit analysis source code base path | :heavy_check_mark: | |
| `image-tag` | Pylint and Bandit analysis source code base path | :heavy_check_mark: | |
| `image-version` | Pylint and Bandit analysis source code base path | :heavy_check_mark: | |

## Usage

```yaml
name: Build and Push Docker Image to Artifactory Workflow

on:
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Build and Push Docker Image to Artifactory
      uses: cepsadigital/github-action-devops-build-and-push-docker-image@master
      with:
        registry-user: ${{ secrets.TD_ARTIFACTORY_REG_USER }}
        registry-password: ${{ secrets.TD_ARTIFACTORY_REG_TOKEN }}
        repository-name: repository-name
        image-name: image-name
        image-tag: image-tag
        image-version: image-version
```

## Contact

DevOps Team - [Devops Documentation Portal](https://doc.devops.cepsacorp.com/) - devops@cepsa.com

More GitHub Actions in Cepsa TD: [https://github.com/cepsadigital?q=github-action-&type=&language=&sort=](https://github.com/cepsadigital?q=github-action-&type=&language=&sort=)
