# Based from https://github.com/dodecaphonic/ansible-rails-app

# A small Rails server playbook for Ansible
It installs:

- Ruby 2.1
- mysql (or postgresql)
- nginx
- Puma (jungle)

1. Change the app name and deploy directory in <code>vars/defaults.yml</code>.
2. Rename `hosts.example` to `hosts` and change it to your hosts.

To run:

    $ ansible-playbook -i hosts app.yml --private-key ~/.ssh/soh-www

    $ ansible-playbook -i hosts app.yml -t ruby,deploy,postgresql,nginx
    $ <deploy your app>
    $ ansible-playbook -i hosts ruby-webapp.yml -t puma

There is an example Capistrano `deploy.rb` in this repository that you can use too.

