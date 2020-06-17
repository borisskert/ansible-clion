# ansible-clion

This ansible-role installs JetBrain's CLion

## Tasks

* Download CLion tar file

| Variable       | Type | Mandatory? | Default | Description           |
|----------------|------|------------|---------|-----------------------|
| clion_version  | text | no         | `2020.1.2` | The CLion version  |

## Usage

### Playbook

```yaml
- hosts: test_machine
  become: yes

  roles:
    - role: ansible-clion
      clion_version: 2020.1.2
```

## Testing

Requirements:

* [Ansible](https://docs.ansible.com/)
* [Molecule](https://molecule.readthedocs.io/en/latest/index.html)
* [yamllint](https://yamllint.readthedocs.io/en/stable/#)
* [ansible-lint](https://docs.ansible.com/ansible-lint/)
* [Docker](https://docs.docker.com/)

### Run within docker

```shell script
molecule test
```

I recommend to use [pyenv](https://github.com/pyenv/pyenv) for local testing.
Within the Github Actions pipeline I use [my molecule Docker image](https://github.com/borisskert/docker-molecule).
