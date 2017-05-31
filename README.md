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
- Give access from a machine to `lucasmouilleron` in one line : `curl -L https://raw.githubusercontent.com/lucasmouilleron/sshForFriends/master/sshForFriends -o $HOME/sshForFriends ; chmod a+x $HOME/sshForFriends ; $HOME/sshForFriends -g -i lucasmouilleron`

ssh -fN -R 10022:localhost:22 sshtunnel@lucasmouilleron.com
ssh testlucas@54.217.248.101
ssh testlucas@lucasmouilleron.com -p 10022