![img.shields.io](https://img.shields.io/badge/GITHUB-ACTION-blue?style=for-the-badge&logo=github)
![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg?style=for-the-badge)
![opa](https://img.shields.io/badge/OPA-DOCKER-orange?style=for-the-badge)


# Open Policy Agent - Conftest

## What is conftest?

Conftest is a utility to help you write tests against structured configuration data. For instance you could write tests for your Kubernetes configurations, or Tekton pipeline definitions, Terraform code, Serverless configs or Docker configurations.

Conftest will test the data you provide it (Dockerfiles, Kubernetes manifests, etc) and compare it against rules written in the rego language used by `Open Policy Agent`.
By default Conftest will check the current working directory for a sub-directory named “policy”, rules in here will be evaluated against the data you’re testing.

## Usage in your repo:

Add the below code in your repo:


```yaml
on: push
name: OPA Docker
jobs:
  docker-security:
    runs-on: ubuntu-latest
# Please copy the steps below this
    steps:
    - uses: actions/checkout@master
    - name: OPA Docker
      uses: ebomart/opa-docker@v1.0
      with:
        file: Dockerfile
```

The Conftest Action has a small number of properties which map to the parameters for Conftest itself. These are passed to the action using with, as demonstrated with files in the above example.

| Property | Default   | Description  |   
|---        |---        |---|
| file      | -         | Dockerfile to test  |
| output    | stdout    | How to format the output from Conftest  |
|  policy   | policy    | Where to find the policy folder or files  |