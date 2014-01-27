REA site performance pre-interview task
=============


Provision a CentOS 6.5 server with nginx passenger ruby and deploy basic sinatra app from
    git://github.com/tnh/simple-sinatra-app.git

Requires
-------
- Vargrant (1.4.3)
- Ansible (1.4.4)
- git
- CentOS base box https://dl.dropboxusercontent.com/u/2236361/VMs/centos-6.5.box

To get this application working locally
=============

    git clone git://github.com/AlanC-au/ansible-rea
    vagrant up

Example output
-------------

$ vagrant up
The following plugins were installed with a version of Vagrant
that had different versions of underlying components. Because
these component versions were changed (which rarely happens),
the plugins must be uninstalled and reinstalled.

To ensure that all the dependencies are properly updated as well
it is _highly recommended_ to do a `vagrant plugin uninstall`
prior to reinstalling.

This message will not go away until all the plugins below are
either uninstalled or uninstalled then reinstalled.

The plugins below will not be loaded until they're uninstalled
and reinstalled:

vagrant-berkshelf, vagrant-omnibus
Bringing machine 'default' up with 'virtualbox' provider...
[default] Importing base box 'centos-6.5'...
[default] Matching MAC address for NAT networking...
[default] Setting the name of the VM...
[default] Clearing any previously set forwarded ports...
[default] Fixed port collision for 22 => 2222. Now on port 2200.
[default] Clearing any previously set network interfaces...
[default] Preparing network interfaces based on configuration...
[default] Forwarding ports...
[default] -- 22 => 2200 (adapter 1)
[default] -- 80 => 8083 (adapter 1)
[default] Booting VM...
[default] Waiting for machine to boot. This may take a few minutes...
[default] Machine booted and ready!
[default] Mounting shared folders...
[default] -- /vagrant
[default] Running provisioner: ansible...

PLAY [all] ******************************************************************** 

GATHERING FACTS *************************************************************** 
ok: [default]

TASK: [secure | install libselinux-python needed for ansible and selinux] ***** 
changed: [default]

TASK: [secure | enable selinux] *********************************************** 
changed: [default]

TASK: [secure | write iptables] *********************************************** 
changed: [default]

TASK: [secure | chkconfig] **************************************************** 
changed: [default]

TASK: [secure | service start] ************************************************ 
changed: [default]

TASK: [ruby | install RVM] **************************************************** 
changed: [default]

TASK: [ruby | install Ruby 2.1] *********************************************** 
changed: [default]

TASK: [ruby | install passenger] ********************************************** 
changed: [default]

TASK: [ruby | install curl-devel] ********************************************* 
changed: [default]

TASK: [nginx | create source directory] *************************************** 
ok: [default]

TASK: [nginx | download source] *********************************************** 
changed: [default]

TASK: [nginx | untar] ********************************************************* 
changed: [default]

TASK: [nginx | install passenger-nginx] *************************************** 
changed: [default]

TASK: [nginx | write nginx.conf] ********************************************** 
changed: [default]

TASK: [nginx | setup init file] *********************************************** 
changed: [default]

TASK: [nginx | setup vhost directories] *************************************** 
changed: [default] => (item=sites-available)
changed: [default] => (item=sites-enabled)

TASK: [nginx | chkconfig] ***************************************************** 
changed: [default]

TASK: [nginx | service start] ************************************************* 
changed: [default]

TASK: [deploy-user | Add the deploy user] ************************************* 
changed: [default]

TASK: [simple-sinatra-app | setup ngnix virtual host] ************************* 
changed: [default]

TASK: [simple-sinatra-app | enable virtual host] ****************************** 
changed: [default]

TASK: [simple-sinatra-app | create the application directories] *************** 
changed: [default] => (item=/app/simple-sinatra-app)

TASK: [simple-sinatra-app | Check out the latest revision of the code] ******** 
changed: [default]

TASK: [simple-sinatra-app | install the app] ********************************** 
changed: [default]

NOTIFIED: [secure | restart iptables] ***************************************** 
changed: [default]

NOTIFIED: [nginx | restart nginx] ********************************************* 
changed: [default]

PLAY RECAP ******************************************************************** 
default                    : ok=27   changed=25   unreachable=0    failed=0   

$ curl localhost:8083
Hello World!
