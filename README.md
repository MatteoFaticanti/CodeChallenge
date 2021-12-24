# CodeChallenge

## Environment

The local environment used to test the scripts had the following software:

| Software  | Version |
| ------------- | ------------- |
| Ubuntu  | 20.04.3 LTS |
| ansible  | 2.9.6 |
| python | 3.8.10 |

## Ansible Directory Layout

```
.
├── ansible.cfg
├── hosts
├── main.yml
└── roles
    ├── ansible-role-docker-ce
    │   ├── LICENSE
    │   ├── README.md
    │   ├── meta
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   ├── tests
    │   │   └── test.yml
    │   └── vars
    │       └── main.yml
    └── provision_instances
        ├── tasks
        │   └── main.yml
        └── vars
            └── main.yml
```

## Requirements

Installed and configured [Google Cloud Platform](https://docs.ansible.com/ansible/latest/scenario_guides/guide_gce.html)  
Installed Google Auth [Python package](https://pypi.org/project/google-auth/)  
Add ssh key to the Google Cloud Project using the command `gcloud compute project-info add-metadata --metadata-from-file ssh-keys=[SSH_KEY_PATH]`

## How to use this repository

change the variables in `/roles/provision_instances/vars/main.yml` with your own Google Cloud configuration

```
---
# vars file for provision_instances

gcp_project: ancient-vortex-196211
gcp_cred_kind: serviceaccount
gcp_cred_file: "/home/matteo/ancient-vortex-196211-d41d6d452d40.json"
gcp_ssh_key: ~/.ssh/google_compute_engine.pub
```
## Execute playbook

The playbook can be executed using `ansible-playbook main.yml`

## References

Documentation for [Ansible Google Cloud Collection](https://docs.ansible.com/ansible/latest/collections/google/cloud/)  
Ansible official [Google Cloud platform guide](https://docs.ansible.com/ansible/latest/scenario_guides/guide_gce.html)  
[Using Ansible to automate Google Cloud Platform](https://developers.redhat.com/blog/2020/05/06/using-ansible-to-automate-google-cloud-platform)  
[Ansible Role docker CE](https://github.com/bt5e/ansible-role-docker-ce)
