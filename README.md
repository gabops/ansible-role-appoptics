gabops.appoptics
================
[![Build Status](https://travis-ci.org/gabops/ansible-role-appoptics.svg?branch=master)](https://travis-ci.org/gabops/ansible-role-appoptics)

Installs and configures SolarWinds Appoptics

Requirements
------------

None.

Role Variables
--------------

| Variable | Default value | Description |
| --- | --- | --- |
| appoptics_managed_config_file | true | Configures agent with the values defined in the default variales. If false just installs the agent. |
| appoptics_service_started | true | Sets if agent service is started after installing/configuring it. |
|appoptics_log_level | info | Sets the log level of the daemon. |
|appoptics_log_path | /var/log/SolarWinds/Snap | Sets the path to store the agent logs. |
|appoptics_log_format | text | Sets the agent log file format. |
|appoptics_auto_discover_path | /opt/SolarWinds/Snap/autoload | Sets the directory to auto load plugins and tasks on the start of the agent. |
|appoptics_plugin_trust_level | 1 | Sets the trust level for plugins. |
|appoptics_tls_cert_path | "" | Sets the TLS certificate path to enable secure plugin communication and authenticate itself to plugins. |
|appoptics_tls_key_path | "" | Sets the TLS certificate path to enable secure plugin communication and authenticate itself to plugins. |
|appoptics_plugin_tls_key_path | "" | Sets the path to plugin certificate's key file used during autoload. |
|appoptics_plugin_tls_cert_path | "" | Sets the path to plugin certificate's key file used during autoload. |
|appoptics_ca_cert_paths | "" | Sets the list of filesystem paths (files/directories) to CA certificates for use in validating. |
|appoptics_plugin_load_timeout | 15 | Sets the maximal time allowed for a plugin to load. Some plugins may require more time to initialize. |
|appoptics_listen_address | 127.0.0.1 | The bind address the agent uses to control and receive data from plugins. |
|appoptics_listen_port | 21414 | The port the agent uses to control and receive data from plugins. |
|appoptics_temp_dir_path | /tmp/SolarWinds/Snap | Sets the temporary directory which houses the temporary files. |
|appoptics_temp_dir_enable | false | Sets whether the application startup leverage the `temp_path_dir to start plugins. The use of the temporary location is considered legacy functionality. |
|appoptics_plugin_path | /opt/SolarWinds/Snap/bin | Search path for load plugin binaries. |
|appoptics_task_path | /opt/SolarWinds/Snap/etc/tasks.d | Search path for task file. |
|appoptics_plugins_include | /opt/SolarWinds/Snap/etc/plugins.d | Search path for plugin configuration files. |
|appoptics_token | "" | Sets the appoptics authentication token. |
|appoptics_url | https://api.appoptics.com/v1/measurements | Sets the appoptics endpoint. |
|appoptics_hostname_alias | "" | Sets a hostname alias if you want want a different host tag than the current hostname of the host. |
|appoptics_proxy_url | "" | Sets the proxy url. |
|appoptics_proxy_user | "" | Sets the user for authenticating against the proxy configured in 'proxy url' field. |
|appoptics_proxy_password | "" | Sets the password for authenticating against the proxy configured in 'proxy url' field. |
|appoptics_ec2_check_timeout | 5s | Sets timeout for querying EC2 instance metadata URL to determine if agent is running on EC2 (or OpenStack). |
|appoptics_gobal_tags | [] | Defines global tags that will be applied to all collected metrics. |
|appoptics_rest_api_enable | false | Controls enabling or disabling of the REST API for the daemon. |
|appoptics_rest_api_https | false | Enables HTTPS for the REST API. If no default certificate and key are provided, then the REST API will generate a private and public key to use for communication. |
|appoptics_rest_api_rest_auth | false | Enables authentication for the REST API. |
|appoptics_rest_api_rest_auth_password | "" | Sets the password to use for the REST API. Currently user and password combinations are not supported. |
|appoptics_rest_api_rest_certificate | "" | Defines the path to the certificate to use for REST API when HTTPS is also enabled. |
|appoptics_rest_api_rest_key | "" | The path to the private key for the certificate in use by the REST API when HTTPs is enabled. |
|appoptics_rest_api_rest_port | 21413 | Sets the port to start the REST API server on. |

> For more information about agent configuration see [Appoptics agent configuration](https://docs.appoptics.com/kb/host_infrastructure/host_agent/configuration/)

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
