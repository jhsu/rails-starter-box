Vagrant.configure("2") do |config|
  config.vm.box       = 'learning-rails'
  config.vm.box_url   = 'learning-rails.box'
  # config.vm.box       = 'precise32'
  # config.vm.box_url   = 'http://files.vagrantup.com/precise32.box'
  
  host_username = "j" # Change this to your username

  if Vagrant::Util::Platform.windows?
    host_directory = "C:/Users/#{host_username}/documents/learning-rails"
  elsif Vagrant::Util::Platform.platform =~ /^darwin/
  	`mkdir -p $HOME/leraning-rails`
  	host_directory = "/Users/#{host_username}/learning-rails"
  else
  	`mkdir -p $HOME/leraning-rails`
  	host_directory = "/home/#{host_username}/learning-rails"
  end
  config.vm.synced_folder host_directory, "/home/vagrant/projects"
  config.vm.hostname = 'learning-rails'

  config.vm.network :forwarded_port, guest: 3000, host: 3000

  config.vm.provision :puppet,
    :manifests_path => 'puppet/manifests',
    :module_path    => 'puppet/modules'
end
