# Sonar Compose

The purpose of this repo is to automate the deploy of Sonarqube to an Amazon Lightsail instance. 

Please note that this implementation is not highly available. All components, to include the database, will be configured and deployed to a single Lightsail environment. It is suggested that you use RDS Postgres to create a HA implementation of Sonarqube.

## How do deploy this from AWS Lightsail console

* From the Lightsail console click `Create Instance`.
* Choose whichever region you prefer (us-east-1).
* Under `Select a blueprint` click on `OS Only` and choose Amazon Linux.
* Create an SSH keypair.
* Check `Enable Automatic Snapshots`.
* Choose the instance size. This requires a Sonarqube server and a Postgres, so probably the $10-20/mo version.
* Add your tags.

## SSH into the instance

* Clone this repository.
* Fire up the docker compose in daemon mode:  `docker compose up -d`

### Exposing port 80 or 443

By default, Sonar will be started on port 9000. To expose this over port 80, You can either run a nginx as a reverse proxy or configure IPTables to forward traffic from 80 to 9000. 

Lightsail offers the ability to encrypt traffic with SSL as well > [Lightsail HTTPS](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/understanding-tls-ssl-certificates-in-lightsail-https)
