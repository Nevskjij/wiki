<!--- Sidebar --->
# Table of Contents
- [What is Docker?](#what-is-docker-)
- [Running a container](#running-a-container-)
- [Configure the container](#configure-the-container-)
    - [Running multiple bots](#running-multiple-bots)
- [Versioning](#versioning-)
<!--- Sidebar --->

# What is Docker [^](#table-of-contents)

According to Wikipedia: **Docker is a set of the platform as service products that use OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries, and configuration files; they can communicate with each other through well-defined channels.**

You can run tf2autobot anywhere, on any operating system that supports Docker, without having to configure additional instances, additional software or having to set up networking.

To download Docker, [head over Docker's download page](https://docs.docker.com/get-docker/). It supports MacOS, Windows and Linux. **Please remember that for Windows, [Hyper-V and Containers need to be enabled](https://docs.docker.com/docker-for-windows/install/#system-requirements) in Windows Features.**

## Use Cases

### Minimal Ops Knowledge

With tf2autobot on Docker, you can learn quickly how to power up a bot without problems and with minimal sysadmin/ops knowledge. You just install Docker and run a command in the terminal and your bot is live.

### Running in Kubernetes

For advanced users, you can orchestrate multiple bots dynamically, both network and workload, using [Kubernetes](https://kubernetes.io/). It can be scheduled as Pod or a StatefulSet replica with 1 replica.

# Running a container [^](#table-of-contents)

Starting with tf2autobot v3.5.0, Docker images are available and you can run the latest, lightweight version of tf2autobot (we recommend using a specific version to avoid breaks):

```bash
$ docker run tf2autobot/tf2autobot:latest-14.16.0-alpine
```

Congrats! You have created your first tf2autobot **container** that runs, **but is not configured and might throw errors**. Follow the instructions to know how to [persist the data](#persisting-the-data) and how to [configure the container](#configure-the-container).

## Persisting the data

The only downside of tf2autobot on Docker is that you need to persist data between your operating system and the container. If you run the container and then you stop it, your `~/tf2autobot/files/<STEAM_ACCOUNT_NAME>/` folder created within the container will no longer exist and will be re-regenerated every time.

To overcome this, we will tell the container to [mount a volume](https://docs.docker.com/storage/volumes/) at the `~/tf2autobot/files/<STEAM_ACCOUNT_NAME>/` folder with a given path in our operating system (like on Desktop for example).

You can use the `-v` flag to specify a mirror between a local path (the path in your PC or on the server) and the container path (which should be, obviously, `~/tf2autobot/files/<STEAM_ACCOUNT_NAME>/`).

We assume the following example, running the command while you're on Desktop and `tf2autobot_data/123456/` folder exists, and the account name is `123456`:

```
$ docker run \
    -v $(pwd)/tf2autobot_data/123456:/home/node/tf2autobot/files/123456 \
    tf2autobot/tf2autobot:latest-14.16.0-alpine
```

**Make sure to replace `123456` with your account name, [as explained in the configuration docs](https://github.com/TF2Autobot/tf2autobot/wiki/Configure-your-options.json-file#using-the-config-generator).**

**The `$(pwd)` at the start of the pathname tells Docker to look for the current context - the current folder we run the command from.**

Every time the container or you will (manually) change files within `~/tf2autobot/files/123456/`, they will persist and you can keep using the bot without fearing the configuration will get lost.

# Configure the container [^](#table-of-contents)

## Environment variables

The recommended way of configuring the container is by using environment variables. In Docker, [you can attach environment variables at runtime](https://docs.docker.com/compose/environment-variables/#set-environment-variables-in-containers) by using the `-e` flag:

```bash
$ docker run \
    -v $(pwd)/tf2autobot_data/123456:/home/node/tf2autobot/files/123456 \
    -e STEAM_ACCOUNT_NAME=some-account-name \
    -e STEAM_PASSWORD=mysecurepassword \
    -e STEAM_SHARED_SECRET="agdgwegdgawfagxafagfkagusbuigiuefh==" \
    tf2autobot/tf2autobot:latest-14.16.0-alpine
```

The environment variables are identical to the ones specified [in the example .env file](https://github.com/TF2Autobot/tf2autobot/wiki/Configuring-the-bot#bot-credentials).

### ecosystem.json

[According to the configuration docs](https://github.com/TF2Autobot/tf2autobot/wiki/Configuring-the-bot), you will need to persist an `ecosystem.json` file in `~/tf2autobot` to configure multiple bots. Like we learned how to persist the data with the `tf2autobot_data` folder, we can as well persist files:

```
$ docker run \
    -v $(pwd)/tf2autobot_data/123456:/home/node/tf2autobot/files/123456 \
    -v $(pwd)/tf2autobot_data/ecosystem.json:/home/node/tf2autobot/ecosystem.json \
    tf2autobot/tf2autobot:latest-14.16.0-alpine
```

### .env

Just like `ecosystem.json`, you can as well [configure](https://github.com/TF2Autobot/tf2autobot/wiki/Configuring-the-bot#--windows) an `.env` file:

```
$ docker run \
    -v $(pwd)/tf2autobot_data/123456:/home/node/tf2autobot/files/123456 \
    -v $(pwd)/tf2autobot_data/.env:/home/node/tf2autobot/.env \
    tf2autobot/tf2autobot:latest-14.16.0-alpine
```

## Running multiple bots

It's highly recommended to run one bot per container to keep the Docker base consistency guidelines. You can however go ahead and configure the ecosystem.json file and have more than one bot per container, but you will need to configure more volumes to mount:

```
$ docker run \
    -v $(pwd)/tf2autobot_data/11111:/home/node/tf2autobot/files/11111 \
    -v $(pwd)/tf2autobot_data/22222:/home/node/tf2autobot/files/22222 \
    -v $(pwd)/tf2autobot_data/ecosystem.json:/home/node/tf2autobot/ecosystem.json \
    tf2autobot/tf2autobot:latest-14.16.0-alpine
```

# Versioning [^](#table-of-contents)

Each Github Release for tf2autobot will automatically create tags for Docker images. The tags follow this pattern:

```
[git_ref]-[node_version]
```

- `[git_ref]` is the git reference tag, like `1.2.0` for releases, `latest` for master and the git commit sha for commits
- `[node_version]` is the Node.js version from [their Docker repo](https://hub.docker.com/_/node/).

### >= 3.5.0

The following `[node_version]` values are used to build images for 3.5.0 and beyond:
- `14.16.0-alpine`
- `14.16.0-buster`
- `14.16.0-buster-slim`
- `14.16.0-stretch`
- `14.16.0-stretch-slim`

### Examples

```bash
$ docker run tf2autobot/tf2autobot:3.5.0-14.16.0-alpine
```

```bash
# using `3.5` instead of any `3.5.x` will install latest `3.5.x` version
$ docker run tf2autobot/tf2autobot:3.5-14.16.0-alpine
```

### I'm new to this, which one to pick?

If you do not know which one to pick, pick `14.16.0-alpine` which is the lightweight one: `tf2autobot/tf2autobot:3.5-14.16.0-alpine` (for example).