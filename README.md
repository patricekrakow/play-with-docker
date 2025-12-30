# Let's Play with Docker

As usual, let's go to <https://killercoda.com/playgrounds/scenario/ubuntu> to get an Ubuntu machine (for 60 minutes).

## Prompt Customization

That's just a question of taste, but I like to cutomize my prompt first.

You can edit the `.bashrc` file:

```text
vi .bashrc
```

and add the following lines at the end:

```bash
# Added by PK
export PS1="\[\e[32m\]\h\[\e[m\]:\w\\$ "
```

Then,  you can execute the command to see the result in all terminal connections:

```text
source .bashrc
```

## Installation

## Reference

- https://docs.docker.com/engine/install/ubuntu/

- https://docs.docker.com/get-started/introduction/develop-with-containers/
