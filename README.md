# Build and Push Docker image in Registry

The `github-action-devops-build-and-push-docker-image` Github Action will build and push a Docker image in Registry
## Inputs

| Name | Description | Required |Default |
| --- | --- | --- | --- |
| `repository-name` | Registry repository where the image will be uploaded | :heavy_check_mark: | |
| `image-name` | Name of the image to upload | :heavy_check_mark: | |
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
    - name: Checkout Git Source
      uses: actions/checkout@v2
    - name: Get Time
      id: time
      uses: nanzm/get-time-action@v1.1
      with:
        format: 'YYYYMMDDHHmmss'
    - name: Build and Push Docker Image to Artifactory
      uses: cepsatrading/github-action-devops-build-and-push-docker-image@master
      with:
        registry-user: ${{ secrets.ARTIFACTORY_REG_USER }}
        registry-password: ${{ secrets.ARTIFACTORY_REG_TOKEN }}
        repository-name: repository-name
        image-name: image-name
        image-tag: "${{ steps.time.outputs.time }}"
        image-version: image-version-${{ steps.time.outputs.time }}
```

## Contact

DevOps Team - [Devops Documentation Portal](https://doc.devops.cepsacorp.com/) - devops@cepsa.com

More GitHub Actions in Cepsa TD: [https://github.com/cepsadigital?q=github-action-&type=&language=&sort=](https://github.com/cepsadigital?q=github-action-&type=&language=&sort=)
