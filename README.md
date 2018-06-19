# The Ninja
The Ninja - Local Development API Runner

To setup the Ninja for the first time

*PREREQUISITES*
* Make sure you have Git installed
* Make sure you have a JDK (1.8) installed

1. Download bfdev.ninja.pem SSL cert from LastPass and install:
```
sudo mkdir -p /etc/ssl/bfdev.ninja
sudo mv bfdev.ninja.pem /etc/ssl/bfdev.ninja
```

2. Download ninjacreds from LastPass to your personal home directory

3. Clone this repo and run the setup script:
```
git clone https://github.com/billfire/ninja.git
cd ninja
./setup.sh
```
This should install and configure Maven (if needed), dnsmasq, and haproxy.

4. Add 127.0.0.1 to list of DNS servers (Open Network Preferences..., Advanced..., DNS)

>NOTE: You will most likely lose all of your DNS settings if you use the default behavior.
>Make a note of your existing settings as a backup and re-add if necessary. 127.0.0.1 should 
>be the first entry so make sure it's at the top

5. Run all the things! 
```
./runallthethings.sh
```

The run script will clone the "master" branch of all of the APIs into /tmp/ninjagit, build, and run them.

Be sure to have any development versions of the APIs you're testing running through IntelliJ or whatever BEFORE running all the things,
with this in the run config:
```
JWT_BASE_DOMAIN=bfdev.ninja
```
And server ports configured like this:
```
login-api: SERVER_PORT=5010
user-api: SERVER_PORT=5011
lois-lane-api: SERVER_PORT=5003
company-api: SERVER_PORT=5004
obligation-api: SERVER_PORT=5005
payment-api: SERVER_PORT=5006
notifier-api: SERVER_PORT=5007
statements-api: SERVER_PORT=5008
invitations-api: SERVER_PORT=5009
```
