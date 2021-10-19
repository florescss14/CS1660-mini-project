This repository contains the source files needed to follow the series [Kubernetes and everything else](https://rinormaloku.com/series/kubernetes-and-everything-else/) or summarized as an article in [Learn Kubernetes in Under 3 Hours: A Detailed Guide to Orchestrating Containers](https://medium.freecodecamp.org/learn-kubernetes-in-under-3-hours-a-detailed-guide-to-orchestrating-containers-114ff420e882)

To learn more about Kubernetes and other related topics check the following examples with the **Sentiment Analysis** application:

* [Kubernetes Volumes in Practice](https://rinormaloku.com/kubernetes-volumes-in-practice/):
* [Ingress Controller - simplified routing in Kubernetes](https://www.orange-networks.com/blogs/210-ingress-controller-simplified-routing-in-kubernetes)
* [Docker Compose in Practice](https://github.com/rinormaloku/k8s-mastery/tree/docker-compose)
* [Istio around everything else series](https://rinormaloku.com/series/istio-around-everything-else/)
* [Simple CI/CD for Kubernetes with Azure DevOps](https://www.orange-networks.com/blogs/224-azure-devops-ci-cd-pipeline-to-deploy-to-kubernetes)
* Envoy series - to be added!
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Link to demo:

https://pitt-my.sharepoint.com/:v:/g/personal/cwf24_pitt_edu/EWRgfWTJsRJPt9xdxipT8vkBX_LfT9NpT2LqHyXVsY9T9A?e=o8QGZD

### Frontend image:

https://hub.docker.com/r/florescss14/sentiment-analysis-frontend

### Logic image:

https://hub.docker.com/r/florescss14/sentiment-analysis-logic

### Webapp image: 

https://hub.docker.com/r/florescss14/sentiment-analysis-web-app

You first have to build the images as seen in the corresponding readme files in sa-frontend, sa-web-app, and sa-logic. Then you can use the following commands on the GCP console to get the images onto the container registry:

**docker pull florescss14/DockerImageName**

Tag your Image with Google proper way:

**docker tag florescss14/DockerImageName  gcr.io/<PROJECT_ID>/florescss14/DockerImageName:version**

Push your Image to the Google Container Registry

**docker push gcr.io/<PROJECT_ID>/florescss14/DockerImageName:version**

I omitted the <PROJECT_ID> for security purposes.

For the logic we need to deploy the pods by:

**kubectl apply -f sa-logic-deployment.yaml**

As we are deploying multiple pods we need to add a service so we can balance them and use both so we do:

**kubectl apply -f service-sa-logic.yaml**

A similar thing is donw with the webapp as we do: 

**kubectl apply -f sa-web-app-deployment.yaml**

**kubectl apply -f service-sa-web-app-lb.yaml**

The frontend code must be changed to the external load balancer of the web application. This means we have to change the link in the App.js file and rebuild the container. This means we repeat the earlier steps and finally do the following:

**kubectl apply -f sa-frontend-deployment.yaml**

By this point it should be up and running and you just have to use the external endpoint given by the frontend pod.






