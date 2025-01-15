## Easy setup
```
docker compose up -d
```

## Clone Registry
You can pull container from here:
```
docker pull ghcr.io/h3cth0r/ubuntu-nix:latest
```

## Start over
```
docker compose down
docker rmi ubuntu:latest

rm -rf shared data config home
mkdir shared data config home

mkdir shared data config
```

## Procedure to replicate manually
```
mkdir shared data config home
```
Setup docker container
```
docker compose up -d
docker compose exec ubuntu bash
```

Install nixos on ubuntu
```
sudo apt update
sudo apt install curl
sudo apt install xz-utils
sudo apt install nano
sudo apt install neovim 


sh <(curl -L https://nixos.org/nix/install) --daemon --yes
```

Restart to complete installation
```
docker compose restart ubuntu
```

Install home manager
```
nix-channel --add https://github.com/nix-community/home-manager/archive/master.tar.gz home-manager
nix-channel --update

nix-shell '<home-manager>' -A install
```

## Live conf logs
```
docker compose logs -f ubuntu
```

```
docker compose logs ubuntu
```

```
home-manager location
/root/.config/home-manager/home.nix
```

Create and public image
```
docker commit my-ubuntu ubuntu-nix
# Create read and delete packages token
docker login --username <github username> --password <github_token> ghcr.io
docker push ghcr.io/h3cth0r/ubuntu-nix:latest
```
