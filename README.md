# kubectl-aliases (read-only)

This repository contains [a script](generate_aliases.py) to generate hundreds of
**read-only** convenient shell aliases for kubectl, so you no longer need to spell out every single
command and --flag over and over again.

An example shell alias created from command/flags permutation looks like:

    alias ksysgdepwslowidel='kubectl --namespace=kube-system get deployment --watch --show-labels -o=wide -l'

Confused? Read on.

### Examples

Some of the 800 generated aliases are:

```sh
alias k='kubectl'
alias kg='kubectl get'
alias kgpo='kubectl get pod'

alias ksysgpo='kubectl --namespace=kube-system get pod'


alias kgsvcoyaml='kubectl get service -o=yaml'
alias kgsvcwn='watch kubectl get service --namespace'
alias kgsvcslwn='watch kubectl get service --show-labels --namespace'

alias kgwf='watch kubectl get -f'
...
```

See [the full list](.kubectl_aliases).

### Installation

You can directly download the [`.kubectl_aliases` file](https://github.com/arriqaaq/kubectl-aliases/blob/master/.kubectl_aliases)
and save it in your $HOME directory, then edit your .bashrc/.zshrc file with:

```sh
[ -f ~/.kubectl_aliases ] && source ~/.kubectl_aliases
```

> **Recommendation:** If you want to use GNU `watch`  command instead of
> `kubectl [...] --watch`, run it like this:
>
>     [ -f ~/.kubectl_aliases ] && source \
>        <(cat ~/.kubectl_aliases | sed -r 's/(kubectl.*) --watch/watch \1/g')

**Print the full command before running it:** Add this to your `.bashrc` or
`.zshrc` file:

```sh
function kubectl() { echo "+ kubectl $@">&2; command kubectl $@; }
```

### Syntax explanation

* **`k`**=`kubectl`
  * **`sys`**=`--namespace kube-system`
* commands:
  * **`g`**=`get`
  * **`d`**=`describe`
  * **`k`**:`kustomize`
  * **`ex`**: `exec -i -t`
  * **`lo`**: `logs -f`
* resources:
  * **`po`**=pod, **`dep`**=`deployment`, **`ing`**=`ingress`,
    **`svc`**=`service`, **`cm`**=`configmap`, **`sec`=`secret`**,
    **`ns`**=`namespace`, **`no`**=`node`
* flags:
  * output format: **`oyaml`**, **`ojson`**, **`owide`**
  * **`all`**: `--all` or `--all-namespaces` depending on the command
  * **`sl`**: `--show-labels`
  * **`w`**=`-w/--watch`
* value flags (should be at the end):
  * **`n`**=`-n/--namespace`
  * **`f`**=`-f/--filename`
  * **`l`**=`-l/--selector`
  

### Authors

- [@ahmetb](https://twitter.com/ahmetb)
- [@arriqaaq](https://github.com/arriqaaq)
-----
