# Let's Play with Docker

As usual, let's go to <https://killercoda.com/playgrounds/scenario/ubuntu> to get an Ubuntu machine (for 60 minutes).

## Prompt Customization

That's just a question of taste, but I like to cutomize my prompt first.

You can edit the `.bashrc` file:

```text
vi .bashrc
```

and add the following lines at the end:

```bash
# Added by PK
export PS1="\[\e[32m\]\h\[\e[m\]:\w\\$ "
```

Then,  you can execute the command to see the result in all terminal connections:

```text
source .bashrc
```

## Installation

Check the current version of Docker:

```text
docker --version
```

### Uninstall old/unofficial version

```text
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc | cut -f1)
```

### Install using the `apt` repository

#### Add Docker's official GPG key

```text
sudo apt update
```

```text
sudo apt install ca-certificates curl
```

```text
sudo install -m 0755 -d /etc/apt/keyrings
```

```text
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```

```text
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

#### Add the repository to Apt sources:

```text
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF
```

```text
sudo apt update
```

#### Install the latest Docker packages

```text
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

> You can answer `Y` (Yes) to all the questions ;-)

Check if the Docker deamon is running:

```text
sudo systemctl status docker
```

if not, you can start it with:

```text
sudo systemctl start docker
```

If you get the following error message:

```text
Job for docker.service failed because the control process exited with error code.
See "systemctl status docker.service" and "journalctl -xeu docker.service" for details.
```

just wait a few seconds and retry.

### Verify the Installation

Finally, you can verify that the installation is successful by running the `hello-world` image:

```text
sudo docker run hello-world
```

> If you are not using Killercoda, it might interestting to continue the installation with [Manage Docker as a non-root user](https://docs.docker.com/engine/install/linux-postinstall#manage-docker-as-a-non-root-user).

## Introduction

You can now follow the hands-on guide [Develop with containers](https://docs.docker.com/get-started/introduction/develop-with-containers/) and use the workaround from [Let's Play with Killercode](https://github.com/patricekrakow/play-with-killercoda/blob/main/README.md#the-workaround) to expose the HTTP service running just on `localhost` to `0.0.0.0` as required by Killercoda.

## Reference

- https://docs.docker.com/engine/install/ubuntu/

- https://docs.docker.com/get-started/introduction/develop-with-containers/
