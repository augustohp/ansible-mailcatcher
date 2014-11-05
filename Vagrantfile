# vi: set ft=ruby et ts=4 sw=4:

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
     if Vagrant.has_plugin?("vagrant-cachier")
         config.cache.scope = :box
     end

    # Debian 6 (squeeze)
    config.vm.define "squeeze53", autostart: false do |debian|
        debian.vm.box = "chef/debian-6.0.8"
        debian.vm.network "private_network", ip: "192.168.27.101"
        debian.vm.hostname = "squeeze.debian.local"
        debian.vm.provider :virtualbox do |vb|
            vb.name = "ansible-mailcatcher-squeeze"
        end
        debian.vm.provision "ansible" do |local|
            local.playbook = "tests/defaults.yml"
        end
    end
end
