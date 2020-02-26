# Ansible Trip - Day 1 pm - Install Ansible

With Ansible, all stories start with a playbook.

Our [playbook1.yml] just contain one *task* that says hello.

Launch it using Ansible :

```
ansible-playbook -i localhost, playbook1.yml
```

The command above should print you this :

```
PLAY [My fist playbook] *******************************************************************************************************************

TASK [My first task] **********************************************************************************************************************
ok: [localhost] => {
    "msg": "Hello World !"
}

PLAY RECAP ********************************************************************************************************************************
localhost                  : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

It's often verbose but alway meanfull. You just have to understand it's langage.

* Your playbook named `My fist playbook` has been PLAYed on the host `localhost`
* The second task was named [debug] and says `Hello World !`in a `debug` message.
* The recap explain you what has been done !

That's all folks !

Congratulations, you are almost an Ansible star !
