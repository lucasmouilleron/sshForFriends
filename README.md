sshForFriends
=============

Temporally grant ssh access to friends.

Identify providers
------------------
- Github : the github username
- Keybase : todo

Examples
--------
- Help : `sshForFriends -h`
- Give access from a machine to `lucasmouilleron` in one line : `curl -L https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends?ck=5 -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -g -x lucasmouilleron.com -l sshtunnel -m 10022 lucasmouilleron`