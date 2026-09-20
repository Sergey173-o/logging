центральный сервер сбора логов (Vagrant + Ansible, rsyslog)
logging-hw/
├── Vagrantfile
└── ansible/
    ├── hosts
    ├── provision.yml
    └── roles/
        ├── web/
        │   ├── tasks/main.yml
        │   ├── handlers/main.yml
        │   └── templates/
        │       ├── nginx-logging.conf.j2
        │       ├── audit-nginx.rules.j2
        │       └── audisp-syslog.conf.j2
        └── log/
            ├── tasks/main.yml
            ├── handlers/main.yml
            └── templates/
                └── rsyslog-central.conf.j2
