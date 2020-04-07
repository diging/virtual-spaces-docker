# Virtual Spaces with Docker Compose

## Setup

Create two volumes:
- one named `db-data`: this will hold your database data
- one named `vspace-data`: this will hold data used by Virtual Spaces

### Virtual Spaces Configuration 

Into the directory `vspace-data`, put a folder called `config` that contains a copy of [this configuration file](app.properties_example) called `app.properties`. Adjust the properties as necessary.

Note that the property `uploads_path` does not need to be adjusted as this is the internal path in the Docker container where Virtual Spaces will store uploaded files. You will find this folder in your shared volume. The property `app_url` should be set to the actual url of the application, so that it can be used in emails to users, etc.

### Docker-Compose environment files

Docker-compose expects two environment files: `db.env` and `vspace.env`. Both are located in the `config` folder next to the `docker-compose.yml` file.

*db.env*
Adjust the MySQL user information. Note that the three variables `MYSQL_USER`, `MYSQL_PASSWORD`, and `MYSQL_DATABASE` should be the same that are used in the `app.properties` config file.

*vspace.env*
Adjust the Tomcat user information. This will be the user that can be used to redeploy Virtual Spaces later.

## Run

Start docker-compose. If all settings are correct, it should start a MySQL database and Virtual Spaces. Virtual Spaces will then create all necessary tables in the database.

When you start up Virtual Spaces for the first time, go to http://yourserver/vspace. You will be asked to set an administrator password. After that you can create additional users.

## Virtual Spaces Documentation

The documentation for Virtual Spaces can be found [here](https://diging.atlassian.net/wiki/spaces/VS2D).
