# -*- mode: ruby -*-
# vi: set ft=ruby :

# Copyright (C) 2016 Nicolas Lamirault <nicolas.lamirault@gmail.com>

# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Require a recent version of vagrant otherwise some have reported errors setting host names on boxes
Vagrant.require_version ">= 1.6.2"

Vagrant.configure(2) do |config|

  config.vm.box = "willy64"
  config.vm.box = "https://cloud-images.ubuntu.com/vagrant/wily/current/wily-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.hostname = "Multichain"
  config.vm.network :private_network, :ip => '10.4.4.4'
  # number_of_nodes.times do |i|
  #   config.vm.define "multichain-node-#{i}" do |node|
  #     node.vm.hostname = "multichain-node-#{i}.#{tld}"
  #     node.vm.network :private_network, :ip => "10.4.4.#{i}"
  #   end
  #   i += 1
  # end

  config.ssh.forward_agent = true
  config.ssh.forward_x11 = true

  config.vm.provider :virtualbox do |vb|
    #vb.gui = true
    vb.customize ["modifyvm", :id, "--memory", "512"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
    vb.name = "CloudDev"
  end

  config.vm.provision "shell", :inline => "wget http://www.multichain.com/download/multichain-1.0-alpha-16.tar.gz"
  config.vm.provision "shell", :inline => "tar -xvzf multichain-1.0-alpha-16.tar.gz"
  config.vm.provision "shell", :inline => "cd multichain-1.0-alpha-16 && mv multichaind multichain-cli multichain-util /usr/local/bin"

end
