# UserAccess
To allow if a new user can ssh to remote servers by giving access to sshd_config file.

Here, we need to build with parameters in Jenkins where we need to specify the user that we need to add to ssh so that it can be authenticated using ssh_config file.
First parameter we need to mention is the username and second parameter is to choose if we want to grant him the access or revoke the access to ssh into multiple remote servers, which are listed in serverlist.txt file.

Another method can be using command ssh-copy-id user@<server-name> between multiple servers for the specific user and thus authenticating the user using ssh public key thus removing the need for password on next ssh for the user between the trusted servers. This command make the required changes in authorized_keys file under .ssh
