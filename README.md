# ansible-workstation

Ansible code to manage personal workstation

## Running on a new machine

Open terminal and run:

```bash
sudo apt update -y
sudo apt install -y ansible
```

Clone the repo locally:

```bash
git clone https://github.com/frezbo/ansible-workstation.git
git submodule update --init --recursive
```

```bash
cd ansible-workstation
ansible-playbook -K deepwater.yml
```

After ansible finishes running plug-in the YubiKey and run:

```bash
gpg --card-status
```

and then run:

```bash
gpg --card-edit
```

In the gpg prompt run:

```bash
fetch
```

Once the key is imported, exit the gpg terminal and then set the following environment variables:

```bash
export PATH="/home/frezbo/.local/share/aquaproj-aqua/bin:${PATH}"
export AQUA_GLOBAL_CONFIG="/home/frezbo/.config/aquaproj-aqua/aqua.yaml"
export AQUA_EXPERIMENTAL_X_SYS_EXEC="true"
export AQUA_LOG_COLOR="always"
export AQUA_PROGRESS_BAR="true"
```

then run:

```bash
chezmoi diff
chezmoi apply
```

Log out and log-in.

> NB: Long term move over to Nix for proper state. Ref: [homelab](https://github.com/danderson/homelab)
