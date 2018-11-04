# UF Open Source Club's Stack

This contains the Docker configs used to setup the clubs website, back-end, and admin portal. 

It should reference the Dockerfile located in each of those repos. We will use [Git Submodules](https://blog.github.com/2016-02-01-working-with-submodules/) to manage everything.

## Getting Started

We will use Docker to develop test the code.

### Installing

Install [Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and [Docker compose](https://docs.docker.com/compose/install/).

From inside the club-stack directory, download the most up-to-date submodules' master branches with

```bash
git submodule update --init --remote
```

### Running

To run the app

```bash
docker-compose up
```

And go to [localhost:80](http://localhost:80/) for the club website.

Once you are done, you can press "Ctrl-C" in the terminal or type

```bash
docker-compose down -v
```

Be sure to read the [certbot-info](nginx/certbot-info.md) file for information about the SSL Certificate configuration.

## Deployment

When updating the project on the server, **never** run `docker-compose down -v` as that will bring down the website. Instead:

1. Update the Git folder
    ```bash
    git pull
    ```
2. Update the submodules (to their master branches)
    ```bash
    git submodule update --remote
    ```
3. Rebuild the docker image
    ```bash
    docker-compose build
    ```
4. Update the running container
    ```bash
    docker-compose up -d
    ```

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for how to work on the project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
