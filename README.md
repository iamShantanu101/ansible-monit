# Ansible monit role

Ansible role for installing and configuring monit on servers.

# Directory structure

```
.
├── defaults
│   └── main.yml
├── files
│   └── check-monit.sh
├── handlers
│   └── main.yml
├── tasks
│   └── main.yml
├── templates
│   └── monitrc.j2
└── vars
    └── main.yml
```

# Configurable variables (necesary to set them before trying out the role.)

```
mmonit_user:
mmonit_pass:

monit_username:
monit_password:

monit_notify_email:
```

# Commands to execute the role

1. Running the role based on tags:

**Tags Available**

```
monit_installed - Checks if monit is installed
monit_ver       - Checks monit version 
install_monit   - Do a fresh monit install
configure_monit - Configure monit installation (main monitrc config)
```

Examples:

```
ansible-playbook -i hosts --tags "monit_installed,monit_ver" monit.yml
```

Note: Tags monit_installed and monit_ver needs needs to ran together as both are dependent on each other

```
ansible-playbook -i hosts --tags "monit_installed,monit_ver,install_monit" monit.yml
```

2. Running the complete playbook

```
ansible-playbook -i hosts monit.yml
```

Note the way tags are incrementally used to check the state on target host individually. The final command will run the complete playbook 


3. That's it. Grab yourself a piece of cookie and enjoy automating.
