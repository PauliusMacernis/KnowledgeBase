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
https://rancher.com/docs/rancher/latest/en/  
https://rancher.com/docs/rancher/latest/en/cattle/rancher-compose/  

- **What are the two main Rancher components?**  
Rancher has two primary components:  
  - Rancher server
  - Rancher host

The server component provides infrastructure orchestration, container orchestration, an application catalog, and authentication control.   
Read more:  
https://rancher.com/docs/rancher/latest/en/  
https://rancher.com/docs/rancher/latest/en/installing-rancher/installing-server/  
https://rancher.com/docs/rancher/latest/en/hosts/  

- **How do Rancher server and host comunicate?**  
The server works with Rancher hosts that run an agent and communicate with the Rancher server over HTTP. You can create a new host from within the Rancher server UI in your cloud provider of choice, or by running the Rancher agent image with docker run on a server.  
Rancher doesn't care if your servers running the agent are virtual or physical as long as they meet the requirements outlined in the documentation.  
Read more:  
https://rancher.com/docs/rancher/latest/en/hosts/  


