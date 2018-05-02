- **What is Rancher?**  
Rancher is an open source software platform that enables organizations to run and manage Docker and Kubernetes in production.
With Rancher, organizations no longer have to build a container services platform from scratch using a distinct set of open source technologies.
Rancher supplies the entire software stack needed to manage containers in production.  
Rancher software consists of four major components:
  - Infrastructure Orchestration. Rancher infrastructure services include networking, storage, load balancer, DNS, and security.
  - Container Orchestration and Scheduling. Rancher includes a distribution of all popular container orchestration and scheduling frameworks today, including Docker Swarm, Kubernetes, and Mesos. In addition to Swarm, Kubernetes, and Mesos, Rancher supports its own container orchestration and scheduling framework called Cattle. Cattle is used extensively by Rancher to orchestrate infrastructure services as well as setting up, managing, and upgrading Swarm, Kubernetes, and Mesos clusters.
  - Application Catalog. Rancher users can deploy an entire multi-container clustered application from the application catalog with one click of a button. 
  - Enterprise-Grade Control. Rancher supports flexible user authentication plugins and comes with pre-built user authentication integration with Active Directory, LDAP, and GitHub. Rancher supports Role-Based Access Control (RBAC) at the level of environments, allowing users and groups to share or deny access to, for example, development and production environments.

In other words, Rancher is container management.  
Rancher provides a nice `UI` that you can use to deploy containers in the Cloud and scale them;  
`Rancher Server` also takes care of issues like networking and load balancing.  
You can also automate your infrastructure deployments with the `Rancher compose CLI`, giving you lots of automation options to truly optimize your deployments.  
Read more:   
https://rancher.com/docs/rancher/v1.6/en/  
https://rancher.com/docs/rancher/v1.6/en/cattle/rancher-compose/  

