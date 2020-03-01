# Ansible Trip - Day 2 am - Hello World (prompted)

We would like to add some variable to our fantastic Hello playbook.

We can ask the user for something by adding a task like this :

```
- name: Ask the enduser it's name
  pause:
    prompt: "What's your name ?"
  register: prompt_result

- name: Say Hello
  debug:
    msg: "Hello {{ prompt_result.user_input }} !"
```

Let's launch it using Ansible :

```
Day002am-HelloWorld_Prompt $ ansible-playbook playbook1.yml

PLAY [My fist playbook] *********************************************************************************************

TASK [Ask the enduser it's name] ************************************************************************************
[Ask the enduser it's name]
What's your name ?:
ok: [localhost]

TASK [Say Hello] ****************************************************************************************************
ok: [localhost] => {
    "msg": "Hello Tonton !"
}

PLAY RECAP **********************************************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

The playbook will now ask your name and echo it. Amazing isn't it ?

What has happened ?
* Ansible ask your name and store your input in a var named `prompt_result`.
* The `debug` task now use the `user_input` property of the variable `prompt_result` (so `prompt_result.user_input`).

> Tip : Variable are actually JSON objects and they often contain a lot of information about the context.
To display what's in something, just use the task debug with the var argument.

To see the content of a JSON object, just debug it :

```
- name: Here is the prompt_result
  debug:
    var: prompt_result
```

For example, in `"stdout": "Paused for 3.01 minutes"` we know the time the enduser took to answer.

I use such kind of prompt when the playbook is about to delete some important resources on a platform (even it's a kind of paradox to ask some user inputs in automatization scripts !)

> Advanced Tip : You can see in [playbook2.yml](playbook2.yml#L20) that we have conditioned the machine behavior regarding user input. When you add a condition using `when` on a Task, it's execution will be conditioned to the boolean expression result. Any Task can be conditionned.

Mostly, we use variables to setup some inputs in our playbooks.

Let's see how this [afternoon](../Day002pm-HelloWorld_vars)
