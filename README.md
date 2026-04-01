# tuxedo-control-center-dinit

## Original tccd service
``` 
# /usr/lib/systemd/system/tccd.service
[Unit]
Description=TUXEDO Control Center Service

[Service]
Type=simple
ExecStart=/opt/tuxedo-control-center/resources/dist/tuxedo-control-center/data/service/tccd --start
ExecStop=/opt/tuxedo-control-center/resources/dist/tuxedo-control-center/data/service/tccd --stop

[Install]
WantedBy=multi-user.target

```
## Dinit Services (WIP)
```
# /etc/dinit.d/tccd
type            = process
command         = /opt/tuxedo-control-center/resources/dist/tuxedo-control-center/data/service/tccd --start
stop-command    = /opt/tuxedo-control-center/resources/dist/tuxedo-control-center/data/service/tccd --stop
smooth-stop     = true
waits-for       = recovery
```
