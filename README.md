# LinuxForHealth FHIR Server Quick Setup

Quickly set up the [LinuxForHealth FHIR Server](https://github.com/LinuxForHealth/FHIR).

By default, the FHIR Server service is configured to allow access to ports on the host machine through the host `host.docker.internal`.

It is also assumed that you are using your own persistence layer and not using the embedded Derby database. The fhir-persistence-schema-cli scripts assume that this DB is postgres.

## Pre-requisites

1. Docker
2. FHIR Persistence Schema. Download from the [releases tab](https://github.com/LinuxForHealth/FHIR/releases).

## Instructions

1. Create a `connection.properties` file that includes the following:
   ```
   db.host=<DB_HOST>
   db.port=<DB_PORT>
   db.database=<DB_NAME>
   user=<DB_USER>
   password=<DB_PASSWORD>
   ```
2. Create DB schemas using `create-schemas.sh`.
3. Create tables within the schema using `create-tables.sh`.
4. Create a `server.env` file that contains atleast the following:
   ```
   TZ=<DESIRED SERVER TIMEZONE>
   FHIR_USER_PASSWORD=<>
   FHIR_ADMIN_PASSWORD=<>
   DATABASE_HOST=<>
   DATABASE_PORT=<>
   DATABASE_NAME=<>
   DATABASE_USER=<>
   DATABASE_PASSWORD=<>
   DATABASE_SCHEMA=<>
   WLP_LOGGING_CONSOLE_LOGLEVEL=<>
   ```
5. Create a `server.xml` or override configuration files within the `overrides` directory and configure it as needed following the instructions [here](https://openliberty.io/docs/latest/reference/config/server-configuration-overview.html).
6. Create and configure a `fhir-server-config.json` as needed.
