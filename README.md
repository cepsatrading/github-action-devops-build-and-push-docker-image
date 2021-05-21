# Build and Push Docker image in Registry

The `github-action-devops-build-and-push-docker-image` Github Action will build and push a Docker image in Registry
## Inputs

| Name | Description | Required |Default |
| --- | --- | --- | --- |
| `repository-name` | Registry repository where the image will be uploaded | :heavy_check_mark: | |
| `image-name` | Name of the image to upload | :heavy_check_mark: | |
| `image-version` | Image version | :heavy_check_mark: | |
| `path-dockerfile` | Other Dockerfile Path |  | |
| `build-arg` | Build Arguments |  | |

## Requirements

* `Dockerfile` file must exist in the root of the project. In the event that the Dockerfile file is in another path, the input "path-dockerfile" must be used with the path where the file is located.

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
        # Optinals inputs
        # path-dockerfile: (i.e) iac/Dockerfile
        # Considerations: If you only have to introduce an argument, you only have to put the argument. In case there are more arguments, you must include "--build-arg" before each argument.
        # build-arg: some_variable_name_a=a_value --build-arg some_variable_name_b=b_value
```

## Contact

DevOps Team - [Devops Documentation Portal](https://doc.devops.cepsacorp.com/) - devops@cepsa.com

More GitHub Actions in Cepsa TD: [https://github.com/cepsadigital?q=github-action-&type=&language=&sort=](https://github.com/cepsadigital?q=github-action-&type=&language=&sort=)
