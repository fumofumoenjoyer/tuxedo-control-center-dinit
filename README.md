# tuxedo-control-center-dinit

## Original tccd and tccd-sleep
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
```
# /usr/lib/systemd/system/tccd-sleep.service
[Unit]
Description=TUXEDO Control Center Service (sleep/resume)
Before=sleep.target
StopWhenUnneeded=yes

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/bin/bash -c "systemctl stop tccd"
ExecStop=/bin/bash -c "systemctl start tccd"

[Install]
WantedBy=sleep.target


```
