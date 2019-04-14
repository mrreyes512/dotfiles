# (dot)Files: Mark Reyes

I like stuff. I like my stuff a certain way. Some may say that 300+ aliases and functions is too many... to those I say you haven't turely embraced life until you've given my lazy aliases a shot. If you don't like them, fine then... go away. If you have questions, or want to contribute, great.
This is s sharable role for setting up my environment.


## Requirements

* Access to the new server
* Repo root must contain a few files
  * aliases
  * id_rsa.pub
  * vimrc
  * zshrc
* Superuser access required to install packages


## Role Variables

Variables required for playbooks

| Variable | Description | Default | 
| -------- | ----------- | ------- | 
| `REMOTE_SERVER` | IP address of remote server | raspberrypi.local | 
| `USERNAME` | Username to attempt to log in with | pi | 
| `PASSWORD` | Username to attempt to log in with | raspberry | 
| `SUDO=True` | If sudo access should be attempted | True | 


## Example Playbook

An Example Playbook: `plays/send_env`

```yaml
- name: Set My Environment
  hosts: "{{ target | default('just_created') }}"
  gather_facts: False
  tasks:
  - include_role: 
      name: dotfiles
    vars:
      MY_PACKAGES: [ git, vim, zsh, figlet ]
      UPDATE_CACHE: true
```


## License

BSD


## Author Information

* [Mark Reyes](mailto:mark.reyes@charter.com)
