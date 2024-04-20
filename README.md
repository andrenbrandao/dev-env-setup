# ThePrimeagen's Developer Productivity Course

These are my configurations and experiments done while taking the course at [Frontend Masters](https://frontendmasters.com/courses/developer-productivity/).

Some of the tips will be implemented in my [Dotfiles Repo](https://github.com/andrenbrandao/dotfiles).

Topics I have found to be most impactful:

- Ansible: automating your personal environment installation in a new machine
- GNU Stow: dotfile management with symlinks
- Tmux: a terminal multiplexer. I have an [article](https://andrebrandao.me/articles/terminal-setup-with-zsh-tmux-dracula-theme/#tmux--dracula-theme) on how I configure mine.
- Fzf: a fuzzy finder

The remaining of the topics were also pretty cool.

## How to do these automation experiments with Docker and Ansible

The point of using docker containers is that we can play with new instances of Ubuntu and check if the ansible scripts are working properly, simulating the situation of getting a new machine.

### Building

To build the docker images used in this project, run `build-dockers.sh`. It will create two clean images:

- `new-computer`: a clean ubuntu installation
- `nvim-computer`: ubuntu with neovim installed

The first one is the base where we can simulate a new machine, while the second is the one used for development of the automation, hence the neovim installation to change the files.

### Running it

After building the images, execute:

```bash
docker run -v .:/usr/local/bin --rm --it nvim-computer bash
```

It will spin up a new docker container. One can now test if all the programs/apps were installed correctly.

To run the ansible command and install all the packages, execute:

```bash
ansible-playbook local.yml
```
