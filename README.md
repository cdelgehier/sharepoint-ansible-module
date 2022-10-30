[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
# Ansible Collection - cdelgehier.sharepoint

This collection embeds a module allowing to manage basic actions with a tool like sharepoint.

## Requirements

The goal was to make a fairly low dependency module.
The only dependencies are:
- requests
- json
- os

## Module Variables

If an essential variable is missing, the module will try to look in the execution environment.

To define them just export them in the shell.

```shell
export SHAREPOINT_CLIENT_ID='1fd2d8ee-ab64-4ea7-91ff-4ff0eeaea745@8762bcf7-08b4-4439-b003-b37c748b5be4'
```
```shell
export SHAREPOINT_CLIENT_SECRET='/5D97FFE09CE34047B691A5C2E8AFC896='
```
```shell
export SHAREPOINT_TENANT_NAME='mycompany'
```
```shell
export SHAREPOINT_TENANT_ID='8613c317-2809-4c99-acf4-8bca8c4daffa'
```
```shell
export SHAREPOINT_SITE_NAME='mydepartment'
```

## Usage

The use of environment variables greatly simplifies the writing of tasks but it is possible to specify these variables in each task.


### Push a file to a folder
```yaml
- name: "Push file to test folder"
  sharepoint:
    client_id: "{{ client_id }}"
    client_secret: "{{ client_secret }}"
    tenant_name: "{{ tenant_name }}"
    tenant_id: "{{ tenant_id }}"
    site_name: "{{ site_name }}"

    local_file_path: /Users/cedricd
    local_file_name: test.txt
    remote_file_path: "{{ remote_file_path }}"
```

### Get a file from a folder
```yaml
- name: "Get file from sharepoint"
  sharepoint:
    method : get
    client_id: "{{ client_id }}"
    client_secret: "{{ client_secret }}"
    tenant_name: "{{ tenant_name }}"
    tenant_id: "{{ tenant_id }}"
    site_name: "{{ site_name }}"

    remote_file_path: "{{ remote_file_path }}"
    remote_file_name: test.txt
    local_file_path: /Users/cedricd
    local_file_name: another_test.txt
```

### Delete a file in a folder
```yaml
- name: "Delete file in sharepoint"
  sharepoint:
    method : delete
    client_id: "{{ client_id }}"
    client_secret: "{{ client_secret }}"
    tenant_name: "{{ tenant_name }}"
    tenant_id: "{{ tenant_id }}"
    site_name: "{{ site_name }}"

    remote_file_path: "{{ remote_file_path }}"
    remote_file_name: test.txt
```

### List the contents of a folder
```yaml
- name: "List the contents of a folderr"
  sharepoint:
    method : list
    client_id: "{{ client_id }}"
    client_secret: "{{ client_secret }}"
    tenant_name: "{{ tenant_name }}"
    tenant_id: "{{ tenant_id }}"
    site_name: "{{ site_name }}"

    remote_file_path: "{{ remote_file_path }}"
```

### Create folder in sharepoint
```yaml
- name: "Create folder in sharepoint"
  sharepoint:
    method : mkdir
    client_id: "{{ client_id }}"
    client_secret: "{{ client_secret }}"
    tenant_name: "{{ tenant_name }}"
    tenant_id: "{{ tenant_id }}"
    site_name: "{{ site_name }}"

    remote_file_path: "{{ remote_file_path }}/plop"
```

### Delete folder in sharepoint
```yaml
- name: "Remove folder in sharepoint"
  sharepoint:
    method : rmdir
    client_id: "{{ client_id }}"
    client_secret: "{{ client_secret }}"
    tenant_name: "{{ tenant_name }}"
    tenant_id: "{{ tenant_id }}"
    site_name: "{{ site_name }}"

    remote_file_path: "{{ remote_file_path }}/plop"
```

## Changelog

See changelog.

## License

GNU GENERAL PUBLIC LICENSE v3
