[![Quality gate](https://sonarcloud.io/api/project_badges/quality_gate?project=theOval_Oval-UAA)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![SonarCloud](https://sonarcloud.io/images/project_badges/sonarcloud-orange.svg)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)

[![Build Status](https://travis-ci.com/theOval/Oval-UAA.svg?branch=master)](https://travis-ci.com/theOval/Oval-UAA)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=alert_status)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=coverage)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=bugs)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=code_smells)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=vulnerabilities)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=security_rating)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Lines of Code](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=ncloc)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Technical Debt](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=sqale_index)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)
[![Duplicated Lines (%)](https://sonarcloud.io/api/project_badges/measure?project=theOval_Oval-UAA&metric=duplicated_lines_density)](https://sonarcloud.io/dashboard?id=theOval_Oval-UAA)

# The Oval UAA

This is a "uaa" application intended to be part of a micro-service architecture.
This is also a JHipster User Account and Authentication (UAA) Server.
This application is configured for Service Discovery and Configuration with the JHipster-Registry. On launch, it will refuse to start if it is not able to connect to the JHipster-Registry at [http://localhost:8761](http://localhost:8761).

## Development

To start your application in the dev profile, run:

    ./mvnw

For further instructions on how to develop with JHipster, have a look at [Using JHipster in development][].

## Building for production

### Packaging as jar

To build the final jar and optimize the UAA application for production, run:

    ./mvnw -Pprod clean verify

To ensure everything worked, run:

    java -jar target/*.jar


### Packaging as war

To package your application as a war in order to deploy it to an application server, run:

    ./mvnw -Pprod,war clean verify

## Testing

To launch your application's tests, run:

    ./mvnw verify


## Code quality

Sonar is used to analyse code quality. You can start a local Sonar server (accessible on http://localhost:9001) with:

```
docker-compose -f src/main/docker/sonar.yml up -d
```

You can run a Sonar analysis with using the [sonar-scanner](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner) or by using the maven plugin.

Then, run a Sonar analysis:

```
./mvnw -Pprod clean verify sonar:sonar
```

If you need to re-run the Sonar phase, please be sure to specify at least the `initialize` phase since Sonar properties are loaded from the sonar-project.properties file.

```
./mvnw initialize sonar:sonar
```

## Using Docker to simplify development

You can use Docker to improve your JHipster development experience. A number of docker-compose configuration are available in the [src/main/docker](src/main/docker) folder to launch required third party services.

For example, to start a mysql database in a docker container, run:

    docker-compose -f src/main/docker/mysql.yml up -d

To stop it and remove the container, run:

    docker-compose -f src/main/docker/mysql.yml down

You can also fully dockerize your application and all the services that it depends on.
To achieve this, first build a docker image of your app by running:

    ./mvnw -Pprod verify jib:dockerBuild

Then run:

    docker-compose -f src/main/docker/app.yml up -d

