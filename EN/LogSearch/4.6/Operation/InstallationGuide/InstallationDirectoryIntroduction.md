# Installation directory introduction

## 1. Overall directory overview

```bash
bklog
├── api
│ ├── apps
│ ├── bin
│ ├── bkoauth
│ ├── blueapps
│ ├── blueking
│ ├── config
│ ├── flower_proxy
│ ├── home_application
│ ├── __init__.py
│ ├── locale
│ ├── manage.py
│ ├── README.md
│ ├── requirements_env.txt
│ ├── requirements.txt
│ ├── runtime.txt
│ ├── settings.py
│ ├── sites
│ ├── static
│ ├── templates
│ ├── urls.py
│ ├── VERSION
│ ├── version_log
│ ├── version_logs
│ ├── version_logs_html
│ └── wsgi.py
├── projects.yaml
├── support-files
│ └── templates
└── VERSION
```

- `api` - submodule, here is consistent with the source code of the SaaS package
- `projects.yaml` - package information
- `VERSION` - version number, consistent with SaaS, to facilitate version maintenance

## 2. bin directory

The bin directory mainly provides a command set for background command operations.

```bash
├── bin
│ ├── environ.sh
│ └── manage.sh
```

- `environ.sh` - Provides environment variables necessary for application running, such as `APP_ID`, `APP_TOKEN`, `DB_USERNAME`, etc.
- `manage.sh` - An encapsulation of the `python manage.py` command. When executed, `source environ.sh` will be first loaded to load the environment variables.

For example, to enter the django console, you can execute the following command

```bash
bin/manage.sh shell
```

## 3. support-files directory

The `templates` directory is used to store template files. Some variables can only be determined during deployment, such as domain name, deployment IP, and component password. These variables can be written into the template in the form of placeholders, rendered during deployment, and written to the specified directory.

```bash
support-files
└── templates
     ├── #etc#supervisor-bklog_search.conf
     └── log_search#bin#environ.sh
```