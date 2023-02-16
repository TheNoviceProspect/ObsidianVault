This is the install on a container based image as opposed to a full vm
wget -O - https://get.ispconfig.org | sudo sh -s -- --no-firewall --use-nginx --no-quota --use-ftp-ports=40110-40210 --unattended-upgrades

Web: 20, 21, 22, 80, 443 and 40110:40210 (All TCP, no UDP)
Mail: 25, 110, 143, 465, 587, 993, and 995 (All TCP, no UDP)
DNS: 53 (TCP and UDP)
Panel: 8080 and 8081 (All TCP, no UDP)


---
Full ISP Install option list:

>Usage: ispc3-ai.sh [] [...]

This script automatically installs all needed packages for an ISPConfig 3 setup using the guidelines from the "Perfect Server Setup" howtos on www.howtoforge.com.

Possible arguments are:
    --help          Show this help page
    --debug         Enable verbose logging (logs each command with the exit code)
    --channel       Choose the channel to use for ISPConfig. --channel=<stable|dev>
                    "stable" is the latest ISPConfig release available on www.ispconfig.org
                    "dev" is the latest stable-branch from the ISPConfig git repository: https://git.ispconfig.org/ispconfig/ispconfig3/tree/stable-3.1
                    -> The dev channel might contain bugs and less-tested features and should only be used in production by very experienced users.
    --lang          Use language for ISPConfig installation. Specify with --lang=en|de (only en (English) and de (German) supported currently).
    --interactive   Don't install ISPConfig in non-interactive mode. This is needed if you want to use expert mode, e. g. to install a slave server that shall be integrated into an existing
                    multiserver setup.
    --use-nginx     Use nginx webserver instead of apache2
    --use-amavis    Use amavis instead of rspamd for mail filtering
    --use-unbound   Use unbound instead of bind9 for local resolving. Only allowed if --no-dns is set.
    --use-php       Use specific PHP versions, comma separated, instead of installing multiple PHP, e.g. --use-php=7.4,8.0 (5.6, 7.0, 7.1, 7.2, 7.3, 7.4 and 8.0 available).
                    --use-php=system disables the sury repository and just installs the system's default PHP version.
                    ommiting the argument (use all versions)
    --use-ftp-ports This option sets the passive port range for pure-ftpd. You have to specify the port range separated by hyphen, e. g. --use-ftp-ports=40110-40210.
                    If not provided the passive port range will not be configured.
    --use-certbot   Use Certbot instead of acme.sh for issuing Let's Encrypt certificates. Not adviced unless you are migrating from a old server that uses Certbot.
    --no-web        Do not use ISPConfig on this server to manage webserver setting and don't install nginx/apache or pureftpd. This will also prevent installing an ISPConfig UI and implies
                    --no-roundcube as well as --no-pma
    --no-mail       Do not use ISPConfig on this server to manage mailserver settings. This will install postfix for sending system mails, but not dovecot and not configure any settings for
                    ISPConfig mail. It implies --no-mailman.
    --no-dns        Do not use ISPConfig on this server to manage DNS entries. Bind will be installed for local DNS caching / resolving only.
    --no-local-dns  Do not install local DNS caching / resolving via bind.
    --no-firewall   Do not install ufw and tell ISPConfig to not manage firewall settings on this server.
    --no-roundcube  Do not install roundcube webmail.
    --roundcube     Install Roundcube even when --no-mail is used. Manual configuration of Roundcube config is needed.
    --no-pma        Do not install PHPMyAdmin on this server.
    --no-mailman    Do not install Mailman mailing list manager.
    --no-quota      Disable file system quota
    --no-ntp        Disable NTP setup
    --unattended-upgrades
                    Install UnattendedUpgrades. You can add extra arguments for automatic cleanup and automatic reboots when necessary with --unattended-upgrades=autoclean,reboot (or only
                    one of them).
    --i-know-what-i-am-doing
                    Prevent the autoinstaller to ask for confirmation before continuing to reconfigure the server.