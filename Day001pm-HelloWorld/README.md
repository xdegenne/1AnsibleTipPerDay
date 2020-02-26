# Ansible Trip - Day 1 pm - Hello World !

With Ansible, all stories start with a **playbook**.

Our [playbook1.yml](playbook1.yml) just contains one **task** that says hello.

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

* Your playbook named `My fist playbook` has been PLAYed on the host `localhost`.
* The first (an unique) task it contains is named `My first task` and says `Hello World !`in a debug `msg`.
* The recap explains you what has been done (au rapport !).

That's all folks !

Just remember : please **always give a name** to your playbooks and tasks, it's very important !
The name you give to the task should a very short description of **What does the task do**.

So let's rename our task (Cf. [playbook2.yml](playbook2.yml)) and relaunch the play.

Congratulations, you are almost an Ansible star !
