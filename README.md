```
👩  This project is part of the passbolt "lab"!
⚗️   It is used to illustrate an article or as a conversation starter.
🧪  Use at your own risks!
```

## Copyright & License

(c) 2021 Passbolt SA

Passbolt is registered trademark of Passbolt S.A.

MIT No Attribution - https://opensource.org/licenses/MIT-0

## Resources

* [Managing Secrets in Ansible using passbolt](https://blog.passbolt.com/managing-secrets-in-ansible-using-passbolt-87af031ceab6)
* [passbolt ansible collection](https://galaxy.ansible.com/anatomicjc/passbolt)
* [py-passbolt library](https://pypi.org/project/py-passbolt/)

## Ansible / passbolt POC

### Launch the docker-compose stack

```
docker-compose up -d
```

### Run the example playbook

Jump in the ansible container:

```
docker-compose run ansible
```

From the ansible container, launch the example playbook:

```
ansible-playbook playbooks/example-playbook.yml
```

Or in one command without jump inside the ansible container:

```
docker-compose run ansible bash -c "ansible-playbook playbooks/example-playbook.yml"
```

![ansible-passbolt-poc-video](ansible-passbolt-poc.gif)

### Services provided by this docker stack

A passbolt CE instance available on http://localhost:12380/, you can recover an account from:

* ada@passbolt.dev
* betty@passbolt.dev
* carol@passbolt.dev
* admin@passbolt.dev

A local webmail for email recovery is available on http://localhost:12325/ for account recovery links. emails are sent by a cron job every minute.

You will need private OpenPGP keys to recover the accounts, you will find them on [pgp-keys](pgp-keys) folder.

The passphrase is the email, aka ada@passbolt.dev passphrase is ada@passbolt.dev.

### How to encrypt in ansible vault format ?

From the ansible container, to encrypt ada@passbolt.dev passphrase:

```
echo -n ada@passbolt.dev | ansible-vault encrypt
```

To encrypt the private key:

```
cat pgp-keys/ada.asc | ansible-vault encrypt
```
