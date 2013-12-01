# piwik-openshift

[Piwik][1] on [OpenShift][2].

## Setup

```sh
git clone https://github.com/tfausak/piwik-openshift.git
cd piwik-openshift
vagrant up
vagrant ssh
cd /vagrant
rhc setup
rhc app create piwik php-5.3
rhc cartridge add mysql-5.1 --app piwik
rm --force --recursive piwik
url=$(rhc app show piwik | awk '/Git URL/ { print $3 }')
git remote add rhc $url
git push --force rhc master
hostname=$(rhc app show piwik | awk '/SSH/ { print $2 }')
command='env | grep OPENSHIFT_MYSQL_DB_'
ssh $hostname $command
# http://piwik-<namespace>.rhcloud.com
```

[1]: http://piwik.org
[2]: https://www.openshift.com
