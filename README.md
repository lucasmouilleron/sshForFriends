sshForFriends
=============

Temporally give ssh access to your friends.

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

Identity providers
------------------
- id_rsa: key from `cat $HOME/.ssh/id_rsa.pub` on your friend's machine (`-r RSA_PUB_KEY`)
- Github : keys from `https://github.com/$USER_NAME.keys` (`-g`, `-i github`)
- Keybase : keys from `https://$USER_NAME.keybase.pub/id_rsa.pub` (`-k`, `-i keybase`)

Behind a firewall
-----------------
- If the computer being accessed is behind a firewall, `sshForFriends` can use a public server for ssh forwading.
- See params `-x`, `-l`, `-m` and `-n`
- On the public server, make sure `GatewayPorts yes` is set in the `/etc/ssh/sshd_config` file
- See examples below

Miscs
-----
- macOS, enable ssh server : `sudo systemsetup -setremotelogin on`

Examples
--------
- Give access from a machine to `lucasmouilleron` in one line : `curl -sL https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -g lucasmouilleron`
- Give access from a machine to `lucasmouilleron` in one line : `curl -sL https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -k lucasmouilleron`
- Give access from a machine behind a firewall to `lucasmouilleron` in one line : `curl -sL https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -g -x lucasmouilleron.com -l sshtunnel -m 10022 lucasmouilleron`
- Give access from a machine behind a firewall to a friend with pub key in one line : `curl -sL https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -r "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDqN4/IlNfY8I5AUYYnj9mieJ9Uyx4rMbZjxyukmwM1nqSpTmFBs5xdqtE1Qi1DDb6V0Nphua80GUxXfIiKmbJVuOnrBjX2qInwMPtFxJ0gr8adXYIamcCVylcCPm2qO418KQpuHNM1es5s0a2hzuuRCtw6trysq/SCSIp6o05OEdHP8CbfCdFA+P7sy99XHG3yGzqHdU0D04ScDePzm1buSOXqQRCrSkuLmRMBhtRQSj7UAI3IlRcF3tEFPqAywjwnZVIvv6fUoXnpJuoCzBPuJv5D5lo06xixwIvHc39t1r4Tv/OrD+EyWfPsmCpLGfEkMRBqmj/ds5c4y6NjO9cl" -x lucasmouilleron.com -l sshtunnel -m 10022 yourfriendname`

Credits
-------
- Inspired by https://github.com/flplv/ssh-allow-friend