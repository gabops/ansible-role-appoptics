gabops.appoptics
================

Installs and configures SolarWinds Appoptics

Requirements
------------

None.

Role Variables
--------------

* `appoptics_add_repository`: true
* `appoptics_managed_config_file`: Configures agent with the values defined in the default variales. If false just installs the agent. Default is **true**
* `appoptics_service_started`: Sets if agent service is started after installing/configuring it. Default is **true**

* `appoptics_log_level`: Sets the log level of the agent. Default is **info**
* `appoptics_log_path`: Sets the path to store the agent logs. Default is **/var/log/SolarWinds/Snap**
* `appoptics_log_format`: Sets the agent log file format. Default is **text**

* `appoptics_auto_discover_path`: Sets the directory to auto load plugins and tasks on the start of the agent. Defaul is **/opt/SolarWinds/Snap/autoload**
* `appoptics_plugin_trust_level`: 0

* `appoptics_tls_cert_path`: /tmp/snaptest-cli.crt
* `appoptics_tls_key_path`: /tmp/snaptest-cli.key
* `appoptics_plugin_tls_key_path`: /tmp/snaptest-srv.key
* `appoptics_plugin_tls_cert_path`: ""
* `appoptics_ca_cert_paths`: /tmp/small-setup-ca.crt:/tmp/medium-setup-ca.crt:/tmp/ca-certs/

* `appoptics_plugin_load_timeout`: 5
* `appoptics_listen_address`: 127.0.0.1
* `appoptics_listen_port`: 21414
* `appoptics_temp_dir_path`: /tmp/SolarWinds/Snap
* `appoptics_temp_dir_enable`: false
* `appoptics_plugin_path`: /opt/SolarWinds/Snap/bin
* `appoptics_task_path`: /opt/SolarWinds/Snap/etc/tasks.d
* `appoptics_plugins_include`: /opt/SolarWinds/Snap/etc/plugins.d

* `appoptics_publisher_plugins`: []

* `appoptics_gobal_tags`: Defines global tags that will be applied to all collected metrics. Default is **[]**

* `appoptics_rest_api_https`: false
* `appoptics_rest_api_enable`: false
* `appoptics_rest_api_rest_auth`: false
* `appoptics_rest_api_rest_auth_pwd`: ""
* `appoptics_rest_api_rest_certificate`: ""
* `appoptics_rest_api_rest_key`: ""
* `appoptics_rest_api_rest_port`: 21413

Dependencies
------------

None.

Example Playbook
----------------

```yaml
    - hosts: servers
      vars:
        appoptics_tls_cert_path: /tmp/snaptest-cli.crt
        appoptics_tls_key_path: /tmp/snaptest-cli.key
        appoptics_gobal_tags:
          environment: production
          project: foo
        appoptics_publisher_plugins:
          - plugin_name: publisher-appoptics
            config:
              token: "secretoken123abc"
              url: https://api.appoptics.com/v1/measurements
              hostname_alias: hostname-01
              proxy_url: proxy_url: https://192.168.0.1:8080"
              proxy_user: user
              proxy_password: 123456
              ec2_check_timeout: 1s
          - plugin_name: publisher-processes
            config:
              token: "secretoken123abc"
              url: https://api.appoptics.com/v1/measurements

      roles:
         - role: gabops.appoptics
```

License
-------

[MIT]((./LICENSE))

Author Information
------------------

Gabriel Suarez ([Gabops](https://github.com/gabops))
