VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "labvm"
  config.vm.box = "generic/debian12"
  config.vm.hostname = "labvm"
  config.ssh.insert_key = false

  # Virtualbox config
  config.vm.provider "vmware_desktop" do |v|
    v.allowlist_verified = true
    v.gui = false
    v.vmx["memsize"] = "2048"
    v.vmx["numvcpus"] = "2"
  end

  # Network config
  config.vm.network :private_network, ip: "192.168.119.30"

  # Sync Folder config
  config.vm.synced_folder "./../../jenkins-vm/jenkins-config", "/home/vagrant/jenkins-config", owner: "vagrant", group: "vagrant"

  # # Executing a shell script
  config.vm.provision "shell", privileged: true, path: "./../../jenkins-vm/jenkins-config/script.sh"
end

