# setting up gitlab-runner

This will install the latest version of `gitlab-ci-multi-runner`.

Assuming you created a brand new Ubuntu instance using [ubuntu-setup](ubuntu-setup.md) and you have a recent version of [Docker installed](install-docker.md).

### Install gitlab-runner
```
curl -L https://packages.gitlab.com/install/repositories/runner/gitlab-ci-multi-runner/script.deb.sh | sudo bash
sudo apt-get install gitlab-ci-multi-runner

sudo usermod -aG docker gitlab-runner
```

#### Register gitlab runner
```
sudo gitlab-ci-multi-runner register
# select shell runner
```

Visit the [official repository](https://gitlab.com/gitlab-org/gitlab-ci-multi-runner) for more details.
