# Tips

Use `/bin/ls -lF /dev/disk/by-uuid/` to see which symlinks point to the devices you want. And then in conky use those instead `${diskio_read /dev/disk/by-uuid/yyyyyyy}`

