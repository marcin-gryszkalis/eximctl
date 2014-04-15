eximctl
=======

exim control tool. Probably useful for those who cannot remember all these *sendmail*-like switches. 

## synopsis
```
# eximctl [command] [parameters]
```

## examples
```
# eximctl version
Exim version 4.82 #0 (FreeBSD 9.2) built 15-Feb-2014 17:56:40

# eximctl status
exim is running as pid 40177.

# eximctl log 1Wa1Xu-000KgD-XX
2014-04-15 13:36:21 Received from srvx@fork.pl U=srvx P=local S=38578
```

## configuration file
*eximctl* looks for **eximctl.conf** in standard locations (*/etc/* and */usr/local/etc* in this particular order). *eximctl* reads config files from all the locations. Settings are described in default config file. In case no config file exists eximctl uses defaults (same as in the default config file).



