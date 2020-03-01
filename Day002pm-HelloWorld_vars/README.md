# Ansible Trip - Day 2 pm - Hello World (vars)

We usually use `vars` to parametrize our tasks.

In [playbook1.yml](playbook1.yml#L7-L8) we define a var named `ia_name` that stores the name of our program.
We use it in the [debug msg](playbook1.yml#L19) to answer the user input.

Let's launch it using Ansible :

```
Day002pm-HelloWorld_vars $ ansible-playbook playbook1.yml
```
```
...
TASK [Say Hello] ****************************************************************************************************
ok: [localhost] => {
    "msg": "Nice to meet you Tonton, my name is HAL 9000."
}
PLAY RECAP **********************************************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

> Tip : Any variable can be printout using {{ }} syntax.

Many var already exist in the execution context of a Task. You can debug all vars using this simple task in [playbook2.yml](playbook2.yml#L12-L14)

The debug msg task in [playbook2.yml](playbook2.yml#L16-L18) use a combination of a playbook var and a context var to printout a debug msg.

> Ansible doc for further : https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html

## Gather facts

We can collect a lot of information about the host where a playbook is played by [activating fact gathering](playbook3.yml#L5).

> Tip : Activate gather_facts when you need to learn some information about the host.

If you execute the [playbook3.yml](playbook3.yml), you can see that a lot of information is now available in `vars`.

The [debug task](playbook3.yml#L18) is now able to know who is launching the playbook by reading the environment variable `USER`.

```
Day002pm-HelloWorld_Parametrized $ ansible-playbook playbook3.yml
```
```
PLAY [My fist playbook] *********************************************************************************************************************
TASK [Gathering Facts] *********************************************************************************************************************
ok: [localhost]

TASK [Display all vars] *********************************************************************************************************************
ok: [localhost] => {
    "vars": {
        ... Not reproduced here for better lisibility ...
    }
}

TASK [Say Hello] *********************************************************************************************************************
ok: [localhost] => {
    "msg": "Nice to meet you xdegenne, my name is HAL 9000@localhost !"
}

PLAY RECAP **********************************************************************************************************
localhost                  : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

Please not that we have written 2 tasks in our playbook but 3 were executed (ok=3). Why ? The [Gater fact module](https://docs.ansible.com/ansible/latest/modules/gather_facts_module.html) adds a task named `Gathering Facts` to our playbook.

> Tip : Activate gather_facts only when you really need informations about remote host. If your playbook don't need such information, set gather_facts to no and your playbook execution will be faster !
