# -*- mode: ruby -*-
# vi: set ft=ruby :

# Specify Vagrant version and Vagrant API version
Vagrant.require_version ">= 2.0.1"
VAGRANTFILE_API_VERSION = "2"
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'

# Create and configure the Docker container(s)
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.ssh.insert_key = false

  config.vm.synced_folder "./", "/app/data"

  # Configure the Docker provider for Vagrant
  config.vm.provider "docker" do |docker|

    # Specify the Docker image to use
    # or the location of the Dockerfile
    #docker.image = "nginx"
	  docker.build_dir = "."

    # Specify port mappings
    # If omitted, no ports are mapped!
    docker.ports = ['15000:5000']

    # Environment Variables for Development
    docker.env = {
      "myhero_data_key" => "DevData",
      "myhero_data_dir" => "/app/data/"
    }

    # Specify a friendly name for the Docker container
    docker.name = 'myhero-data'
  end
end
