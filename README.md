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
| `ansible_role_redhat_insights_malware_scan_enable` | No | False | Enable malware scanning. Note that this feature is still in Beta. |
| `ansible_role_redhat_insights_malware_scan_test_scan` | No | false | Perform a simple test scan of the insights-client config directory and process to verify installation and scanning are working correctly. The results from this scan do not show up in the webUI. Once verified, disable this option to perform actual malware scans. |
| `ansible_role_redhat_insights_malware_scan_scan_filesystem` | No | true | Scan the filesystem? When it is false, the filesystem isn't scanned and the filesystem_* options that follow are ignored |
| `ansible_role_redhat_insights_malware_scan_filesystem_scan_only` | No | | A single or list of files/directories to be scanned and no others, for example: `[/var/www, /home]` means only scan files in /var/www and /home. No value means scan all files and directories |
| `ansible_role_redhat_insights_malware_scan_filesystem_scan_exclude` | No | [/proc, /sys, /cgroup, /selinux, /net, /mnt, /media, /dev] | A single or list of files/directories to be excluded from filesystem scanning. If an item appears in both `ansible_role_redhat_insights_malware_scan_filesystem_scan_only` and in `ansible_role_redhat_insights_malware_scan_filesystem_scan_exclude`, the reusult will be that `ansible_role_redhat_insights_malware_scan_filesystem_scan_exclude` will take precedence and the item will be excluded. |
| `ansible_role_redhat_insights_malware_scan_filesystem_scan_since` | No | | Scan files created or modified since X days ago or since the 'last' scan. Valid values are integers >= 1 or the string 'last'.  For example: `1` would mean scan files created/modified since 1 day ago, `last` would mean scan files created/modified since the last successful scan. No value means scan all files regardless of created/modified date |
| `ansible_role_redhat_insights_malware_scan_exclude_network_filesystem_mountpoints` | No | true | Exclude mounted network/external filesystems mountpoints? Scanning files within mounted network filesystems may be slow and cause extra network traffic. |
| `ansible_role_redhat_insights_malware_scan_network_filesystem_types` | No | [nfs, nfs4, cifs, smbfs, fuse.sshfs, ceph, glusterfs, gfs, gfs2] | List of network/external filesystem types to search for mountpoints on the system. If any mountpoints are found for these filesystem types, the value of the `ansible_role_redhat_insights_malware_scan_exclude_network_filesystem_mountpoints` option will determine if files within the mountpoints are scanned or not. |
| `ansible_role_redhat_insights_malware_scan_scan_processes` | No | false | Scan the running processes? This option is disabled by default to prevent an impact on system performance when scanning numerous or large processes. When it is false, no processes are scanned. |
| `ansible_role_redhat_insights_malware_scan_processes_scan_only` | No | | Processes to be scanned and no others, for example: `["123", "1..100", "10000..", "docker", "chrome"]` means only scan PID 123, PIDs from 1 to 100 inclusive, PIDs >= 10000 and process names containing the strings docker or chrome. No value means scan all processes |
| `ansible_role_redhat_insights_malware_scan_processes_scan_exclude` | No | | Processes to be excluded from scanning. Uses the same syntax as `ansible_role_redhat_insights_malware_scan_processes_scan_only`. If an item appears in both `ansible_role_redhat_insights_malware_scan_processes_scan_only` and in `ansible_role_redhat_insights_malware_scan_processes_scan_exclude` would mean that `ansible_role_redhat_insights_malware_scan_processes_scan_exclude` takes precedence and the item will be excluded. No value means don't exclude any processes |
| `ansible_role_redhat_insights_malware_scan_processes_scan_since` | No | | Scan processes created since X days ago or since the 'last' scan. Valid values are integers >= 1 or the string 'last'. For example: `1` means scan processes created since 1 day ago, `last` means scan processes created since the last successful scan. No value means scan all processes regardless of created date |
| `ansible_role_redhat_insights_malware_scan_add_metadata` | No | true | Add extra metadata about each scan match (if possible), eg file type & md5sum, matching line numbers, process name. The extra metadata will display in the webUI along with the scan matches. |
| `ansible_role_redhat_insights_malware_scan_scan_timeout` | No | 3600 | Abort a particular scan if it takes longer than scan_timeout seconds. |
| `ansible_role_redhat_insights_malware_scan_nice_value` | No | 19 | Run the yara process with this nice priority value.  Default is 19 (lowest priority). |
| `ansible_role_redhat_insights_malware_scan_cpu_thread_limit` | No | | The max number of CPUs threads used by yara when scanning. Autodetected. |

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