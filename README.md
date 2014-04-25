# Barry's ssh key

## Local system

### Installation

    curl -L https://raw.githubusercontent.com/steakknife/ssh_keys/master/id_rsa_steakknife.pub >> ~/.ssh/authorized_keys

### Removal

    sed -i '' '/barry\.allard/d' ~/.ssh/authorized_keys

## Remote box  
    
### Installation (on remote box)

    ssh user@box.domain "curl -L https://raw.githubusercontent.com/steakknife/ssh_keys/master/id_rsa_steakknife.pub >> ~/.ssh/authorized_keys"

### Removal (from remote box)

    ssh user@box.domain "sed -i '' '/barry\.allard/d' ~/.ssh/authorized_keys"

## Removal notes

Be sure to also:

 - expire the associated user account
 - disable the password
 - kill all process with a negative pid to kill the process tree completely `kill -9 $(pgrep -u <username> | sed 's/^/-/')`
 - cleanup (`rm -rf`) / give (`mv + chown`) homedir to someone
 - after all files and processes are expunged, reap the user account too
