gabops.appoptics
================

Installs and configures SolarWinds Appoptics

Requirements
------------

None.

Role Variables
--------------

* `appoptics_managed_config_file:` Configures agent with the values defined in the default variales. If false just installs the agent. Default is **true**
* `appoptics_service_started:` Sets if agent service is started after installing/configuring it. Default is **true**

* `appoptics_log_level:` Sets the log level of the daemon. Default is **info**
* `appoptics_log_path:` Sets the path to store the agent logs. Default is **/var/log/SolarWinds/Snap**
* `appoptics_log_format:` Sets the agent log file format. Default is **text**

* `appoptics_auto_discover_path:` Sets the directory to auto load plugins and tasks on the start of the agent. Defaul is **/opt/SolarWinds/Snap/autoload**
* `appoptics_plugin_trust_level:` Sets the trust level for plugins. Default is **1**

* `appoptics_tls_cert_path:` Sets the TLS certificate path to enable secure plugin communication and authenticate itself to plugins. Default is **""**
* `appoptics_tls_key_path:` Sets the TLS certificate path to enable secure plugin communication and authenticate itself to plugins. Default is **""**
* `appoptics_plugin_tls_key_path:` Sets the path to plugin certificate's key file used during autoload. Default is **""**
* `appoptics_plugin_tls_cert_path:` Sets the path to plugin certificate's key file used during autoload. Default is **""**
* `appoptics_ca_cert_paths:` Sets the list of filesystem paths (files/directories) to CA certificates for use in validating. Default is **""**

* `appoptics_plugin_load_timeout:` Sets the maximal time allowed for a plugin to load. Some plugins may require more time to initialize. Default is **15**
* `appoptics_listen_address:` The bind address the agent uses to control and receive data from plugins. Default is **127.0.0.1**
* `appoptics_listen_port:` The port the agent uses to control and receive data from plugins. Default is **21414**
* `appoptics_temp_dir_path:` sets the temporary directory which houses the temporary files. Default is **/tmp/SolarWinds/Snap**
* `appoptics_temp_dir_enable:` Sets whether the application startup leverage the `temp_path_dir` to start plugins. The use of the temporary location is considered legacy functionality. Default is **false**
* `appoptics_plugin_path:` Search path for load plugin binaries. Default is **/opt/SolarWinds/Snap/bin**
* `appoptics_task_path:` Search path for task file. Default is **/opt/SolarWinds/Snap/etc/tasks.d**
* `appoptics_plugins_include:` Search path for plugin configuration files. Default is **/opt/SolarWinds/Snap/etc/plugins.d**

* `appoptics_token:` Sets the appoptics authentication token Default is **""**
* `appoptics_url:` Sets the appoptics endpoint. Default is **https://api.appoptics.com/v1/measurements**
* `appoptics_hostname_alias:` Sets a hostname alias if you want want a different host tag than the current hostname of the host. Default is **""**
* `appoptics_proxy_url:` Sets the proxy url. Default is **""**
* `appoptics_proxy_user:` Sets the user for authenticating against the proxy configured in 'proxy url' field. Default is **""**
* `appoptics_proxy_password:` Sets the password for authenticating against the proxy configured in 'proxy url' field. Default is **""**
* `appoptics_ec2_check_timeout:` Sets timeout for querying EC2 instance metadata URL to determine if agent is running on EC2 (or OpenStack). Default is **1s**

* `appoptics_gobal_tags:` Defines global tags that will be applied to all collected metrics. Default is **[]**

* `appoptics_rest_api_enable:` Controls enabling or disabling of the REST API for the daemon. Default is **false**
* `appoptics_rest_api_https:` https enables HTTPS for the REST API. If no default certificate and key are provided, then the REST API will generate a private and public key to use for communication. Default is **false**
* `appoptics_rest_api_rest_auth:` Enables authentication for the REST API. Default is **false**

* `appoptics_rest_api_rest_auth_password:` Sets the password to use for the REST API. Currently user and password combinations are not supported. Default is **""**
* `appoptics_rest_api_rest_certificate:` Defines the path to the certificate to use for REST API when HTTPS is also enabled. Default is **""**
* `appoptics_rest_api_rest_key:` The path to the private key for the certificate in use by the REST API when HTTPs is enabled. Default is **""**
* `appoptics_rest_api_rest_port:` Sets the port to start the REST API server on. Default is **21413**

Dependencies
------------

None.

Example Playbook
----------------

```yaml
    - hosts: servers
      vars:
        appoptics_token: secretoken123abc
        appoptics_url: https://api.appoptics.com/v1/measurements
        appoptics_hostname_alias: hostname-01
        appoptics_proxy_url: https://192.168.0.1:8080
        appoptics_proxy_user: user
        appoptics_proxy_password: 123abc
        appoptics_ec2_check_timeout: 5s
        appoptics_tls_cert_path: /tmp/snaptest-cli.crt
        appoptics_tls_key_path: /tmp/snaptest-cli.key
        appoptics_gobal_tags:
          environment: production
          project: foo
      roles:
         - role: gabops.appoptics
```

License
-------

[MIT]((./LICENSE))

Author Information
------------------

Gabriel Suarez ([Gabops](https://github.com/gabops))
