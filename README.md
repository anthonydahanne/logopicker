# logopicker
This application was generated using JHipster 4.14.0, you can find documentation and help at [http://www.jhipster.tech/documentation-archive/v4.14.0](http://www.jhipster.tech/documentation-archive/v4.14.0).

This is a "microservice" application intended to be part of a microservice architecture, please refer to the [Doing microservices with JHipster][] page of the documentation for more information.

This application is configured for Service Discovery and Configuration with the JHipster-Registry. On launch, it will refuse to start if it is not able to connect to the JHipster-Registry at [http://localhost:8761](http://localhost:8761). For more information, read our documentation on [Service Discovery and Configuration with the JHipster-Registry][].

## Development

To start your application in the dev profile, simply run:

    ./mvnw


For further instructions on how to develop with JHipster, have a look at [Using JHipster in development][].



## Building for production

To optimize the logopicker application for production, run:

    ./mvnw -Pprod clean package

To ensure everything worked, run:

    java -jar target/*.war


Refer to [Using JHipster in production][] for more details.

## Testing

To launch your application's tests, run:

    ./mvnw clean test
### Other tests

Performance tests are run by [Gatling][] and written in Scala. They're located in [src/test/gatling](src/test/gatling) and can be run with:

    ./mvnw gatling:execute

For more information, refer to the [Running tests page][].

## Using Docker to simplify development (optional)

You can use Docker to improve your JHipster development experience. A number of docker-compose configuration are available in the [src/main/docker](src/main/docker) folder to launch required third party services.

For example, to start a mysql database in a docker container, run:

    docker-compose -f src/main/docker/mysql.yml up -d

To stop it and remove the container, run:

    docker-compose -f src/main/docker/mysql.yml down

You can also fully dockerize your application and all the services that it depends on.
To achieve this, first build a docker image of your app by running:

    ./mvnw verify -Pprod dockerfile:build

Then run:

    docker-compose -f src/main/docker/app.yml up -d

For more information refer to [Using Docker and Docker-Compose][], this page also contains information on the docker-compose sub-generator (`jhipster docker-compose`), which is able to generate docker configurations for one or several JHipster applications.

## Continuous Integration (optional)

To configure CI for your project, run the ci-cd sub-generator (`jhipster ci-cd`), this will let you generate configuration files for a number of Continuous Integration systems. Consult the [Setting up Continuous Integration][] page for more information.

[JHipster Homepage and latest documentation]: http://www.jhipster.tech
[JHipster 4.14.0 archive]: http://www.jhipster.tech/documentation-archive/v4.14.0
[Doing microservices with JHipster]: http://www.jhipster.tech/documentation-archive/v4.14.0/microservices-architecture/
[Using JHipster in development]: http://www.jhipster.tech/documentation-archive/v4.14.0/development/
[Service Discovery and Configuration with the JHipster-Registry]: http://www.jhipster.tech/documentation-archive/v4.14.0/microservices-architecture/#jhipster-registry
[Using Docker and Docker-Compose]: http://www.jhipster.tech/documentation-archive/v4.14.0/docker-compose
[Using JHipster in production]: http://www.jhipster.tech/documentation-archive/v4.14.0/production/
[Running tests page]: http://www.jhipster.tech/documentation-archive/v4.14.0/running-tests/
[Setting up Continuous Integration]: http://www.jhipster.tech/documentation-archive/v4.14.0/setting-up-ci/

[Gatling]: http://gatling.io/

## Deployment

### Configure

* Set zone to whatever you want in `src/main/resources/config/application.yml`
* Set the same zone in `frontend/src/app/app.service.ts`

### Start frontend

```bash
ng server --open
```

### Local

```bash
docker-compose -f src/main/docker/mysql.yml up -d
mvn -Pprod
```

### Heroku

```bash
./deploy_heroku.sh
heroku ps:scale web=0
```

### Google Cloud Platform

### Amazon Beanstalk

### Microsoft Azure

### Cloud Foundry

### Troubleshooting

* [JHipster Registry](https://henri-jhipster-registry.herokuapp.com)

```bash
# could be admin:admin@ is authentication was there
curl -H 'Content-Type: application/json' -H "Accept: application/json" https://henri-jhipster-registry.herokuapp.com/api/eureka/applications
curl -H 'Content-Type: application/json' -H "Accept: application/json" https://henri-jhipster-registry.herokuapp.com/eureka/apps/LOGOPICKER
curl http://localhost:8080/api/logos/current
```

Database cleanup:

```bash
docker exec -ti docker_logopicker-mysql_1 mysql
```

```sql
use logopicker
drop table logo;
drop table jhi_persistent_audit_evt_data;
drop table jhi_persistent_audit_event;
drop table databasechangelog;
drop table databasechangeloglock;
show tables;
```

Env: [http://localhost:8080/management/env](http://localhost:8080/management/env)
