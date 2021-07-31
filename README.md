# Self Host forem

You need fedora core os for self hosting forem(software on which dev.to is built) what to do on other OS distributions.

You can install vagrant from this [link](https://www.vagrantup.com/downloads)

Put the vagrant file in the folder. In this folder we will setup everything we want to setup for self hosting forem.

Run

```bash
vagrant up

```

Edit the selfhost/inventory/forem/setup.yml file. Add forem domain name, default_email, forem_subdomain_name vault secret keys as given in the 6th point of  [forem selfhost repo](https://github.com/forem/selfhost#quick-start)

Now run 
```bash
vagrant ssh

cd /vagrant

#  Generate a SSH key using the following command named and save it to ${HOME}/.ssh/forem.

ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

# generate one more normal key name id_rsa

ssh-keygen -t rsa -b 4096 -C "your_email@example.com"


```

Use ls -lh ~/.ssh/forem* to ensure you have both a ${HOME}/.ssh/forem private key, and a corresponding ${HOME}/.ssh/forem.pub public key.

Follow the forth and fith steps in forem selfhost setup repo [link](https://github.com/forem/selfhost#setup)

Now run ansible-playbook -i inventory/forem/setup.yml playbooks/providers/aws.yml

That is it this will deploy your forem to AWS cloud



