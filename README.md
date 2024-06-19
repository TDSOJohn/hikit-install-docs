
# Install Hikit for development

First draft of hikit development install guide.

An IDE with support for typescript and Kotlin is recommended (ex.: Intellij IDEA Ultimate).

A software that interacts with databases could help when debugging database interactions (ex.: Datagrip).

### Repositories

- [Hikit](https://github.com/SeC-Hikit/Hikit)
- [Hikit frontend](https://github.com/SeC-Hikit/Hikit-Frontend-CAIBO)
- [Hikit-Common](https://github.com/SeC-Hikit/Hikit-Common)

There are also these additional services to interface with other public APIs.
These are not required for a basic installation but provide additional features or information to the user.

- [Hikit-ERT](https://github.com/SeC-Hikit/Hikit-ERT)
- [Hikit-Weather](https://github.com/SeC-Hikit/Hikit-Weather)
- [Hikit-OSM](https://github.com/SeC-Hikit/Hikit-OSM)

### Dependencies

- Hikit
    - Java 11 SDK
    - Maven 3
    - [MongoDB](https://www.mongodb.com/)
    - [MongoDB database tools](https://www.mongodb.com/docs/database-tools/installation/installation/)

- Hikit frontend
    - Nodejs 16 (currently tested with 16.14.2)

### Run local instance

First of all clone and build [Hikit-Common](https://github.com/SeC-Hikit/Hikit-Common).

Then, after cloning this repo, simply run `mvn install -f root/pom.xml -P microservice-binding`.

Some changes are needed in order to test everything locally. Namely, `application.properties` contains paths that need to point to a local folder for temporary storage and logging.

Change these values:
- `storage.path`
- `temp.storage.path`
- `logging.file.name`
- `keycloak.truststore`

Run Hikit's Main.java
- use Java 11 SDK
- set the root of the project as working directory
- link to `application.properties` in CLI arguments

Open Hikit-frontend
- set the correct node version with `nvm use 16.14.2`
- run the development server with `ng serve --proxy-config src/proxy.conf.json --host 0.0.0.0`

Add the entry to the maintenance MongoDB database with

`mongorestore --dir=./db --gzip -d=prod`
