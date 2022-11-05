<div align="center"><table><tr><td>
<h1><a href="https://github.com/z-shell/zi">
  <p><img align="center" src="https://github.com/z-shell/zi/raw/main/docs/images/logo.svg" alt="Logo" width="60px" height="60px" /></a>
  ❮ Zi Package - Subversion ❯</p>
</h1>
<h3 align="center">
<table>
    <tr>
        <td><b>Package source:</b></td>
        <td>Source Tarball</td>
        <td>Binary</td>
        <td>Git</td>
        <td>Node</td>
        <td>Gem</td>
    </tr>
    <tr>
        <td><b>Status:</b></td>
        <td>✔️ (default)</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
</table></h3>
<p><img align="center" src="https://user-images.githubusercontent.com/59910950/172344415-306d8484-dc46-4fee-89db-9cfa9c149182.png" alt="zi subversion package" width="100%" height="auto" /></p>
</td></tr></table></div>

## Available `pack''` invocations

```shell
# Download and install the APR dependency of Subversion
zi pack for apr
```

```shell
# Download, build and install the latest Subversion source tarball
zi pack for subversion
```

## Default Profile

Provides the Subversion revision control system by compiling and installing it to the `$ZPFX` directory (`~/.zi/polaris` by default).
It uses the [z-shell/z-a-readurl](https://github.com/z-shell/z-a-readurl) annex to download the latest Subversion tarball.

The Zi command executed will be equivalent to:

```shell
zi as"null|monitor" dlink"https://.*/subversion-%VERSION%.tar.bz2" \
  atclone'zpextract --move --auto; print -P \\n%F{75}Building Subversion...\\n%f; ./configure \
    --prefix="$ZPFX" --with-apr='$ZPFX' >/dev/null && make >/dev/null && print -P \
    \\n%F{75}Installing Subversion to $ZPFX...\\n%f && make install >/dev/null && print -P \
    \\n%F{34}Installation of Subversion succeeded.%f || \
    print -P \\n%F{160}Installation of Subversion failed.%f' \
  atpull'%atclone' for \
    https://subversion.apache.org/download.cgi
```

---

> This repository compatible with [Zi](https://github.com/z-shell/zi)

The [apache/subversion](https://github.com/apache/subversion) zsh package that uses the [zsh-string-lib](https://github.com/z-shell/zsh-string-lib) to automatically:

- get the plugin's Git repository OR release-package URL,
- get the list of the recommended ices for the plugin,
  - there can be multiple lists of ices,
  - the ice lists are stored in _profiles_; there's at least one profile, _default_,
  - the ices can be selectively overridden.
