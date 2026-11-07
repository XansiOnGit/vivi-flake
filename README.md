# vivi-flake

Nix flake for [Vivi](https://github.com/djxnzi/vivi).

## Usage

Add to your `flake.nix`:

```nix
inputs = {
  nixpkgs.url = "github:NixOS/nixpkgs/nixos-unstable";

  vivi-src = {
    url = "github:djxnzi/vivi";
    flake = false;
  };

  vivi = {
    url = "github:XansiOnGit/vivi-flake";
    inputs.nixpkgs.follows = "nixpkgs";
    inputs.vivi-src.follows = "vivi-src";
  };
};
```

Add the overlay:

```nix
nixpkgs.overlays = [ vivi.overlays.default ];
```

Install it:

```nix
environment.systemPackages = [ pkgs.vivi ];
```

## Update it as you will.

```bash
nix flake update
sudo nixos-rebuild switch --flake .#yourhostname
```

## Try without installing

```bash
nix run github:XansiOnGit/vivi-flake
```

## Development and such

```bash
nix develop
```
