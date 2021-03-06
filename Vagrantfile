$VAGRANT_CONFIG_VERSON = 2
Vagrant.require_plugin "vagrant-aws"
Vagrant.require_plugin "vagrant-winrm-syncedfolders"

Vagrant.configure($VAGRANT_CONFIG_VERSION) do |config|
  config.vm.box = "dummy"
  config.vm.box_url = "https://github.com/mitchellh/vagrant-aws/blob/master/dummy.box?raw=true"
  config.vm.communicator = "winrm"
  config.vm.guest = :windows

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV["AWS_SECRET_ACCESS_KEY"]
    aws.keypair_name = ENV["AWS_KEYPAIR_NAME"]

    aws.ami = "ami-fa05b392"
    aws.tags = {
      'Name' => ENV["ASSET_NAME"],
      'net.matrix.orgunit' => "Infrastructure",
      'net.matrix.organization' => "Dallas Makerspace",
      'net.matrix.commonname' => "cloud",
      'net.matrix.locality' => "Dallas",
      'net.matrix.state' => "Texas",
      'net.matrix.country' => "USA",
      'net.matrix.environment' => "nonprod",
      'net.matrix.application' => "infrastructure",
      'net.matrix.role' => "application services",
      'net.matrix.owner' => "infrastructure@dallas.ms",
      'net.matrix.customer' => "PVT-01",
      'net.matrix.costcenter' => "INT-01"
    }
    
    aws.instance_type = "t2.micro"
    aws.region = ENV["AWS_DEFAULT_REGION"]
    aws.subnet_id = ENV["AWS_SUBNET"]
    aws.security_groups = ENV["AWS_SECURITY_GROUPS"]
    override.nfs.functional = false
  end
end
