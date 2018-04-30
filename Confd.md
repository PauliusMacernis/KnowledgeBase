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

- **Explain `confd -interval 10 -backend consul -node consul:8500`**  
`confd` - Confd is a lightweight configuration management tool that allows you to keep configuration files up to date from data stored in backends like environment variables, Consul (https://www.consul.io/), Etcd (https://github.com/coreos/etcd), Redis (https://redis.io/), and others. You can also reload applications to pick up changes during runtime without restarting the container. With Confd, we can separate our configuration management from infrastructure code.  
`-interval 10` - interval (int) - The backend polling interval in seconds. (600 replaced with `10`)  
`-backend consul` - backend (string) - The backend to use. ("etcd" replaced with `consul`)  
`-node consul:8500` - the backend node to get data from. The data is from `consul` service running on the exposed port number `8500` in this case.  
Read more:  
https://github.com/kelseyhightower/confd/blob/master/docs/configuration-guide.md  
https://github.com/kelseyhightower/confd/blob/master/docs/command-line-flags.md  

- **What is the difference between unsing `getv` and `getenv` in the Confd templates?**  
`getenv` function is specific to using environment variables. The other Confd backends use `getv`.  
`getv`  
Returns the value as a string where key matches its argument or an optional default value. Returns an error if key is not found and no default value given. Usage: `value: {{getv "/key"}}`, with a default value: `value: {{getv "/key" "default_value"}}`.  
`getenv`  
Wrapper for os.Getenv. Retrieves the value of the environment variable named by the key. It returns the value, which will be empty if the variable is not present. Optionally, you can give a default value that will be returned if the key is not present. Usage: `
export HOSTNAME=hostname; hostname: {{getenv "HOSTNAME"}}`, with a default value: `ipaddr: {{getenv "HOST_IP" "127.0.0.1"}}`.  
Read more:  
https://github.com/kelseyhightower/confd/blob/master/docs/templates.md#getv  
https://github.com/kelseyhightower/confd/blob/master/docs/templates.md#getenv  




