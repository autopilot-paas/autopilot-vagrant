
conf = {
    'box_name' => 'precise',
    'box_url' => 'http://files.vagrantup.com/precise64.box',
    'allocate_memory' => 1024,
    'num_cpus' => 1
}

Vagrant.configure("2") do |config|

  config.vm.box = conf['box_name']
  config.vm.box_url = conf['box_url']


  config.vm.provider "virtualbox" do |v|
   memory = conf['allocate_memory'].to_s()
   v.customize ["modifyvm", :id, "--memory", memory]
  
   n_cpus = conf['num_cpus'].to_s()
   v.customize ["modifyvm", :id, "--cpus", n_cpus]
  end

  config.vm.define "master" do |master|
    master.vm.hostname = "salt-master"
    master.vm.network "private_network", ip: "10.0.10.1"
  end

  config.vm.define "minion1" do |minion1|
    minion1.vm.hostname = "salt-minion1"
    minion1.vm.network "private_network", ip: "10.0.10.2"
  end

end
