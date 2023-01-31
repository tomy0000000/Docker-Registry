# Docker Images

The source code for my custom Docker images on [Docker Hub](https://hub.docker.com/u/tomy0000000).

Use the ansible playbook in [tomy0000000/playbooks](https://github.com/tomy0000000/playbooks/) to setup docker daemon first.

## Installation

Most image (service) comes in two format, `Dockerfile` and `Docker Compose`.

Generally, Dockerfile is designed as a simple development runtime. Whereas Docker Compose is designed to managed / visualized complicated configuration, in addition, `restart=always` flag enables the container to daemonized as services.

Consult each README for detailed usage.

### Awesome Variables

Dockerfiles might use some of the following variables to provide consistent experience.

* `AWESOME_USER`: The username of the service or login shell in the container
* `AWESOME_PASSWORD`: The password of the service, or the user password in the container
* `AWESOME_HOST`: The hostname used in the container

#### Declare manually per shell session

```sh
# password can be generated with `openssl rand -base64 32`
export AWESOME_USER=$USER
export AWESOME_PASSWORD="Vb8abtQWOmOF19UPOPXALMWedupIlLcxt12/9tYb5Dc="
export AWESOME_HOST=$HOST
```

#### Add to your `.bashrc`, `.zshrc`, `config.fish`

```sh
echo -e 'export AWESOME_USER=$USER\nexport AWESOME_PASSWORD='$(openssl rand -base64 32)'\nexport AWESOME_HOST=$HOST' >> ~/.zshrc
```

## Custom Setting

Custom setting comes in three type: `Applied`, `Runtime`, `Host Machine`.

The following chart indicate which type of settings is handled using different approach.

|              | Dockerfile | Docker Compose |
| ------------ | ---------- | -------------- |
| Applied      | ✅          | ✅              |
| Runtime      | ❌*         | ✅              |
| Host Machine | ❌          | ❌              |

\**Runtime settings is not handled in Dockerfile, but can be handle using command given in README*

If not specified, settings is required by default. Therefore, if your installation method doesn't handle correctly, unexpected results might happened.
