# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "centos-6.5"
  config.vm.box_url = "https://dl.dropboxusercontent.com/u/2236361/VMs/centos-6.5.box"
  config.vm.network "forwarded_port", guest: 80, host: 8083
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/site.yml"
  end
end
