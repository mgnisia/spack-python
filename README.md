![](https://img.shields.io/docker/pulls/mgnisia/spack-python)

# Spack Container for Python CI Testing

This repo contains a `Dockerfile` which can be used as a container for testing in a CI or local environment.

Currently the following python environments are include:

- Python 3.5
- Python 3.6
- Python 3.7
- Python 3.8

Import to mention is also that for the Python 3.5 version the openssl dependency works out of the box. Python3.5 requires an `openssl` version of lower than `1.1.0`.


## Tox Example 

In Gitlab Pipeline this container could be used as:

```
.job_template_spack: &spack
  image: imagename
  variables:
    LC_ALL: C.UTF-8
    LANG: C.UTF-8
  before_script:
    - . ~/spack/share/spack/setup-env.sh
    - spack load py-tox

py35:
  <<: *spack
  stage: test
  script:
    - spack load python@3.5.0
    - tox -e py35
```
