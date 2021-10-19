This repository contains the source files needed to follow the series [Kubernetes and everything else](https://rinormaloku.com/series/kubernetes-and-everything-else/) or summarized as an article in [Learn Kubernetes in Under 3 Hours: A Detailed Guide to Orchestrating Containers](https://medium.freecodecamp.org/learn-kubernetes-in-under-3-hours-a-detailed-guide-to-orchestrating-containers-114ff420e882)

To learn more about Kubernetes and other related topics check the following examples with the **Sentiment Analysis** application:

* [Kubernetes Volumes in Practice](https://rinormaloku.com/kubernetes-volumes-in-practice/):
* [Ingress Controller - simplified routing in Kubernetes](https://www.orange-networks.com/blogs/210-ingress-controller-simplified-routing-in-kubernetes)
* [Docker Compose in Practice](https://github.com/rinormaloku/k8s-mastery/tree/docker-compose)
* [Istio around everything else series](https://rinormaloku.com/series/istio-around-everything-else/)
* [Simple CI/CD for Kubernetes with Azure DevOps](https://www.orange-networks.com/blogs/224-azure-devops-ci-cd-pipeline-to-deploy-to-kubernetes)
* Envoy series - to be added!
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Link to demo: https://pitt-my.sharepoint.com/:v:/g/personal/cwf24_pitt_edu/EWRgfWTJsRJPt9xdxipT8vkBX_LfT9NpT2LqHyXVsY9T9A?e=o8QGZD

frontend image: https://hub.docker.com/r/florescss14/sentiment-analysis-frontend
logic image: https://hub.docker.com/r/florescss14/sentiment-analysis-logic
webapp image: https://hub.docker.com/r/florescss14/sentiment-analysis-web-app

You first have to build the images as seen in the corresponding readme files in sa-frontend, sa-web-app, and sa-logic. Then you can use the following commands on the GCP console to get the images onto the container registry:
docker pull florescss14/DockerImageName

Tag your Image with Google proper way:
docker tag florescss14/DockerImageName  gcr.io/<PROJECT_ID>/florescss14/DockerImageName:version

Push your Image to the Google Container Registry
docker push gcr.io/<PROJECT_ID>/florescss14/DockerImageName:version
