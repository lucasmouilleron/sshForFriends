sshForFriends
=============

Temporally grant ssh access to friends.

`sshForFriends` uses friends public keys to give them access to the computer.
When `sshForFriends` has finished running, public keys are cleaned and friends can't access the computer anymore.
Public keys are fetched from known identity providers.

Tested on macOS and Ubuntu.

No password, no hastle, 100% SSH.

![Screenshot](http://grabs.lucasmouilleron.com/Screen%20Shot%202017-05-31%20at%2015.31.02.png)

Usage
-----
- `sshForFriends [OPTIONS] friendUsername`
- `friendUsername` is the friend username which will be granted access (identity provider username)
- `sshForFriends -h` for more usage help

Identify providers
------------------
- Github : keys from `https://github.com/$USER_NAME.keys` (`-g`, `-i github`)
- Keybase : keys from `https://$USER_NAME.keybase.pub/id_rsa.pub` (`-k`, `-i keybase`)

Behind a firewall
-----------------
- If the computer being accessed is behind a firewall, `sshForFriends` can use a public server for ssh forwading.
- See params `-x`, `-l`, `-m` and `-n`
- See examples below

Examples
--------
- Give access from a machine to `lucasmouilleron` in one line : `curl -sL https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -g -x lucasmouilleron.com`
- Give access from a machine behind a firewall to `lucasmouilleron` in one line : `curl -sL https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -g -x lucasmouilleron.com -l sshtunnel -m 10022 lucasmouilleron`

Credits
-------
- Inspired by https://github.com/flplv/ssh-allow-friend