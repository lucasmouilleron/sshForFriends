sshForFriends
=============

Temporally grant ssh access to friends.

Identify providers
------------------
- Github : the github username
- Keybase : todo

Behind a firewall
-----------------
- If the computer being accessed is behind a firewall, `sshForFriends` can use a public server for ssh forwading.
- See params `-x`, `-l`, `-m` and `-n`
- See examples below

Examples
--------
- Help : `sshForFriends -h`
- Give access from a machine to `lucasmouilleron` in one line : `curl -sL https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends?ck=6 -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -g -x lucasmouilleron.com`
- Give access from a machine behind a firewall to `lucasmouilleron` in one line : `curl -sL https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -g -x lucasmouilleron.com -l sshtunnel -m 10022 lucasmouilleron`