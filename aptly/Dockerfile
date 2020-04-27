FROM ubuntu

apt-get update
apt install -y wget bzip2 gnupg gpgv gnupg awscli


wget -qO - https://www.aptly.info/pubkey.txt |  apt-key add -
printf "deb http://repo.aptly.info/ squeeze main" |  tee -a /etc/apt/sources.list.d/newrelic-infra.list
---------
gpg --generate-key
gpg --list-secret-keys
gpg --delete-secret-keys 1351797E54D61E378387D6583D6267774DC26E23
---------


gpg --no-default-keyring --keyring trustedkeys.gpg --keyserver pool.sks-keyservers.net --recv-keys BB29EE038ECCE87C
curl -s https://download.newrelic.com/infrastructure_agent/gpg/newrelic-infra.gpg |  apt-key add -
aptly mirror create newrelic2 https://download.newrelic.com/infrastructure_agent/linux/apt buster main
aptly mirror update newrelic2

aptly mirror list
aptly mirror show newrelic2
aptly snapshot create newrelic_snapshot from mirror newrelic2
aptly publish snapshot newrelic_snapshot

export AWS_ACCESS_KEY_ID="XXXXXXXX" AWS_SECRET_ACCESS_KEY="YYYYYYYYYYYY"
aptly publish snapshot newrelic_snapshot s3:nr-test:

--------
Configure S3 bucket as web hosting

sources.list:
deb http://nr-test.s3-website-us-east-1.amazonaws.com/ buster main


aptly repo add newrelic ./nri-haproxy_1.0.1-1_amd64.deb