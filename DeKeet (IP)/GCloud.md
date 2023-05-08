# Google Cloud

## Kubernetes

Cluster is set up in Google Cloud.

We have a staging cluster and production cluster.

production cluster is availabe at: https://dekeet.jovisimons.nl/

![cluster](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/gCloudCluster.png)

## Build

On master push Google build pipeline runs and run tests, if test fail the build also fails, then it creates a jar file. When jar file is created it creates new image and pushes it to the registry. Finally, the doplyment gets triggered:

![BuildSucceed](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/gcloudBuild.png)


## Deploy

We deploy the newly created image with Google Cloud Deploy. It first deploys on staging cluster and can be tested. Then it can be promoted to production.

![GCPPipeline](https://github.com/Adv-Software-DeKeet/.github/blob/main/DeKeet%20(IP)/images/GCPDeployStag%26Prod.png)