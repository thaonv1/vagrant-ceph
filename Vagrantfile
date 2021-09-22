# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'
BOX_IMAGE_CENTOS7 = "centos/7"
BOX_IMAGE_UBUNTU20= "generic/ubuntu2004"

Vagrant.configure(2) do |config|

  config.vm.provision "shell", path: "bootstrap_ubuntu20.sh"
  config.ssh.insert_key = false

  # VM master 
  config.vm.define "ceph1" do |ceph1|
    ceph1.vm.provider "libvirt" do |v|
      v.memory = 4096
      v.cpus = 4
      v.storage_pool_name = 'kvm2' # Cau hinh noi luu VM. Su dung lenh "virsh pool-list"  de lay ten cua pool.			
      # v.graphics_ip = '0.0.0.0'
    end
    ceph1.vm.box = BOX_IMAGE_UBUNTU20
    ceph1.vm.box_check_update  = false
    ceph1.vm.hostname = "ceph1"
    ceph1.vm.network :private_network, ip: "172.16.16.201"
	ceph1.vm.network "public_network", :dev => "vlan2342", :mode => 'bridge', :type => "bridge", :ip => "172.16.71.201"
    ceph1.vm.provision "shell", path: "bootstrap_ubuntu20.sh"
  end

  # VM ceph2
  config.vm.define "ceph2" do |ceph2|
    ceph2.vm.provider "libvirt" do |v|
      v.memory = 2048
      v.cpus = 2
      v.storage :file, :size => '20G' #them o cung thu 2
      v.storage_pool_name = 'kvm2' # Cau hinh noi luu VM. Su dung lenh "virsh pool-list"  de lay ten cua pool.
      # v.graphics_ip = '0.0.0.0'
    end
    ceph2.vm.box = BOX_IMAGE_UBUNTU20
    ceph2.vm.box_check_update  = false
    ceph2.vm.hostname = "ceph2"
    ceph2.vm.network :private_network, ip: "172.16.16.202"
	ceph2.vm.network "public_network", :dev => "vlan2342", :mode => 'bridge', :type => "bridge", :ip => "172.16.71.202"
    ceph2.vm.provision "shell", path: "bootstrap_ubuntu20.sh"
  end

  # VM ceph3
  config.vm.define "ceph3" do |ceph3|
    ceph3.vm.provider "libvirt" do |v|
      v.memory = 2048
      v.cpus = 2
      v.storage_pool_name = 'kvm2' # Cau hinh noi luu VM. Su dung lenh "virsh pool-list"  de lay ten cua pool.
      # v.graphics_ip = '0.0.0.0'
    end
    ceph3.vm.box = BOX_IMAGE_UBUNTU20
    ceph3.vm.box_check_update  = false
    ceph3.vm.hostname = "ceph3"
    ceph3.vm.network :private_network, ip: "172.16.16.203"
	ceph3.vm.network "public_network", :dev => "vlan2342", :mode => 'bridge', :type => "bridge", :ip => "172.16.71.203"
    ceph3.vm.provision "shell", path: "bootstrap_ubuntu20.sh"
   
  end

end
