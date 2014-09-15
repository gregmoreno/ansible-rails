

Using ec2, create a group with Power role and add user to that group. Note ec2.yml will update hosts
```
AWS_ACCESS_KEY=access AWS_SECRET_KEY="secret" ansible-playbook -i hosts ec2.yml
ansible-playbook -i hosts create-user.yml --user root --limit launched
ansible-playbook -i hosts bootstrap.yml --limit launched
```

If you are not using ec2, make sure you have access to server first.
Assuming you still need to upload ssh key to the server and you have the root password
```
scp ~/.ssh/id_rsa.pub root@app.com:~/uploaded_key.pub
ssh root@staging.app.com
mkdir -m og-rwx .ssh
cat ~/uploaded_key.pub >> ~/.ssh/authorized_keys
```

Update hosts file to change the domain or IP under www
```
ansible-playbook -i hosts create-user.yml --user root --limit www
ansible-playbook -i hosts bootstrap.yml --limit www
```


Sources:
* http://tomoconnor.eu/blogish/part-3-ansible-and-amazon-web-services/#.U_ffpbxdXA4
* https://github.com/dodecaphonic/ansible-rails-app
* https://github.com/jgrowl/ansible-playbook-ruby-from-src
* https://github.com/bennojoy/mysql
* http://thornelabs.net/2014/03/08/install-ansible-create-your-inventory-file-and-run-an-ansible-playbook-and-some-ansible-commands.html
* https://github.com/radamanthus/ansible-rails
