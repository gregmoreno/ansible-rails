ssh-keyscan staging.steponehealth.com >> ~/.ssh/known_hosts

Assuming you still need to upload ssh key to the server and you have the root password

```
scp ~/.ssh/id_rsa.pub root@staging.steponehealth.com:~/uploaded_key.pub
ssh root@staging.steponehealth.com
mkdir -m og-rwx .ssh
cat ~/uploaded_key.pub >> ~/.ssh/authorized_keys
```

Create the user. After this, will use deploy user

```
ansible-playbook -i hosts create-user.yml --user root
ansible-playbook -i hosts bootstrap.yml
```

Sources:

* https://github.com/dodecaphonic/ansible-rails-app
* https://github.com/jgrowl/ansible-playbook-ruby-from-src
* https://github.com/bennojoy/mysql
* http://thornelabs.net/2014/03/08/install-ansible-create-your-inventory-file-and-run-an-ansible-playbook-and-some-ansible-commands.html
