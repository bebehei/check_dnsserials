# check_dnsserials

Check your DNS is in sync by comparing the serials. This is a general icinga/icinga2/nagios/anyOtherNagiosFork plugin.

It is written in Shell (Bash).

# Installation and requirements

*   bash (it may be compliant to zsh, too. but not sh!)
*   [monitoring-plugins](https://github.com/monitoring-plugins/monitoring-plugins)
    On debian-based systems you need the package `nagios-plugins` or the package `monitoring-plugins`

# Usage

	check_dnsserials -d DOMAIN [-H DNS-MASTER] [-S DNS-SLAVES] [ -s SOA-SERIAL] [-w FAILS] [-c FAILS] [ -h -v ]

	DNS-MASTER: The master to get all main informations from
	DNS-SLAVES: The slaves to compare with the master's serial
	SOA-SERIAL: The serial number used to compare all DNS slaves (not recommended to set)
	FAILS: The amount of DNS servers allowed having another serial (=> amount of dns servers not in sync) (defaults to 0)

	If any of DNS-MASTER, DNS-SLAVES or SOA-SERIAL is unset, it'll get queried from the DNS system.

`FAILS` determines the amount of slaves, which are allowed out of sync.

Usecase: If you have 5 servers, and 2 are giving a wrong serial, the plugin will fall to warning if you specifiy `-w 2`. (vice-versa with `-c`)
