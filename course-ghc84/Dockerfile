FROM sydneyhaskell/nix

#RUN nix-channel --add https://nixos.org/channels/nixpkgs-unstable nixpkgs
RUN nix-channel --update

# base image
RUN nix-env -iA \
    nixpkgs.curl \
    nixpkgs.emacs \
    nixpkgs.git \
    nixpkgs.vim \
    nixpkgs.tmux \
    nixpkgs.wget 

# trust/use these 3rd party caches
RUN nix-env -iA cachix -f https://github.com/NixOS/nixpkgs/tarball/889c72032f8595fcd7542c6032c208f6b8033db6
RUN cachix -v use hie-nix

# haskell ide engine
RUN nix-env -iA hie84 -f https://github.com/domenkozar/hie-nix/tarball/a7ef4c4ceef1dbf46aabff68a4b9bd86d41d0886

# haskell
RUN nix-env -iA \
   nixpkgs.haskell.compiler.ghc844 \
   nixpkgs.haskellPackages.ghcid \
   nixpkgs.haskellPackages.hasktags \
   nixpkgs.haskellPackages.hlint \
   nixpkgs.haskellPackages.hoogle \
   nixpkgs.haskellPackages.pointfree \
   nixpkgs.haskellPackages.pointful
