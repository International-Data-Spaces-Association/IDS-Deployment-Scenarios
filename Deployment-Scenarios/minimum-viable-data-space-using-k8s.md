# IDS deployment scenarios 

## Introduction - How to deploy an IDS-Testbed using  [<img src="../images/img-buildkite/kubernetes.png" width="20" height="20" alt="kubernetes"/>](https://kubernetes.io/)
This is a deployment scenario provided by [Atos](https://atos.net/es/spain) You can find the content on its [original repository](https://github.com/FlexiGroBots-H2020/Data-Space/tree/External-connector)

The European data strategy focuses strongly on the ideas of data sharing and data spaces. This blog explains how to deploy and use a data space through Kubernetes technology [International Data Spaces Association](https://internationaldataspaces.org/). You will see specifically how data between a "provider" and a "user" is shared based on the installation and configuration defined in the [IDS testbed](https://github.com/International-Data-Spaces-Association/IDS-testbed/blob/master/InstallationGuide.md), but the data space will be running in a K8S cluster instead of a Docker Compose. For a detailed explanation of the individual components of the infrastructure, please refer to the official [Reference Architecture Model](https://internationaldataspaces.org/wp-content/uploads/IDS-Reference-Architecture-Model-3.0-2019.pdf). 

# Deployment
## Steps to deploy a data space using K8s
One of the most typical topics in the development of a product is the deployment process. Usually in development-phases is usual to use tools such as docker, docker-compose, env, etc, but these kinds of tools are not oriented to production environments. Therefore, it has been developed a set of manifests to deploy an IDS-Testbed in a Kubernetes cluster. This allows re-create a real environment and it is easier to migrate from local to cloud.
To achieve this change of architecture is essential to design each manifest using the official IDSA components. In addition, it is necessary to use a reverse proxy to access the cluster, in this case, two reverse proxies have been tested, Nginx and Traefik. For reasons of scalability, cloud-management and visibility, Traefik offers better performance than Nginx. Even so, both methods are in the repository [IDS-testbed-k8s-folder].

### Minimum requirements

This architecture has been tested on a laptop with the following requirements:

Software requirements
- [Kubectl](https://kubernetes.io/es/docs/tasks/tools/) version:
  - Client Version: `v1.24.0`
  - Kustomize Version: `v4.5.4`
  - Server Version: `v1.24.0`
- [Kompose](https://kompose.io/)
  - `1.26.0`

- Cluster runs in [Docker-Desktop](https://docs.docker.com/desktop/windows/install/)
  - `v20.10.14`

-  [IDS-Release 1.0](https://github.com/International-Data-Spaces-Association/IDS-testbed)
-   OS Windows 10 Enterprise
    -   WSL2: Ubuntu 20.04 LTS
  
- OpenSSL `1.1.1f`



Hardware-requirements

The characteristics of the PC used are:

- 16 GB RAM.
- Intel(R) Core(TM) i5-10310U CPU @ 1.70GHz   2.21 GHz.

- 237 GB ROM memory.

## CLI steps

Firstly, it is necessary to download the *repository[IDS-testbed-k8s-folder] with the manifests.

```git clone https://github.com/International-Data-Spaces-Association/IDS-testbed/```

It is important to have some sort of cluster either local or cloud. To test the system it is recommended to run the system in the local environment. And, when the specification of the local system has been established the next step would be to migrate the architecture to the cloud. In addition, the Nginx setup only validated to run in a local cluster

After that, the reverse proxy has to be the first component to be deployed. There are two folders one with Nginx and another with Trafik. The commands to deploy the Nginx are the following:


```kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.2.0/deploy/static/provider/cloud/deploy.yaml```

`kubectl apply -f ./Nginx/4-ingress-connection-nginx.yaml `

Regarding Traefik is available both local and cloud, thus, in order to deploy a Traefik in a local machine the 4-ingresroute-local has to be deployed instead of deploying in a cluster the file 4-ingressroute-rancher has to be deployed. The commands to run this reverse proxy are the following, it is important to run the commands in order:

`kubectl apply -f ./traefik/9-rbac.yaml `

`kubectl apply -f ./traefik/7-crd-yaml `

`kubectl apply -f ./traefik/0-service.yaml `

`kubectl apply -f ./traefik/1-deployment.yaml`

`kubectl apply -f ./traefik/8-middleware.yaml `

`kubectl apply -f ./traefik/10-pvc.yaml`

`kubectl apply -f ./traefik/4-ingressroute-rancher.yaml`


After raising the reverse-proxy the next step is to launch the data space. In order to work in a cluster using good practices it is essential to have a clean environment, for this reason, it is important to create a namespace for the DataSpace. 
The easiest way to create a namespace is using the next command. In this case, ids-2 is the name of the namespace. 
  
  `kubectl create namespace ids-2`

Finally, it has been created two folders with similar content. The difference is in the deployment environment, so, the idsa_manifest_local is oriented for a local cluster and the idsa_manifests_rancher is oriented for a cloud cluster (in this case in a Rancher cluster). But, the way to install both folders is the same.

`kubectl apply -f ./idsa_manifest_local/Broker/0-broker-core-services.yaml -n ids-2`

`kubectl apply -f ./idsa_manifest_local/Broker/1-broker-core-deploy.yaml -n ids-2`

`kubectl apply -f ./idsa_manifest_local/Broker/2-daps-broker-confimap.yaml -n ids-2`


`kubectl apply -f ./idsa_manifest_local/Connectors/0-connectors-services.yaml -n ids-2`

`kubectl apply -f ./idsa_manifest_local/Connectors/1-connectorA.yaml -n ids-2`

`kubectl apply -f ./idsa_manifest_local/Connectors/2-connectorB.yaml -n ids-2`

`kubectl apply -f ./idsa_manifest_local/Connectors/2-connectors-configmap.yaml -n ids-2`

`kubectl apply -f ./idsa_manifest_local/Connectors/3-connectors-secrets.yaml -n ids-2`


`kubectl apply -f ./idsa_manifest_local/Omejdn/0-omejdn-services.yaml -n ids-2`

`kubectl apply -f ./idsa_manifest_local/Omejdn/1-omejdn-deployments.yaml -n ids-2`

`kubectl apply -f ./idsa_manifest_local/Omejdn/2-omejdn-configmap.yaml -n ids-2`

## External Connector

In order to ensure that any connector can register in the deployed data space, the repository [IDS-testbed-k8s-folder] includes a Dataspace connector V(8.0.2) with the minimum requirements to register it to the data space.

~~~
services:
  connectorc:
    image: ghcr.io/international-data-spaces-association/dataspace-connector:latest
    container_name: connectorc
    ports:
      - XXXX:XXXX
    networks:
      - local

    volumes:
      - ./conf/config.json:/config/config.json
      - ./conf/testbed4.p12:/conf/testbedX.p12
      - ./conf/connectorC.p12:/config/connectorX.p12
      - ./conf/truststore.p12:/config/truststore.p12

    environment:
      - CONFIGURATION_PATH=/config/config.json
      - SERVER_PORT=8082
      - DAPS_URL='https://URL-WITH-EXPOSED-DAPS.eu'
      - DAPS_TOKEN_URL=https://URL-WITH-EXPOSED-DAPS.eu/auth/token
      - DAPS_KEY_URL=https://URL-WITH-EXPOSED-DAPS.eu/auth/jwks.json
      

      - DAPS_WHITELISTED_URL=http://URL-WITH-EXPOSED-DAPS.eu/auth,http://omejdn/auth
      - DAPS_INCOMING_DAT_DEFAULT_WELLKNOWN=/jwks.json
      
      #- OMEJDN_DOMAIN=http://URL-WITH-EXPOSED-DAPS.eu/auth/
      - SERVER_SSL_KEY-STORE=file:///config/connectorC.p12
networks:
  local:
    driver: bridge
~~~

## Test the system and utilization


The file TestbedPreconfigurationK8s.postman_collection has been modified to test the data space and the connectors. This file has a request set to check the data space status. It is recommended to pass all tests before using the data space. 

The *[IDS-testbed-k8s-folder] repository has a little library in .ipynb that facilitates the use of the data space. This library is written in python and is designed to use simple functions and send any type of data through the data space. 

Piece of code here


This system has been used in an European real project to join the data exchange among pilots. The name of this project is FlexigroBots and its goal is the creation of data value chains in the agriculture environment that maximize synergies, collaboration, and opening of new business opportunities based on data while ensuring sovereignty and security is one of the main goals of the H2020 FlexiGroBots project. To achieve all that, an IDSA-compliant DataSpace has been implemented to be deployed and operated in cloud-native infrastructures managed by Kubernetes.

In addition to being one of the requirements of the project, it is essential for FlexiGroBots that data is shared among the different stakeholders of the agri-food domain (e.g., IoT platforms providers, farm management systems vendors, robotics systems manufacturers) to break the silos that currently exist and to enable more powerful services to be developed. From the existing IDSA open-source testbed that relies on Docker containers and Docker-compose for the deployment and orchestration, an @Atos team has developed all necessary manifests to achieve the aforementioned deployment to realise an IDS-Testbed using a Kubernetes cluster. It is being used in collaboration with the rest of the partners of FlexiGroBots to enable information to be exchanged in three different agricultural pilots.



---


To learn more about this topic, please consult the [IDSA Reference Architecture Model](https://internationaldataspaces.org/use/reference-architecture/) and the implementations of the main connectors, [Eclipse](https://github.com/eclipse-dataspaceconnector/DataSpaceConnector) and the [IDS Reference Connector](https://github.com/International-Data-Spaces-Association/DataspaceConnector/). For any comments or suggestions on this guide, we also invite you to contact us. 

---

### CREDITS
This article was written by [Antonio Carlos Cob Parro](https://www.linkedin.com/in/carlos-cob-parro/) under the supervision of [Daniel Calvo Moreno](https://www.linkedin.com/in/calvoad/).

A. Carlos Cob is Telecommunications engineer and software developer specialised in artificial intelligence and machine learning.

Daniel Calvo is Telecommunications engineer with more than 10 years of experience working on research and innovation projects in the area of embedded systems, edge computing, Internet of Things (IoT) and Artificial Intelligence.



'*'repository[IDS-testbed-k8s-folder]: We need to know where to push the manifests. I do not know if you would prefer to have the deployment in the IDS-TesteBed repository or another different repository. I wrote Sonia about that because we have prepared whole documentation about k8s deployment. Even so, we will be looking forward to hearing from you.