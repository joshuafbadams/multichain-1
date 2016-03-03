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

number_of_nodes = ENV['MULTICHAIN_NODES'].to_i
if number_of_nodes < 1
  number_of_nodes = 2
end

Vagrant.configure(2) do |config|

  config.vm.box = "willy64"
  config.vm.box = "https://cloud-images.ubuntu.com/vagrant/wily/current/wily-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.hostname = "Multichain"
  number_of_nodes.times do |i|
    config.vm.define "multichain-node-#{i}" do |node|
      node.vm.hostname = "multichain-node-#{i}"
      node.vm.network :private_network, :ip => "10.9.9.1#{i}"
    end
    i += 1
  end

  config.ssh.forward_agent = true
  config.ssh.forward_x11 = true

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "512"]
    vb.customize ["modifyvm", :id, "--cpus", 1]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/multichain.yml"
    ansible.verbose = "v"
    number_of_nodes.times do |i|
      config.vm.define "multichain-node-#{i}" do |node|
        node.vm.hostname = "multichain-node-#{i}"
      end
      i += 1
    end
    multichain_nodes = Array.new
    number_of_nodes.times do |i|
      multichain_nodes.push("multichain-node-#{i}")
    end
    ansible.groups = {'multichain_nodes' => multichain_nodes}
  end

end
