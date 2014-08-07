eximctl
=======

**exim control tool**. Allows to perform administrative tasks using friendly interface. Probably useful for those who cannot remember all these *sendmail*-like switches. 

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

# eximctl freeze to fork.pl
1WdGuK-0002pW-Bw root@fork.pl -> root@fork.pl
Message 1WdGuK-0002pW-Bw is now frozen
```

## options
```
   start                  -- start exim via service
   stop                   -- stop exim via service and SIGTERM + SIGKILL
   restart                -- stop + start
   status                 -- status
   what                   -- full status
   kill                   -- kill all exim process
   alive                  -- check if exim is alive (report via exitcode)
   pids                   -- list pids of exim processes
   top                    -- exitop (using exim main log)

   config                 -- show config
   syntax                 -- test configuration syntax
   reload                 -- reload config with SIGHUP
   version                -- show exim version

   mailq                  -- show the queue
   mailqq                 -- show the queue (brief format)
   queue                  -- show the queue, mailq alias
   qsize                  -- show queue size
   qstats                 -- queue statistics
   qgrep <msg spec>       -- grep queue (brief format)

   flush <msg spec>       -- flush queue
   flushall               -- flush all (including frozen, exim -qff mode)

   log <msg spec>         -- show log for message
   head <msg spec>        -- show message header
   body <msg spec>        -- show message body
   contents <msg spec>    -- show complete contents (header+body) of message

   delete <msg spec>      -- delete message from queue (no error sent)
   fail <msg spec>        -- fail message (bounce)
   freeze <msg spec>      -- freeze message
   thaw <msg spec>        -- thaw (unfreeze) message

   routing email          -- view routing for email

    <msg spec> -- specification for message:
     - msg id - message id, formatted as xxxxxx-xxxxxx-xx
     - [from|to] regexp - regexp to be matched against sender (from, the default) or recipient (to)
     - use explicit regexp to match all messages (eg. single dot would match any message)
```
## configuration file
*eximctl* looks for **eximctl.conf** in standard locations (*/etc/*, */usr/local/etc* and direcotry where eximctl script is stored -- in this particular order). *eximctl* reads config files from all the locations. Settings are described in default config file. In case no config file exists eximctl uses built-in defaults (same as in the default config file).

## dependencies

It's assumed that all binaries and scripts used by *eximctl* are available in $PATH.

Following external tools are required:

 * exim binary (tested with modern exim 4.x)
 * scripts installed with exim (*exiqgrep*, *exiwhat* etc.)
 * *top* command uses *exitop* script, available at https://github.com/mcnewton/exitop . In case *exitop* is not found in $PATH there is additional configuration option to specify explicit path.
 * *ps* tool (any POSIX compliant version should do but tested only with FreeBSD 9+ base-system version and Linux procps-ng v.3)
 * */sbin/service* to allow exim daemon management

## author

Marcin Gryszkalis <mg@fork.pl>


