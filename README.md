Setup

    macOS Monterey, v12.0.1
    processor: ARM M1 (macbook air)
    memory: 16 Gb
 
 Install Nix
 ```console
 1) sh <(curl -L https://nixos.org/nix/install) --no-daemon
 ```
 
 ```console
 2) edit /etc/nix/nix.conf and add following 2 lines
 
     substituters        = https://hydra.iohk.io https://iohk.cachix.org https://cache.nixos.org/
     trusted-public-keys = hydra.iohk.io:f/Ea+s+dFdN+3Y/G+FDgSq+a5NEWhJGzdjvKNGv0/EQ= iohk.cachix.org-1:DpRUyj7h7V830dp/i6Nti+NEO2/nhblbov/8MW7Rqoo= cache.nixos.org-1:6NCHdD59X431o0gWypbMrAURkbJ16ZPMQFGspcDShjY=
 ```
 Close the terminal and start the terminal again. If you dont do this then cache changes above will not be taken and it will unneccesarily build ghc etc.
 
 
 ```console
 2a) git clone https://github.com/input-output-hk/plutus-apps
 2b) git checkout 7f53f18dfc788bf6aa929f47d840efa1247e11fd
 3) nix build -f default.nix docs.site
 4) nix-build -A plutus-playground.server
 5) nix-shell
 6) cd plutus-playground-server 
6a) plutus-playground-server
```

Now open another terminal 
```console
7) nix-shell
8) npm install -g npm
9) cd plutus-playground-client
10) update the webpack.config.js https: true to https: false
11) npm run start
```

Once the build is complete you can open  https://localhost:8009/ and then run the example

Incase you get any dependency issues the install homebrew
```console
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

