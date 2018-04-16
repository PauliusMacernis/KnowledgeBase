# PHP Xdebug

- **Explain the following lines found in `xdebug.ini` file:**  
```
[xdebug]
xdebug.default_enable=1
xdebug.remote_autostart=1
xdebug.remote_connect_back=1
xdebug.remote_port=9001
xdebug.remote_enable=1
xdebug.idekey=DOCKER_XDEBUG
```

`xdebug.default_enable`  
Type: boolean, Default value: `1`  
If this setting is 1, then stacktraces will be shown by default on an error event. You can disable showing stacktraces from your code with xdebug_disable(). As this is one of the basic functions of Xdebug, it is advisable to leave this setting set to 1.  

`xdebug.remote_autostart`  
Type: boolean, Default value: `0`  
Normally you need to use a specific HTTP GET/POST variable to start remote debugging (see Remote Debugging). When this setting is set to 1, Xdebug will always attempt to start a remote debugging session and try to connect to a client, even if the GET/POST/COOKIE variable was not present.  

`xdebug.remote_connect_back`  
Type: boolean, Default value: `0`, Introduced in Xdebug >= 2.1  
If enabled, the `xdebug.remote_host` setting is ignored and Xdebug will try to connect to the client that made the HTTP request. It checks the `$_SERVER['HTTP_X_FORWARDED_FOR']` and `$_SERVER['REMOTE_ADDR']` variables to find out which IP address to use.  
If `xdebug.remote_addr_header` is configured, then the `$SERVER` variable with the configured name will be checked before the `$_SERVER['HTTP_X_FORWARDED_FOR']` and `$_SERVER['REMOTE_ADDR']` variables.  
This setting does not apply for debugging through the CLI, as the `$SERVER` header variables are not available there.  
Please note that there is no filter available, and anybody who can connect to the webserver will then be able to start a debugging session, even if their address does not match `xdebug.remote_host`.  

`xdebug.remote_port`  
Type: integer, Default value: `9000`  
The port to which Xdebug tries to connect on the remote host. Port `9000` is the default for both the client and the bundled debugclient. As many clients use this port number, it is best to leave this setting unchanged.  

`xdebug.remote_enable`  
Type: boolean, Default value: `0`  
This switch controls whether Xdebug should try to contact a debug client which is listening on the host and port as set with the settings `xdebug.remote_host` and `xdebug.remote_port`. If a connection can not be established the script will just continue as if this setting was `0`.  

`xdebug.idekey`  
Type: string, Default value: `*complex*`  
Controls which IDE Key Xdebug should pass on to the `DBGp` debugger handler. The default is based on environment settings. First the environment setting `DBGP_IDEKEY` is consulted, then `USER` and as last `USERNAME`. The default is set to the first environment variable that is found. If none could be found the setting has as default `''`. If this setting is set, it always overrides the environment variables.  

