VAGRANTFILE_API_VERSION = "2"

proxy = ENV['http_proxy'] || ""

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "atlassian"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 4096
    vb.cpus = 4
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.extra_vars = {
      proxy_env: {
        http_proxy: proxy
      }
    }
  end
  config.vm.network "forwarded_port", guest: 1990, host: 1990,
    auto_correct: true
  config.vm.synced_folder "~", "/host"

end
