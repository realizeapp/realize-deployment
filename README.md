Realize Deployment
---------------------------------------

This will let you quickly deploy [Realize](http://www.realize.pe) to a remote server and get up and running.

Quickstart
----------------------------------------

1. See `secrets/users/users.yml.template`.  Edit this how to see fit and rename to `users.yml`.
2. The public keys that you specified in the file above should go in `secrets/keys/*.key`.
3. Edit `secrets/vars/realize_prod_vars.yml.template` and rename to `realize_prod_vars.yml`.
    * We recommend using postgresql, but you can switch the DB string to `sqlite:///realize.db` if you want to simplify things.
    * You should put all the Oauth accounts you want to use under `OAUTH_SECRETS`.
    * The `SECRET_KEY` and `SECURITY_SALT_PASSWORD` should be long, random strings.
    * If you use postgresql, make sure to replace the `database_user` and `database_password` values in the `DB_URL`.
4. [Optional] Spin up a server on Amazon AWS using `cloudformation/realize.json`.
    * If you skip this, you can use an existing server, but you will have to edit `playbooks/realize_prod.yml` (or make your own playbook) that matches your server.
    * In the AWS console, feel free to modify the variables how you want, but ensure that you enter a valid SSH key.
5. Install python requirements `pip install requirements.txt` **Don't use a virtualenv for this, as ansible doesn't play nice with them!**.
6. Go to the ansible playbooks directory (`cd playbooks`) and run `ansible-playbook -vvvv --user=ubuntu realize_prod.yml -i ./ec2.py  -c ssh` to configure your server.

Contributions
--------------------------------------------

Contributions are very welcome.  If you want to contribute, please fork and make a pull request.  We will review as soon as we can.

Communication
--------------------------------------------

You can find us at #realize on freenode IRC.  You can also email us at <hello@realize.pe>.