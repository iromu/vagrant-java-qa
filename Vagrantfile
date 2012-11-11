# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "precise32"

  config.vm.host_name = "java-qa-vm"

  config.vm.customize ["modifyvm", :id, "--memory", 256]

  config.vm.network :hostonly, "10.12.122.122", :netmask => "255.255.0.0"

  config.vm.provision :chef_solo do |chef|

    chef.cookbooks_path = ["cookbooks"]

    chef.json.merge!({
                         :build_essential => {
                             :compiletime => true
                         },
                         :nginx => {
                             :install_method => "source"
                         },
                         :java => {
                             :install_flavor => "oracle",
                             :oracle => {
                                 "accept_oracle_download_terms" => true
                             }
                         },
                         :sonar => {
                             :web_domain => "sonar.java-qa.vm"
                         },
                         :jenkins => {
                             :http_proxy => {
                                 :variant => "nginx",
                                 :host_name => "jenkins.java-qa.vm"
                             }
                         }
                     })

    chef.add_recipe "apt"
    chef.add_recipe "build-essential"
    chef.add_recipe "nginx"
    chef.add_recipe "sonar"
    chef.add_recipe "sonar::proxy_nginx"
    chef.add_recipe "jenkins"
  end

end
