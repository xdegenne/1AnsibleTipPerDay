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
ansible-playbook -i localhost, playbook1.yml
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

> Advanced Tip : You can see in [playbook2.yml](playbook2.yml) that we have conditioned the machine behavior regarding user input.  

Mostly, we use variables to setup some inputs in our playbooks.

Let's see how this [afternoon](https://github.com/xdegenne/1AnsibleTipPerDay/tree/master/Day002pm-HelloWorld_Parametrized)
