# Sonar Compose

The purpose of this repo is to automate the deploy of Sonarqube to an Amazon Lightsail instance. 

## How do deploy this from AWS Lightsail console

* From the Lightsail console click `Create Instance`.
* Choose whichever region you prefer (us-east-1).
* Under `Select a blueprint` click on `OS Only` and choose Amazon Linux.
* Click on `+ Add launch script`
* Enter the following into the dialog box:
```bash
curl -o lightsail-compose.sh https://raw.githubusercontent.com/mgivneyjg/sonar-compose/main/deploy.sh

chmod +x ./lightsail-compose.sh

./lightsail-compose.sh
```

* Optionally, create an SSH keypair.
* Check `Enable Automatic Snapshots`.
* Choose the instance size. This requires a Sonarqube server and a Postgres, so probably the $10-20/mo version.
* Add your tags.

## How to start this locally

You can use a .env file to export the environment variables to a local file you don't check into source control.

```docker-compose --env-file .env.dev up -d```
