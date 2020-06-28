# ansible-clion

This ansible-role installs JetBrains CLion

## What this role does

* Download and extract JetBrains CLion
* Register desktop application
* On arm architecture: Compile pty4j
* On arm architecture: Compile file-watcher

## Tasks

* Download CLion tar file

| Variable       | Type | Mandatory? | Default | Description           |
|----------------|------|------------|---------|-----------------------|
| clion_version  | text | no         | `2020.1.2` | The CLion version  |

## Usage

### Add to `requirements.yml`

```yaml
- name: install-clion
  src: https://github.com/borisskert/ansible-clion.git
  scm: git
```

### example `playbook.yml`

```yaml
- hosts: test_machine
  become: yes

  roles:
    - role: install-clion
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

## License

MIT

## Author Information

* [borisskert](https://github.com/borisskert)
