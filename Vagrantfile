Vagrant.configure("2") do |config|
	config.vm.box = "precise64"
	config.vm.box_url = "http://files.vagrantup.com/precise64.box"

	config.vm.provision :shell, :inline => <<-'SH'
		aptitude -q -y update
		aptitude -q -y install git
		gem update --no-rdoc --no-ri --system
	SH

	config.vm.provision :shell, :inline => <<-'SH', :privileged => false
		cat <<-'EOT' > .bash_profile
			PATH="$(ruby -rubygems -e 'puts Gem.user_dir')/bin:$PATH"
		EOT
		. .bash_profile
		cat <<-'EOT' > .gemrc
			gem: --no-document
			install: --user-install
		EOT
		gem install rhc
		gem update rhc
	SH
end
