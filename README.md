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
rhc setup
```

## Deploy

```sh
cd /vagrant
git remote add rhc ssh://5294b15e5004462b480001e4@piwik-fausak.rhcloud.com/~/git/piwik.git
git push rhc master
```

[1]: http://piwik.org
[2]: https://www.openshift.com
[3]: http://taylor.fausak.me
