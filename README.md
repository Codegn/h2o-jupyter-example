# H2O exploration

## I) To test a H2O standalone service, in order to use H2O FLOW

### First time

docker run -it --name h2o-test -p 54321:54321 -p 54322:54322 openjdk:8 bash
wget http://h2o-release.s3.amazonaws.com/h2o/rel-yau/1/h2o-3.26.0.1.zip
unzip h2o-3.26.0.1.zip
cd h2o-3.26.0.1
java -jar h2o.jar

Point your browser to http://localhost:54321

### Restarting service

docker start h2o-test -ai
cd home/h2o-3.26.0.1
java -jar h2o.jar

Point your browser to http://localhost:54321

## II) Use docker-compose file to run a H2O container and a jupyter container that can connect to it.
docker-compose up
copy the jupyter url into your browser.

you still can go to http://localhost:54321 to use h2o flow.

when you are done:
docker-compose down

Note: The entrypoint in the docker-compose file for the h2o service uses -Xmx8g that set the maximum amount of memory that the java virtual machine is able to use. If this is not set then by default it uses 2gb.

The test notebook contains an AutoML example.