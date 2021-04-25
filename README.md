# kubernetes-helm-concepts

##### References
- https://github.com/phcollignon/helm3
- https://helm.sh/
- https://artifacthub.io/
- https://kubernetes.io/docs/reference/kubernetes-api
- https://spring.io/guides/gs/accessing-data-mysql
- https://helm.sh/docs/intro/install/
- https://github.com/asinghalgit/spring-boot-mysql-helm

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

```
- curl -LO https://get.helm.sh/helm-v3.5.4-linux-amd64.tar.gz
- tar -zxvf helm-v3.5.4-linux-amd64.tar.gz 
- sudo mv linux-amd64/helm /usr/local/bin/helm
- helm help
- helm repo add stable https://charts.helm.sh/stable
- helm search repo stable
```
![screenshot16](screenshot16.PNG)

![screenshot17](screenshot17.PNG)

![screenshot18](screenshot18.PNG)

#### By default, Helm is configured to use which repository?
Helm is by default not configured to use any repository. So it has to be manually configured.

#### How to add official Helm chart repository? Also give an example of installing sample chart.

```
- helm search repo stable
- helm repo update
- helm install stable/mysql --generate-name
- helm show chart stable/mysql
- helm show all stable/mysql
- helm ls
- helm list
- helm uninstall smiling-penguin
- helm status smiling-penguin
```

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

- deploy standalone spring-boot-hello-app using helm

```
- 
```
![screenshot30](screenshot30.PNG)
![screenshot31](screenshot31.PNG)
![screenshot32](screenshot32.PNG)
![screenshot33](screenshot33.PNG)
![screenshot34](screenshot34.PNG)
![screenshot35](screenshot35.PNG)
![screenshot36](screenshot36.PNG)
![screenshot37](screenshot37.PNG)
![screenshot39](screenshot39.PNG)
![screenshot40](screenshot40.PNG)

- deploy enterprise app (UI + backend + DB) using helm

![screenshot38](screenshot38.PNG)


- example of installing Guestbook release (1.0 -> 2.0) -> 1.0)

```
- helm install demo-guestbook guestbook
- kubectl get pods -l app=frontend
- helm list --short
- helm get manifest demo-guestbook | less
- helm upgrade demo-guestbook guestbook
- kubectl describe pods -l app=frontend
- helm status demo-guestbook
- helm rollback demo-guestbook 1
- helm history demo-guestbook
- helm uninstall demo-guestbook
```

![screenshot41](screenshot41.PNG)
![screenshot42](screenshot42.PNG)
![screenshot43](screenshot43.PNG)
![screenshot44](screenshot44.PNG)
![screenshot45](screenshot45.PNG)
![screenshot46](screenshot46.PNG)
![screenshot47](screenshot47.PNG)

- example of installing spring-boot-mysql-app

```
- helm create spring-boot
- tree spring-boot
- helm install demo-spring-boot spring-boot
- helm list --short
- helm status demo-spring-boot
- helm history demo-spring-boot
- helm get manifest demo-spring-boot
```

Source Code - https://github.com/asinghalgit/spring-boot-mysql-helm

![screenshot48](screenshot48.PNG)
![screenshot48](screenshot49.PNG)
![screenshot50](screenshot50.PNG)
![screenshot51](screenshot51.PNG)
![screenshot52](screenshot52.PNG)
![screenshot53](screenshot53.PNG)
![screenshot54](screenshot54.PNG)
![screenshot55](screenshot55.PNG)
![screenshot56](screenshot56.PNG)
![screenshot57](screenshot57.PNG)


