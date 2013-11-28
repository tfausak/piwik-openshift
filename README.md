# piwik-openshift

[Piwik][1] running on [OpenShift][2] for [taylor.fausak.me][3].

## Setup

```sh
git clone https://github.com/tfausak/piwik-openshift.git
cd piwik-openshift
vagrant up
vagrant ssh
```

```sh
cd /vagrant
rhc setup
rhc app create piwik php-5.3
rhc cartridge add mysql-5.1 --app piwik
ssh $(rhc app show piwik | grep SSH | awk '{ print $2 }') 'env | grep OPENSHIFT_MYSQL_DB_'
```

## Deploy

```sh
cd /vagrant
git remote add rhc $(rhc app show piwik | grep 'Git URL' | awk '{ print $3 }')
git push rhc master
```

[1]: http://piwik.org
[2]: https://www.openshift.com
[3]: http://taylor.fausak.me
