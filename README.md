# self_host_confluent_platform

Estudo sobre Confluent Platform Self-Hosted
link: https://docs.confluent.io/platform/current/platform-quickstart.html

## 0 - Adjustments

On Mac: Docker memory is allocated minimally at 6 GB (Mac). When using Docker Desktop for Mac, the default Docker memory allocation is 2 GB. Change the default allocation to 6 GB in the Docker Desktop app by navigating to Preferences > Resources > Advanced.

On Windows: Docker Desktop for Windows is running on WSL 2. For more information, see How to Run Confluent on Windows in Minutes.

## 1 - Download or copy the contents of the Confluent Platform all-in-one Docker Compose file

> curl --silent --output docker-compose.yml https://raw.githubusercontent.com/confluentinc/cp-all-in-one/7.3.3-post/cp-all-in-one/docker-compose.yml

## 2 - Start the Confluent Platform stack with the -d option to run in detached mode:

> docker-compose up -d

Each Confluent Platform component starts in a separate container. Your output should resemble:

> Creating network "cp-all-in-one_default" with the default driver
> Creating zookeeper ... done
> Creating broker    ... done
> Creating schema-registry ... done
> Creating rest-proxy      ... done
> Creating connect         ... done
> Creating ksql-datagen    ... done
> Creating ksqldb-server   ... done
> Creating control-center  ... done
> Creating ksqldb-cli      ... done

## 3 - Verify that the services are up and running:

> docker-compose ps

After a few minutes, if the state of any component isn’t Up, run the docker-compose up -d command again, or try docker-compose restart <image-name>, for example:

> docker-compose restart control-center

https://docs.confluent.io/platform/current/platform-quickstart.html#step-3-generate-mock-data

https://docs.confluent.io/platform/current/platform-quickstart.html#step-4-create-a-stream-and-table-by-using-sql-statements