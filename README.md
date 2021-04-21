# kubernetes-helm-concepts

##### References
- https://github.com/phcollignon/helm3
- https://helm.sh/
- https://artifacthub.io/
- https://kubernetes.io/docs/reference/kubernetes-api/service-resources/service-v1/#ServiceSpec

#### What is the context of using helm?
![screenshot1](screenshot1.PNG)

#### Why helm?
To deploy a single application (production grade), we need to do following things to deploy in kubernetes cluster
- Application
- containerazied application
- deployment and pod
- config map
- secrets
- service
- ingress
- install above resources one by one in correct order

![screenshot2](screenshot2.PNG)

![screenshot3](screenshot3.PNG)

![screenshot4](screenshot4.PNG)

For example - one way could be as follows:

- we write a script by which we deploy all the workload resources mentioned above
- but then what will happen if we need to roll back to previous version of application etc.

![screenshot5](screenshot5.PNG)

![screenshot6](screenshot6.PNG)

![screenshot7](screenshot7.PNG)

- Till now, we have installed new version of application

- Now, Project manager asks to roll back to previous version

- Now, dev ops team realize that they need a tool for packaing and versioning applications

#### what is helm?

- Helm is package manager for kubernetes

![screenshot8](screenshot8.PNG)

![screenshot9](screenshot9.PNG)

#### How does Helm 3 work?
- instead of using kubectl command for each kubernetes object, we embed kubernetes object definitions in 
a package called a chart
-  Chart is then passed to Helm
- Helm connects to kubernetes api to create kubernetes objects
- Helm uses kubernetes client to talk to REST kubernetes API and its security layer

![screenshot10](screenshot10.PNG)

#### Where does Helm store release history and configuration?
- Helm stores release manifests inside Kubernetes as secrets. This provides history and persistence for all the releases.
- These are stored in same namespace as your application namespace
- it is centralized in cluster

#### What will happen if i modify the kubernetes objects with a tool other than Helm?

![screenshot11](screenshot11.PNG)

![screenshot12](screenshot12.PNG)

#### By default, which Kubernetes namespace is used by Helm to store kubernetes objects?
Default namespace but you can tell Helm to use different namespace 

![screenshot13](screenshot13.PNG)

#### How does Kubernetes environment with Helm look like?

![screenshot14](screenshot14.PNG)

![screenshot15](screenshot15.PNG)

#### How to install Helm?
![screenshot16](screenshot16.PNG)

![screenshot17](screenshot17.PNG)

![screenshot18](screenshot18.PNG)

#### By default, Helm is configured to use which repository?
Helm is by default not configured to use any repository. So it has to be manually configured.

#### How to add official Helm chart repository? Also give an example of installing sample chart.
![screenshot19](screenshot19.PNG)
![screenshot20](screenshot20.PNG)

![screenshot21](screenshot21.PNG)
![screenshot22](screenshot22.PNG)
![screenshot23](screenshot23.PNG)

#### What is recommended way to delete objects installed using Helm?
Via uninstall command

![screenshot24](screenshot24.PNG)

#### Please explain a bit around structure of Helm chart.

![screenshot25](screenshot25.PNG)

![screenshot27](screenshot27.PNG)

![screenshot30](screenshot30.PNG)

#### Please explain how we can document around Helm chart.

![screenshot26](screenshot26.PNG)

#### Please explain more about Chart.yaml file.
![screenshot28](screenshot28.PNG)

#### Which are the most commonly used Helm commands?
![screenshot29](screenshot29.PNG)


#### Let's do some exercise

- deploy spring-boot-hello-app using helm

![screenshot30](screenshot30.PNG)
![screenshot31](screenshot31.PNG)
![screenshot32](screenshot32.PNG)
![screenshot33](screenshot33.PNG)
![screenshot34](screenshot34.PNG)
![screenshot35](screenshot35.PNG)
![screenshot36](screenshot36.PNG)
![screenshot37](screenshot37.PNG)


