Adding UF to EKS environment - Lessons learned

Indentations in daemonset and config map need to be monitored

ansible-playbook 2.9.6
  config file = /opt/ansible/ansible.cfg
  configured module search path = [u'/opt/ansible/library', u'/opt/ansible/apps/library', u'/opt/ansible/ansible_commands']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible-playbook
  python version = 2.7.16 (default, Sep  3 2019, 19:05:58) [GCC 8.3.1 20190507 (Red Hat 8.3.1-4)]
{
    "_meta": {
        "hostvars": {
            "localhost": {
                "ansible_connection": "local", 
                "ansible_environment": {}, 
                "ansible_post_tasks": null, 
                "ansible_pre_tasks": null, 
                "ansible_ssh_user": "splunk", 
                "cert_prefix": "https", 
                "config": {
                    "baked": "default.yml", 
                    "defaults_dir": "/tmp/defaults", 
                    "env": {
                        "headers": null, 
                        "var": "SPLUNK_DEFAULTS_URL", 
                        "verify": true
                    }, 
                    "host": {
                        "headers": null, 
                        "url": null, 
                        "verify": true
                    }, 
                    "max_delay": 60, 
                    "max_retries": 3, 
                    "max_timeout": 1200
                }, 
                "dmc_asset_interval": "3,18,33,48 * * * *", 
                "dmc_forwarder_monitoring": false, 
                "docker": true, 
                "hide_password": false, 
                "java_download_url": null, 
                "java_update_version": null, 
                "java_version": null, 
                "retry_delay": 6, 
                "retry_num": 60, 
                "shc_sync_retry_num": 60, 
                "splunk": {
                    "admin_user": "admin", 
                    "allow_upgrade": true, 
                    "app_paths": {
                        "default": "/opt/splunkforwarder/etc/apps", 
                        "deployment": "/opt/splunkforwarder/etc/deployment-apps", 
                        "httpinput": "/opt/splunkforwarder/etc/apps/splunk_httpinput", 
                        "idxc": "/opt/splunkforwarder/etc/master-apps", 
                        "shc": "/opt/splunkforwarder/etc/shcluster/apps"
                    }, 
                    "apps_location": [], 
                    "asan": false, 
                    "build_location": null, 
                    "build_url_bearer_token": null, 
                    "cluster_master_url": "", 
                    "deployer_url": "", 
                    "dfs": {
                        "dfc_num_slots": 4, 
                        "dfw_num_slots": 10, 
                        "dfw_num_slots_enabled": false, 
                        "enable": false, 
                        "spark_master_host": "127.0.0.1", 
                        "spark_master_webui_port": 8080
                    }, 
                    "enable_service": false, 
                    "exec": "/opt/splunkforwarder/bin/splunk", 
                    "group": "splunk", 
                    "hec": {
                        "cert": null, 
                        "enable": true, 
                        "password": null, 
                        "port": 8088, 
                        "ssl": true, 
                        "token": null
                    }, 
                    "home": "/opt/splunkforwarder", 
                    "hostname": "splunk-forwarder-dd58c", 
                    "http_enableSSL": false, 
                    "http_enableSSL_cert": null, 
                    "http_enableSSL_privKey": null, 
                    "http_enableSSL_privKey_password": null, 
                    "http_port": 8000, 
                    "idxc": {
                        "enable": false, 
                        "label": "idxc_label", 
                        "pass4SymmKey": null, 
                        "replication_factor": 3, 
                        "replication_port": 9887, 
                        "search_factor": 3, 
                        "secret": null
                    }, 
                    "ignore_license": false, 
                    "launch": {}, 
                    "license_download_dest": "/tmp/splunk.lic", 
                    "license_master_url": "", 
                    "license_uri": "splunk.lic", 
                    "multisite_master_port": 8089, 
                    "multisite_replication_factor_origin": 1, 
                    "multisite_replication_factor_total": 3, 
                    "multisite_search_factor_origin": 1, 
                    "multisite_search_factor_total": 3, 
                    "opt": "/opt", 
                    "pass4SymmKey": null, 
                    "password": "**************", 
                    "pid": "/opt/splunkforwarder/var/run/splunk/splunkd.pid", 
                    "preferred_captaincy": true, 
                    "role": "splunk_universal_forwarder", 
                    "root_endpoint": null, 
                    "s2s": {
                        "ca": null, 
                        "cert": null, 
                        "enable": true, 
                        "password": null, 
                        "port": 9997, 
                        "ssl": false
                    }, 
                    "search_head_captain_url": "", 
                    "secret": null, 
                    "service_name": null, 
                    "set_search_peers": true, 
                    "shc": {
                        "enable": false, 
                        "label": "shc_label", 
                        "pass4SymmKey": null, 
                        "replication_factor": 3, 
                        "replication_port": 9887, 
                        "secret": null
                    }, 
                    "smartstore": null, 
                    "svc_port": 8089, 
                    "tar_dir": "splunkforwarder", 
                    "user": "root", 
                    "wildcard_license": false
                }, 
                "splunk_home_ownership_enforcement": true, 
                "wait_for_splunk_retry_num": 60
            }
        }
    }, 
    "all": {
        "children": [
            "ungrouped"
        ], 
        "hosts": [
            "localhost"
        ], 
        "vars": {
            "ansible_connection": "local", 
            "ansible_environment": {}, 
            "ansible_post_tasks": null, 
            "ansible_pre_tasks": null, 
            "ansible_ssh_user": "splunk", 
            "cert_prefix": "https", 
            "config": {
                "baked": "default.yml", 
                "defaults_dir": "/tmp/defaults", 
                "env": {
                    "headers": null, 
                    "var": "SPLUNK_DEFAULTS_URL", 
                    "verify": true
                }, 
                "host": {
                    "headers": null, 
                    "url": null, 
                    "verify": true
                }, 
                "max_delay": 60, 
                "max_retries": 3, 
                "max_timeout": 1200
            }, 
            "dmc_asset_interval": "3,18,33,48 * * * *", 
            "dmc_forwarder_monitoring": false, 
            "docker": true, 
            "hide_password": false, 
            "java_download_url": null, 
            "java_update_version": null, 
            "java_version": null, 
            "retry_delay": 6, 
            "retry_num": 60, 
            "shc_sync_retry_num": 60, 
            "splunk": {
                "admin_user": "admin", 
                "allow_upgrade": true, 
                "app_paths": {
                    "default": "/opt/splunkforwarder/etc/apps", 
                    "deployment": "/opt/splunkforwarder/etc/deployment-apps", 
                    "httpinput": "/opt/splunkforwarder/etc/apps/splunk_httpinput", 
                    "idxc": "/opt/splunkforwarder/etc/master-apps", 
                    "shc": "/opt/splunkforwarder/etc/shcluster/apps"
                }, 
                "apps_location": [], 
                "asan": false, 
                "build_location": null, 
                "build_url_bearer_token": null, 
                "cluster_master_url": "", 
                "deployer_url": "", 
                "dfs": {
                    "dfc_num_slots": 4, 
                    "dfw_num_slots": 10, 
                    "dfw_num_slots_enabled": false, 
                    "enable": false, 
                    "spark_master_host": "127.0.0.1", 
                    "spark_master_webui_port": 8080
                }, 
                "enable_service": false, 
                "exec": "/opt/splunkforwarder/bin/splunk", 
                "group": "splunk", 
                "hec": {
                    "cert": null, 
                    "enable": true, 
                    "password": null, 
                    "port": 8088, 
                    "ssl": true, 
                    "token": null
                }, 
                "home": "/opt/splunkforwarder", 
                "hostname": "splunk-forwarder-dd58c", 
                "http_enableSSL": false, 
                "http_enableSSL_cert": null, 
                "http_enableSSL_privKey": null, 
                "http_enableSSL_privKey_password": null, 
                "http_port": 8000, 
                "idxc": {
                    "enable": false, 
                    "label": "idxc_label", 
                    "pass4SymmKey": null, 
                    "replication_factor": 3, 
                    "replication_port": 9887, 
                    "search_factor": 3, 
                    "secret": null
                }, 
                "ignore_license": false, 
                "launch": {}, 
                "license_download_dest": "/tmp/splunk.lic", 
                "license_master_url": "", 
                "license_uri": "splunk.lic", 
                "multisite_master_port": 8089, 
                "multisite_replication_factor_origin": 1, 
                "multisite_replication_factor_total": 3, 
                "multisite_search_factor_origin": 1, 
                "multisite_search_factor_total": 3, 
                "opt": "/opt", 
                "pass4SymmKey": null, 
                "password": "**************", 
                "pid": "/opt/splunkforwarder/var/run/splunk/splunkd.pid", 
                "preferred_captaincy": true, 
                "role": "splunk_universal_forwarder", 
                "root_endpoint": null, 
                "s2s": {
                    "ca": null, 
                    "cert": null, 
                    "enable": true, 
                    "password": null, 
                    "port": 9997, 
                    "ssl": false
                }, 
                "search_head_captain_url": "", 
                "secret": null, 
                "service_name": null, 
                "set_search_peers": true, 
                "shc": {
                    "enable": false, 
                    "label": "shc_label", 
                    "pass4SymmKey": null, 
                    "replication_factor": 3, 
                    "replication_port": 9887, 
                    "secret": null
                }, 
                "smartstore": null, 
                "svc_port": 8089, 
                "tar_dir": "splunkforwarder", 
                "user": "root", 
                "wildcard_license": false
            }, 
            "splunk_home_ownership_enforcement": true, 
            "wait_for_splunk_retry_num": 60
        }
    }, 
    "ungrouped": {
        "hosts": []
    }
}

DO NOT CONFIGURE BY HAND! USE DEFAULT ANSIBLE CONFIGS IN SPLUNK-DOCKER!



