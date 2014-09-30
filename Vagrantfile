# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Turn on ssh x11 forwarding to true
  config.ssh.forward_x11 = "true"

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.provider "virtualbox" do |v|
    v.memory = 512
    v.cpus = 1
  end

  config.vm.provider "parallels" do |v|
    v.memory = 512
    v.cpus = 1
  end

  #####
  # Main CDash Dashboard.
  #####

  config.vm.define "dash", primary: true do |v|
    v.vm.provision :shell, :path => "bootstrap_dashboard.sh"
    v.vm.network "private_network", ip: "10.1.2.10"
    v.vm.box = "ubuntu/precise64"
    v.vm.hostname = "dashboard"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "256"
                   ]
    end
  end

  ######
  # Ubuntu Boxes
  ######

  # Using a pre-built, pre-provisioned image.
  config.vm.define "prebuilt_t64" do |v|
    v.vm.box = "nc_t64"
    v.vm.hostname = "nct64"

  end

  config.vm.define "prebuilt_t32" do |v|
    v.vm.box = "nc_t32"
    v.vm.hostname = "nct32"

  end

  config.vm.define "t64" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "ubuntu/trusty64"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "4096",
                    "--cpus", "2"
                   ]
    end
  end

  config.vm.define "t64_big" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "ubuntu/trusty64"
    v.vm.hostname = "bigt64"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "4096",
                    "--cpus", "2"
                   ]
    end
  end

  config.vm.define "t32" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "ubuntu/trusty32"
  end

  config.vm.define "t32_big" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "ubuntu/trusty32"
    v.vm.hostname = "bigt32"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "4096",
                    "--cpus", "2"
                   ]
    end
  end

  config.vm.define "s64" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "saucy64"
  end

  config.vm.define "s32" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "saucy32"
  end

  config.vm.define "p64" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "ubuntu/precise64"
  end

  config.vm.define "p32" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "ubuntu/precise32"
  end

  ######
  # End Ubuntu Boxes
  ######

  #####
  # Start Debian Boxes
  #####

  config.vm.define "debian64" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "debian64"
  end

  config.vm.define "debian32" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "debian32"
  end

  #####
  # Start Debian Boxes
  #####

  ######
  # Start CentOS Boxes
  ######

  config.vm.define "cent64" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "centos64"
  end

  config.vm.define "cent32" do |v|
    v.vm.provision :shell, :path => "bootstrap_ci.sh"
    v.vm.box = "centos32"
  end

  ######
  # End CentOS Boxes
  ######

  ######
  # Ubuntu Boxes for HDF5 Parallel Tests
  # Use MPICH and OPENMPI configurations.
  ######

  # OpenMPI configurations

  config.vm.define "t64_openmpi" do |v|
    v.vm.provision :shell, :path => "bootstrap_openmpi.sh"
    v.vm.box = "ubuntu/trusty64"
    v.vm.hostname = "t64openmpi"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "1024",
                    "--cpus", "2"
                   ]
    end
  end

  config.vm.define "t32_openmpi" do |v|
    v.vm.provision :shell, :path => "bootstrap_openmpi.sh"
    v.vm.box = "ubuntu/trusty32"
    v.vm.hostname = "t32openmpi"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "1024",
                    "--cpus", "2"
                   ]
    end
  end

  # MPICH configurations

  config.vm.define "t64_mpich" do |v|
    v.vm.provision :shell, :path => "bootstrap_mpich.sh"
    v.vm.box = "ubuntu/trusty64"
    v.vm.hostname = "t64mpich"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "1024",
                    "--cpus", "2"
                   ]
    end
  end

  config.vm.define "t32_mpich" do |v|
    v.vm.provision :shell, :path => "bootstrap_mpich.sh"
    v.vm.box = "ubuntu/trusty32"
    v.vm.hostname = "t32mpich"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "1024",
                    "--cpus", "2"
                   ]
    end
  end

  ######
  # End Ubuntu Boxes for HDF5 Parallel Tests
  #####

  ######
  # Ubuntu Boxes for pnetcdf Parallel Tests
  ######
  config.vm.define "t64_pnet" do |v|
    v.vm.provision :shell, :path => "bootstrap_pnet_ci.sh"
    v.vm.box = "ubuntu/trusty64"
    v.vm.hostname = "t64pnet"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "1024",
                    "--cpus", "2"
                   ]
    end
  end

  config.vm.define "t32_pnet" do |v|
    v.vm.provision :shell, :path => "bootstrap_pnet_ci.sh"
    v.vm.box = "ubuntu/trusty32"
    v.vm.hostname = "t32pnet"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "1024",
                    "--cpus", "2"
                   ]
    end
  end
  ######
  # End Ubuntu Boxes for pnetcdf Parallel Tests
  ######

  ######
  # Plain ubuntu box.
  ######

  config.vm.define "plain", primary: true do |v|
    v.vm.box = "ubuntu/trusty64"
    v.vm.hostname = "plain"

    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "512"
                   ]
    end
  end

  # Pre-built developer boxes, without ctest infrastructure.
  config.vm.define "dev64" do |v|
    v.vm.box = "wf_dev64"
    v.vm.hostname = "dev64"
    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "2048",
                    "--cpus", "2"
                   ]
    end
  end

  config.vm.define "dev32" do |v|
    v.vm.box = "wf_dev32"
    v.vm.hostname = "dev32"
    v.vm.provider "virtualbox" do |vb|
      vb.customize [
                    "modifyvm", :id,
                    "--memory", "2048",
                    "--cpus", "2"
                   ]
    end
  end

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  # config.vm.box_url = "http://domain.com/path/to/above.box"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:
  #   vb.customize ["modifyvm", :id, "--memory", "1024"]
  # end
  #
  # View the documentation for the provider you're using for more
  # information on available options.

  # Enable provisioning with Puppet stand alone.  Puppet manifests
  # are contained in a directory path relative to this Vagrantfile.
  # You will need to create the manifests directory and a manifest in
  # the file precise64.pp in the manifests_path directory.
  #
  # An example Puppet manifest to provision the message of the day:
  #
  # # group { "puppet":
  # #   ensure => "present",
  # # }
  # #
  # # File { owner => 0, group => 0, mode => 0644 }
  # #
  # # file { '/etc/motd':
  # #   content => "Welcome to your Vagrant-built virtual machine!
  # #               Managed by Puppet.\n"
  # # }
  #
  # config.vm.provision "puppet" do |puppet|
  #   puppet.manifests_path = "manifests"
  #   puppet.manifest_file  = "site.pp"
  # end

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  #
  # config.vm.provision "chef_solo" do |chef|
  #   chef.cookbooks_path = "../my-recipes/cookbooks"
  #   chef.roles_path = "../my-recipes/roles"
  #   chef.data_bags_path = "../my-recipes/data_bags"
  #   chef.add_recipe "mysql"
  #   chef.add_role "web"
  #
  #   # You may also specify custom JSON attributes:
  #   chef.json = { :mysql_password => "foo" }
  # end

  # Enable provisioning with chef server, specifying the chef server URL,
  # and the path to the validation key (relative to this Vagrantfile).
  #
  # The Opscode Platform uses HTTPS. Substitute your organization for
  # ORGNAME in the URL and validation key.
  #
  # If you have your own Chef Server, use the appropriate URL, which may be
  # HTTP instead of HTTPS depending on your configuration. Also change the
  # validation key to validation.pem.
  #
  # config.vm.provision "chef_client" do |chef|
  #   chef.chef_server_url = "https://api.opscode.com/organizations/ORGNAME"
  #   chef.validation_key_path = "ORGNAME-validator.pem"
  # end
  #
  # If you're using the Opscode platform, your validator client is
  # ORGNAME-validator, replacing ORGNAME with your organization name.
  #
  # If you have your own Chef Server, the default validation client name is
  # chef-validator, unless you changed the configuration.
  #
  #   chef.validation_client_name = "ORGNAME-validator"
end
