# rhidm_manager_users

## Description:

Configure Users and Groups inside RH IdM (IPA)

_Note: Still work in progress_

## Behaviour:

**Feature:** Configure users and groups inside RH IdM (IPA)
- **Given** a VM of capable size and power is available
- **Given** the connection details to the VM are known
- **Given** the hostname has been set and configured properly
- **Given** there is working DNS and NTP available
- **Given** the host is using a valid Red Hat subscription
- **Given** Installed Red Hat Identity Management on a system
- **When** A new user / group need to be configured in RH IdM (IPA)
- **Then** Get a kerberos ticket
- **Then** Configure IPA
- **Then** IPA add group admins
- **Then** IPA add Administrative users
- **Then** IPA add Administrative user to admin group
- **Then** IPA add group users
- **Then** IPA add users
- **Then** IPA add user to user group
- **Then** Destroy ticket

## Configuration:

Common variables used by this role:

| Variable  | Required | Description  | Example  | 
|---|---|---|---|
| **rhidm_default_password** | yes | Default Password for IDM | rhidm_default_password=redhat123 |

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Install RH IDM
  include_role:
    name: rhidm_install_application
  vars:
    projects:
      - name: 'DEV'
        automation_server: "yes"
        admins:
          - devAdmin@acme.com
        users:
          - dev1@acme.com
          - dev2@acme.com
      - name: 'TEST'
        admins:
          - testAdmin@acme.com
        users:
          - tester1@acme.com
          - tester2@acme.com
```
