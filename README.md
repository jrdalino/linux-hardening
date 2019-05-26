# Linux Hardening

## Install Software Updates
- CentOS
```
$ yum update
```
- Debian/Ubuntu
```
$ apt-get update && apt-get upgrade
```

## Setting Up

### Set the Hostname
- CentOS 7 / Ubuntu 16.04 and above
```
$ cat /etc/hosts
$ hostnamectl set-hostname example_hostname
$ cat /etc/hosts
```

- CentOS 6
```
$ echo "HOSTNAME=example_hostname" >> /etc/sysconfig/network
$ hostname "hostname"
```

- Ubuntu 14.04
```
$ echo "example_hostname" > /etc/hostname
$ hostname -F /etc/hostname
```

### Set the Timezone (Optional)
- CentOS 7
```
$ timedatectl list-timezones
$ timedatectl set-timezone 'America/New_York'
$ date
```

- Ubuntu
```
$ dpkg-reconfigure tzdata
$ date
```

## Add a Limited User Account
- CentOS 7
- Create the user, replacing example_user with your desired username, and assign a password and Add the user to the wheel group for sudo privileges:
```
$ useradd example_user && passwd example_user
$ usermod -aG wheel example_user
```

- Ubuntu
- Create the user, replacing example_user with your desired username. You’ll then be asked to assign the user a password and Add the user to the sudo group so you’ll have administrative privileges:
```
$ adduser example_user
$ adduser example_user sudo
```

## Harden SSH Access

### Create an Authentication Key Pair

### SSH Daemon Options
- Disallow root logins over SSH
- Disable SSH password authentication
- Listen on only one internet protocol

### Use Fail2Ban for SSH Login Protection
- http://www.fail2ban.org/wiki/index.php/Main_Page

## Remove Unused Network-Facing Services

### Determine Running Services
```
$ sudo ss -atpu
```

### Determine Which Services to Remove
- nmap

### Uninstall the Listening Services
- CentOS
```
$ sudo yum remove package_name
```

- Ubuntu
```
$ sudo apt purge package_name
```

## Configure a Firewall
- CentOS (FirewallD/Iptables)
- Ubuntu (UFW/Iptables)
