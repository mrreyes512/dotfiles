# (dot)Files: Mark Reyes

I like stuff. I like my stuff a certain way. Some may say that 300+ aliases and functions is too many... to those I say you haven't turely embraced life until you've given my lazy aliases a shot. If you don't like them, fine then... go away. If you have questions, or want to contribute, great.
This is s sharable role for setting up my environment.


## Requirements

* Access to the new server
* Superuser access required to install packages
* An SSH key saved at `~/.ssh/id_rsa`


## Role Variables

Variables required for playbooks

| Variable | Description | Default | 
| -------- | ----------- | ------- | 
| `REMOTE_SERVER` | IP address of remote server | pi | 
| `USERNAME` | Username to attempt to log in with | mreyes | 
| `SUDO=True` | If sudo access should be attempted | True | 


## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }
```


## License

BSD


## Author Information

* [Mark Reyes](mailto:mark.reyes@charter.com)
