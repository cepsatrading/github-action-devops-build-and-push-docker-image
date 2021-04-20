# Build and Push Docker image in Registry

The `github-action-devops-build-and-push-docker-image` Github Action will build and push a Docker image in Registry
## Inputs

| Name | Description | Required |Default |
| --- | --- | --- | --- |
| `repository-name` | Registry repository where the image will be uploaded | :heavy_check_mark: | |
| `image-name` | Name of the image to upload | :heavy_check_mark: | |
| `image-tag` | Tag to include in the image | :heavy_check_mark: | |
| `image-version` | Image version | :heavy_check_mark: | |

## Requirements

* `Dockerfile` file must exist in the root of the project.

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
