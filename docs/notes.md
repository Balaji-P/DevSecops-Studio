
Jenkins Issues:
===============

1. Setup wizard appear even when jenkins.install.runSetupWizard=false

Fix is to add the following to geerlingguy.jenkins role task

```bash
- name: Fix a defect to disable setup wizard
  jenkins_script:
    script: |
      import static jenkins.model.Jenkins.instance as jenkins
      import jenkins.install.InstallState
      if (!jenkins.installState.isSetupComplete()) {
        InstallState.INITIAL_SETUP_COMPLETED.initializeState()
      }
    user: "{{ admin.userid }}"
    password: "{{ admin.password }}"
```

2. Plugin installation fails so added retries, see https://github.com/geerlingguy/ansible-role-jenkins/issues/169
so added following four lines to plugins.yml task  

```bash
  retries: 2                # https://github.com/geerlingguy/ansible-role-jenkins/issues/169
  delay: 3
  register: result            # <<<
  until: result is succeeded  # <<<
 
```

2. Because of a bug, wizard will show even after successful installation of Jenkins

Fix is to add the following task as disable-wizard.yml and call it from main.yml

see https://github.com/geerlingguy/ansible-role-jenkins/issues/181

```bash
- name: Fix a defect to disable setup wizard
  jenkins_script:
    script: |
      import static jenkins.model.Jenkins.instance as jenkins
      import jenkins.install.InstallState
      if (!jenkins.installState.isSetupComplete()) {
        InstallState.INITIAL_SETUP_COMPLETED.initializeState()
      }
    user: "{{ jenkins_admin_username }}"
    password: "{{ jenkins_admin_password }}"
```

Gitlab
=======

- Verify the gitlab works fine locally in VM because of docker bug on Travis

DevSecOps-Box
=============
- Don't forget to add machine's host name in hosts_entry.yml once you a add new box.
