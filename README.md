# Environments

In this repository you can find some environments for testing [Kraken](https://github.com/kraken-ng/Kraken) implants and modules.

Kraken environments are about YAML files to deploy different web applications using **Docker Compose**.

The existing environments are distributed in:
- [PHP](php): containers deploying PHP web platforms.
  - Apache 2.4.53 + PHP 8.0.18
  - Apache 2.4.25 + PHP 7.0.33
  - Apache 2.4.10 + PHP 5.4.45
- [Java](java): containers deploying Java (JSP) web platforms.
  - Tomcat 10.1.5 + JDK 17
  - Tomcat 10.1.0-M14 + JDK 16
  - Tomcat 9.0.45 + JDK 15
  - Tomcat 9.0.39 + JDK 14
  - Tomcat 9.0.33 + JDK 13
  - Tomcat 8.5.47 + JDK 12
  - Tomcat 10.1.5 + JRE 11
  - Tomcat 9.0.13 + JRE 10
  - Tomcat 9.0.8 + JRE 9
  - Tomcat 9.0.20 + JRE 1.8
  - Tomcat 7.0.94 + JRE 1.7
  - Tomcat 7.0.91 + JRE 1.6

> Currently there is no environment for testing .NET agents. The easiest way to do this is deploying an Internet Information Services (IIS) on a Windows machine and uploading the .NET agent as an aspx file. Future releases will incorporate deployment environments using Vagrant in order to cover all technologies.

## Usage

To deploy the environments, Docker Compose must be used along with its corresponding YAML configuration file.

An example of deploying PHP containers:

```bash
# Deploying containers in daemon mode (no need to build because images are used)
docker compose -f php/docker-compose.yml up -d
docker compose -f php/docker-compose.yml up php8-apache -d

# Unloading the deployed containers
docker compose -f php/docker-compose.yml down -v

# Accessing the deployed php8-apache container
docker compose -f php/docker-compose.yml exec php8-apache bash
```

> **Warning:** before deploying the environments, ensure that you have the necessary resources (space and memory).

## Contribute

You can add new web platforms to Kraken environments. To do so, simply follow the steps below:

1. Create the Docker Compose compatible deployment file.
2. Validate and ensure the correct functioning of Kraken agents for the technology in use by the container (do not add a deployment environment in which Kraken does not function correctly).
3. Open a pull request and I will merge it ASAP.

Any contribution is appreciated, since validating the tool in different environments ensures its correct operation.
