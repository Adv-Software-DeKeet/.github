# Google Cloud

## Kubernetes

Cluster is set up in Google Cloud.

We have a staging cluster and production cluster.

production cluster is availabe at: https://dekeet.jovisimons.nl/

![cluster](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/gCloudCluster.png)


Here are all the pods running:

![PodsGcloud](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/podsGKE.png)

## Build

For building I use Google Cloud Build. It builds, test, scans and containerized image. see below for more info:

![Build](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/gcloudBuildSum.png)

### Build and test

On master push Google build pipeline runs and run tests, if test fail the build also fails, then it creates a jar file. When jar file is created it creates new image and pushes it to the registry. 


### Sonarcloud

Then I use sonarcloud which scans all my files.

SonarCloud result:

![SonarCloud](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/SonarCloud.png)

### K6 Load testing

It also load tests in my pipeline.

It gets saved in the cloud at K6 and can see the results:

![K6Pipeline](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/K6Pipeline.png)

### Create and push image to registry

After SonarCloud it creates a new image and pushes it my image registry DockerHub. Finally, the deployment gets triggered.

## Deploy

We deploy the newly created image with Google Cloud Deploy. It first deploys on staging cluster and can be tested. Then it can be promoted to production.

![GCPPipeline](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/GCPDeployStag%26Prod.png)