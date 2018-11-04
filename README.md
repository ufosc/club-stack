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
docker-compose up -d
```

And go to [localhost:80](http://localhost:80/) for the club website.

Once you are done, you can press "Ctrl-C" in the terminal or type

```bash
docker-compose down -v
```

Be sure to read the [certbot-info](nginx/certbot-info.md) file for information about the SSL Certificate configuration.

<!-- ## Deployment

**Additional steps to deploy and run the project**
 -->

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for how to work on the project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
