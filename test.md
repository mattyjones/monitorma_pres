
### dev-foo.prd.amazon.com

    define hostgroup {
     hostgroup_name debian-servers
     alias  Debian GNU/Linux Servers
     members  localhost,webserver,ldapserver
    }

#### Service - SSH
    define service {
     hostgroup_name   debian-servers
     service_description  SSH
     check_command   check_ssh
     use    generic-service
     notification_interval  0
    }

#### Service - Ping
      define service {
       hostgroup_name   debian-servers
       service_description  PING
       check_command   check_ping!100.0,20%!500.0,60%
       use    generic-service
       notification_interval  0
      }
