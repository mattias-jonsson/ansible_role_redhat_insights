Ansible Role: ansible_role_redhat_insights
=========

Handles installation and configuration of Red Hat Insights agents. This role is inspired by and also contains the insights.facts file from https://github.com/RedHatInsights/insights-client-role.

Supported distributions:

<ul>
<li>Red Hat Enterprise Linux 7
<li>Red Hat Enterprise Linux 8
<li>Red Hat Enterprise Linux 9
</ul>


Role Variables
--------------


| Variable | Required | Default | Comments |
| -------- | -------- | ------- | -------- |
| `ansible_role_redhat_insights_loglevel` | No | DEBUG | Set log level, valid options DEBUG, INFO, WARNING, ERROR, CRITICAL. Default DEBUG, |
| `ansible_role_redhat_insights_auto_config` | No | True | Enable auto configure with Satellite server, |
| `ansible_role_redhat_insights_authmethod` | No | BASIC | Set authentication method, valid options BASIC, CERT. Default BASIC, |
| `ansible_role_redhat_insights_username` | No | | Username to use with BASIC authenticaton. |
| `ansible_role_redhat_insights_password` | No | | Password to use with BASIC authenticaton. |
| `ansible_role_redhat_insights_base_url` | No | cert-api.access.redhat.com:443/r/insights | Base URL for the Insights API. |
| `ansible_role_redhat_insights_proxy` | No | | URL for your proxy.  Example: http://user:pass@192.168.100.50:8080. |
| `ansible_role_redhat_insights_auto_update` | No | True | Automatically update the dynamic configuration. |
| `ansible_role_redhat_insights_obfuscate` | No | False | Obfuscate IP addresses. |
| `ansible_role_redhat_insights_obfuscate_hostname` | No | False | Obfuscate hostname. Requires `ansible_role_redhat_insights_obfuscate=True`. |
| `ansible_role_redhat_insights_display_name` | No | | Display name for registration. |
| `ansible_role_redhat_insights_ansible_host` | No | | Ansible hostname for this system. |
| `ansible_role_redhat_insights_cmd_timeout` | No | 120 | Timeout for commands run during collection, in seconds. |
| `ansible_role_redhat_insights_http_timeout` | No | 120 | Timeout for HTTP calls, in seconds. |
| `ansible_role_redhat_insights_core_collect` | No | True | Use insights-core as the collection source. Included for compatibility only. Modify only as directed. |
| `ansible_role_redhat_insights_redaction_file` | No | /etc/insights-client/file-redaction.yaml | Location of the redaction file for commands, files, and components. |
| `ansible_role_redhat_insights_content_redaction_file` | No | /etc/insights-client/file-content-redaction.yaml | Location of the redaction file for patterns and keywords, |
| `ansible_role_redhat_insights_tags_file` | No | /etc/insights-client/tags.yaml | Location of the tags file for this system. |
| `ansible_role_redhat_insights_enable_malware_scan` | No | False | Enable malware scanning. Note that this feature is still in Beta. |


Example Playbook
----------------


    - hosts: servers

      vars:
        ansible_role_redhat_insights_display_name: somedisplayname
        ansible_role_redhat_insights_ansible_host: somehostname
        ansible_role_redhat_insights_enable_malware_scan: True

      roles:
         - ansible_role_linux_update

License
-------

Apache License, Version 2.0

Author Information
------------------

Mattias Jonsson