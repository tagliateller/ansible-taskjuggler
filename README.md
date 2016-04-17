# ansible-taskjuggler

Jenkins Install frei nach https://github.com/ICTO/ansible-jenkins
start taskjuggler u.a.

## Installation GitLab

* VM controller auf 192.168.50.10
* VM gitlab auf 192.168.50.21
* private key auf VM gitlab kopieren nach controller

[vagrant@localhost ansible-taskjuggler]$ ansible-playbook --private-key=~/gitlab_private_key -i gitlab.inventory test-gitlab.yml

```
TASK [geerlingguy.gitlab : Copy GitLab configuration file.] ********************
changed: [default]

RUNNING HANDLER [geerlingguy.gitlab : restart gitlab] **************************
fatal: [default]: FAILED! => {"changed": true, "cmd": ["gitlab-ctl", "reconfigure"], "delta": "0:01:38.003977", "end": "2016-04-17 09:35:50.308380", "failed": true, "failed_when_result": true, "rc": 1, "start": "2016-04-17 09:34:12.304403", "stderr": "", "stdout": "init (upstart 1.12.1)\n\u001b[0m\n================================================================================\u001b[0m\n\u001b[31mError executing action `run` on resource 'execute[clear the gitlab-rails cache]'\u001b[0m\n================================================================================\u001b[0m\n\n\u001b[0mMixlib::ShellOut::ShellCommandFailed\u001b[0m\n------------------------------------\u001b[0m\nExpected process to exit with [0], but received ''\n\u001b[0m---- Begin output of /opt/gitlab/bin/gitlab-rake cache:clear ----\n\u001b[0mSTDOUT: \n\u001b[0mSTDERR: \n\u001b[0m---- End output of /opt/gitlab/bin/gitlab-rake cache:clear ----\n\u001b[0mRan /opt/gitlab/bin/gitlab-rake cache:clear returned \u001b[0m\n\n\u001b[0mResource Declaration:\u001b[0m\n---------------------\u001b[0m\n# In /opt/gitlab/embedded/cookbooks/cache/cookbooks/gitlab/recipes/gitlab-rails.rb\n\u001b[0m\n\u001b[0m325: execute \"clear the gitlab-rails cache\" do\n\u001b[0m326:   command \"/opt/gitlab/bin/gitlab-rake cache:clear\"\n\u001b[0m327:   action :nothing\n\u001b[0m328: end\n\u001b[0m329: \n\u001b[0m\n\u001b[0mCompiled Resource:\u001b[0m\n------------------\u001b[0m\n# Declared in /opt/gitlab/embedded/cookbooks/cache/cookbooks/gitlab/recipes/gitlab-rails.rb:325:in `from_file'\n\u001b[0m\n\u001b[0mexecute(\"clear the gitlab-rails cache\") do\n\u001b[0m  action [:nothing]\n\u001b[0m  retries 0\n\u001b[0m  retry_delay 2\n\u001b[0m  default_guard_interpreter :execute\n\u001b[0m  command \"/opt/gitlab/bin/gitlab-rake cache:clear\"\n\u001b[0m  backup 5\n\u001b[0m  returns 0\n\u001b[0m  declared_type :execute\n\u001b[0m  cookbook_name \"gitlab\"\n\u001b[0m  recipe_name \"gitlab-rails\"\n\u001b[0mend\n\u001b[0m\n\u001b[0m", "stdout_lines": ["init (upstart 1.12.1)", "\u001b[0m", "================================================================================\u001b[0m", "\u001b[31mError executing action `run` on resource 'execute[clear the gitlab-rails cache]'\u001b[0m", "================================================================================\u001b[0m", "", "\u001b[0mMixlib::ShellOut::ShellCommandFailed\u001b[0m", "------------------------------------\u001b[0m", "Expected process to exit with [0], but received ''", "\u001b[0m---- Begin output of /opt/gitlab/bin/gitlab-rake cache:clear ----", "\u001b[0mSTDOUT: ", "\u001b[0mSTDERR: ", "\u001b[0m---- End output of /opt/gitlab/bin/gitlab-rake cache:clear ----", "\u001b[0mRan /opt/gitlab/bin/gitlab-rake cache:clear returned \u001b[0m", "", "\u001b[0mResource Declaration:\u001b[0m", "---------------------\u001b[0m", "# In /opt/gitlab/embedded/cookbooks/cache/cookbooks/gitlab/recipes/gitlab-rails.rb", "\u001b[0m", "\u001b[0m325: execute \"clear the gitlab-rails cache\" do", "\u001b[0m326:   command \"/opt/gitlab/bin/gitlab-rake cache:clear\"", "\u001b[0m327:   action :nothing", "\u001b[0m328: end", "\u001b[0m329: ", "\u001b[0m", "\u001b[0mCompiled Resource:\u001b[0m", "------------------\u001b[0m", "# Declared in /opt/gitlab/embedded/cookbooks/cache/cookbooks/gitlab/recipes/gitlab-rails.rb:325:in `from_file'", "\u001b[0m", "\u001b[0mexecute(\"clear the gitlab-rails cache\") do", "\u001b[0m  action [:nothing]", "\u001b[0m  retries 0", "\u001b[0m  retry_delay 2", "\u001b[0m  default_guard_interpreter :execute", "\u001b[0m  command \"/opt/gitlab/bin/gitlab-rake cache:clear\"", "\u001b[0m  backup 5", "\u001b[0m  returns 0", "\u001b[0m  declared_type :execute", "\u001b[0m  cookbook_name \"gitlab\"", "\u001b[0m  recipe_name \"gitlab-rails\"", "\u001b[0mend", "\u001b[0m", "\u001b[0m"], "warnings": []}

PLAY RECAP *********************************************************************
default                    : ok=12   changed=8    unreachable=0    failed=1
```

Aufruf mit Browser: 502 too much time - ingesamt tut sich aber was ...

