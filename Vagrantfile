# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

  vmbox = "precise64"
  vmboxurl = "http://files.vagrantup.com/precise64.box"  
  gluster_repo = "http://download.gluster.org/pub/gluster/glusterfs/LATEST/Ubuntu/12.04/glusterfs_3.3.0-1_amd64.deb"
  gluster_file = "glusterfs_3.3.0-1_amd64.deb"

  config.vm.define :gluster1 do |gluster1|
    gluster1.vm.box = vmbox
    gluster1.vm.box_url = vmboxurl
    gluster1.vm.host_name = "gluster1"
    gluster1.vm.network :hostonly, "192.168.33.10"
    gluster1.vm.provision :shell, :inline => "sudo apt-get update -y"
    gluster1.vm.provision :shell, :inline => "sudo apt-get install -y python-software-properties"
    gluster1.vm.provision :shell, :inline => "sudo add-apt-repository -y ppa:gluster/glusterfs-3.5"
    gluster1.vm.provision :shell, :inline => "sudo apt-get update -y"
    gluster1.vm.provision :shell, :inline => "sudo apt-get install -y glusterfs-server"
#    gluster1.vm.provision :shell, :inline => "sudo service glusterfs-server start"
    gluster1.vm.provision :shell, :inline => "sudo mkdir -p /srv/brick{1,2,3,4} /mnt/point{1,2}"
    gluster1.vm.provision :shell, :inline => "echo sudo mount -t glusterfs 127.0.0.1:/gv1 /mnt/point1 >> .bashrc"
    gluster1.vm.provision :shell, :inline => "echo sudo mount -t glusterfs 127.0.0.1:/gv2 /mnt/point2 >> .bashrc"
  end

  config.vm.define :gluster2 do |gluster2|
    gluster2.vm.box = vmbox
    gluster2.vm.box_url = vmboxurl
    gluster2.vm.host_name = "gluster2"
    gluster2.vm.network :hostonly, "192.168.33.11"
    gluster2.vm.provision :shell, :inline => "sudo apt-get update -y"
    gluster2.vm.provision :shell, :inline => "sudo apt-get install -y python-software-properties"
    gluster2.vm.provision :shell, :inline => "sudo add-apt-repository -y ppa:gluster/glusterfs-3.5"
    gluster2.vm.provision :shell, :inline => "sudo apt-get update -y"
    gluster2.vm.provision :shell, :inline => "sudo apt-get install -y glusterfs-server"
#    gluster2.vm.provision :shell, :inline => "sudo service glusterfs-server start"
    gluster2.vm.provision :shell, :inline => "sudo mkdir -p /srv/brick{1,2,3,4} /mnt/point{1,2}"
    gluster2.vm.provision :shell, :inline => "echo sudo mount -t glusterfs 127.0.0.1:/gv1 /mnt/point1 >> .bashrc"
    gluster2.vm.provision :shell, :inline => "echo sudo mount -t glusterfs 127.0.0.1:/gv2 /mnt/point2 >> .bashrc"
  end

  config.vm.define :gluster3 do |gluster3|
    gluster3.vm.box = vmbox
    gluster3.vm.box_url = vmboxurl
    gluster3.vm.host_name = "gluster3"
    gluster3.vm.network :hostonly, "192.168.33.12"
    gluster3.vm.provision :shell, :inline => "sudo apt-get update -y"
    gluster3.vm.provision :shell, :inline => "sudo apt-get install -y python-software-properties"
    gluster3.vm.provision :shell, :inline => "sudo add-apt-repository -y ppa:gluster/glusterfs-3.5"
    gluster3.vm.provision :shell, :inline => "sudo apt-get update -y"
    gluster3.vm.provision :shell, :inline => "sudo apt-get install -y glusterfs-server"
#    gluster3.vm.provision :shell, :inline => "sudo service glusterfs-server start"
    gluster3.vm.provision :shell, :inline => "sudo mkdir -p /srv/brick{1,2,3,4} /mnt/point{1,2}"
    gluster3.vm.provision :shell, :inline => "echo sudo mount -t glusterfs 127.0.0.1:/gv1 /mnt/point1 >> .bashrc"
    gluster3.vm.provision :shell, :inline => "echo sudo mount -t glusterfs 127.0.0.1:/gv2 /mnt/point2 >> .bashrc"
  end

  config.vm.define :gluster4 do |gluster4|
    gluster4.vm.box = vmbox
    gluster4.vm.box_url = vmboxurl
    gluster4.vm.host_name = "gluster4"
    gluster4.vm.network :hostonly, "192.168.33.13"
    gluster4.vm.provision :shell, :inline => "sudo apt-get update -y"
    gluster4.vm.provision :shell, :inline => "sudo apt-get install -y python-software-properties"
    gluster4.vm.provision :shell, :inline => "sudo add-apt-repository -y ppa:gluster/glusterfs-3.5"
    gluster4.vm.provision :shell, :inline => "sudo apt-get update -y"
    gluster4.vm.provision :shell, :inline => "sudo apt-get install -y glusterfs-server"
#    gluster4.vm.provision :shell, :inline => "sudo service glusterfs-server start"
    gluster4.vm.provision :shell, :inline => "sudo mkdir -p /srv/brick{1,2,3,4} /mnt/point{1,2}"
    gluster4.vm.provision :shell, :inline => "sudo gluster peer probe 192.168.33.10"
    gluster4.vm.provision :shell, :inline => "sudo gluster peer probe 192.168.33.11"
    gluster4.vm.provision :shell, :inline => "sudo gluster peer probe 192.168.33.12"
    gluster4.vm.provision :shell, :inline => "sudo gluster volume create gv1 replica 2 192.168.33.10:/srv/brick1 192.168.33.11:/srv/brick1 192.168.33.12:/srv/brick1 192.168.33.13:/srv/brick1 force"
    gluster4.vm.provision :shell, :inline => "sudo gluster volume create gv2 replica 3 192.168.33.10:/srv/brick2 192.168.33.11:/srv/brick2 192.168.33.12:/srv/brick2 192.168.33.13:/srv/brick2 192.168.33.10:/srv/brick3 192.168.33.11:/srv/brick3 192.168.33.12:/srv/brick3 192.168.33.13:/srv/brick3 192.168.33.10:/srv/brick4 192.168.33.11:/srv/brick4 192.168.33.12:/srv/brick4 192.168.33.13:/srv/brick4 force"
    gluster4.vm.provision :shell, :inline => "sudo gluster volume start gv1"
    gluster4.vm.provision :shell, :inline => "sudo gluster volume start gv2"
    gluster4.vm.provision :shell, :inline => "sudo mount -t glusterfs 127.0.0.1:/gv1 /mnt/point1"
    gluster4.vm.provision :shell, :inline => "sudo mount -t glusterfs 127.0.0.1:/gv2 /mnt/point2"
    gluster4.vm.provision :shell, :inline => "for i in `seq -w 1 100`; do sudo cp -rp /var/log/syslog /mnt/point1/copy-test-$i; done"
    gluster4.vm.provision :shell, :inline => "for i in `seq -w 1 100`; do sudo cp -rp /var/log/syslog /mnt/point2/copy-test-$i; done"
  end
end
