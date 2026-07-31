> [!IMPORTANT]
> **This project is no longer maintained and the repository is archived.**
>
> It never left the experimental stage, and it has not been updated in years:
> `go.mod` targets Go 1.17 and pins IPFS libraries from 2019. Expect to fix
> things before it builds and runs.
>
> Two known potholes, both reported and never fixed. The `go get` install step
> below stopped working when [Go 1.18 removed package installation from
> `go get`](https://go.dev/doc/go1.18#go-get); use `go install <pkg>@latest`
> instead. And there are open reports of segfaults on some Linux distributions.
>
> The idea still holds up: Kubo continues to ship the
> [git IPLD codec](https://github.com/ipfs/kubo/tree/master/plugin/plugins/git),
> so a working helper is possible. It just needs someone to do the work. There
> are 30-odd forks, and forking is a fine answer.
>
> The repository can be unarchived, but only for a named maintainer who commits
> to keeping it up. If that is you, reach out to the
> [IPFS Foundation](https://ipfsfoundation.org/about/).

# Git IPLD remote helper

Push and fetch commits using IPFS!

This helper is experimental as of now

## Usage
```
Clone an example repository:
$ git clone ipld://2347e110c29742a1783134ef45f5bff58b29e40e

Pull a commit:
$ git pull ipld://2347e110c29742a1783134ef45f5bff58b29e40e

Push:
$ git push --set-upstream ipld:// master
```

Note: Some features like remote tracking are still missing, though the plugin is
quite usable. IPNS helper is WIP and doesn't yet do what it should

## Installation
1. `go get github.com/ipfs-shipyard/git-remote-ipld`
2. `make install`
3. Done
4. Make sure you run go-ipfs 0.4.17 or newer as you need git support

## Limitations / TODOs
* ipns remote is not implemented fully yet

# Troubleshooting
* `fetch: manifest has unsupported version: 2 (we support 3)` on any command
  - This usually means that tracker data format has changed
  - Simply do `rm -rf .git/ipld`

## Contribute

This repository is archived and is not accepting contributions. Drive-by patches
will not reopen it. Unarchiving requires someone willing to be named as
maintainer. If that is you, contact the
[IPFS Foundation](https://ipfsfoundation.org/about/). Forking is fine too.

## License
MIT
