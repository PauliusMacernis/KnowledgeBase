- **What is Confd?**  
Confd is a lightweight configuration management tool that allows you to keep configuration files up to date from data stored in backends like environment variables, Consul (https://www.consul.io/), Etcd (https://github.com/coreos/etcd), Redis (https://redis.io/), and others. You can also reload applications to pick up changes during runtime without restarting the container. With Confd, we can separate our configuration management from infrastructure code.  
Read more:  
https://github.com/kelseyhightower/confd/blob/master/docs/quick-start-guide.md  

- **Explain `confd -onetime -backend env`**  
`confd` - Confd is a lightweight configuration management tool that allows you to keep configuration files up to date from data stored in backends like environment variables, Consul (https://www.consul.io/), Etcd (https://github.com/coreos/etcd), Redis (https://redis.io/), and others. You can also reload applications to pick up changes during runtime without restarting the container. With Confd, we can separate our configuration management from infrastructure code.  
`-onetime` - `confd` supports two modes of operation `daemon` and `onetime`. In `daemon` mode `confd` polls a backend for changes and updates destination configuration files if necessary.  
`-backend env` - we pick `env` as the backend for this case. `confd` supports the following backends: `etcd`, `consul`, `vault`, `env` (environment variables), `redis`, `zookeeper`, `dynamodb`, `rancher`, `ssm` (AWS Simple Systems Manager Parameter Store), etc.  
Read more:  
https://github.com/kelseyhightower/confd  
https://github.com/kelseyhightower/confd/blob/master/docs/quick-start-guide.md  
