# Manual compose steps

```
mkdir shared data config
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

## Life conf logs
```
docker compose logs -f ubuntu
```

```
docker compose logs ubuntu
```

## Start over
docker compose down
docker rmi ubuntu:latest

rm -rf shared data config
mkdir shared data config
