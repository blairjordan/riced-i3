# Riced i3

![](screenshots/screenshot1.png?raw=true)

## Features

- Spotify (current song)
- Current weather
- 24HR clock
- Volume control
- Cryptocurrency price movements
- Network up/ down
- Total CPU usage %
- Total mem usage %
- Storage usage

## Requirements

### Fonts

Font-awesome: `ttf-font-awesome`

### rofi

Rofi is `drun` on steroids.

Install it here:
https://github.com/davatorium/rofi/blob/next/INSTALL.md#install-distribution

I use the rofi theme: `glue_pro_blue.rasi` (Set using `rofi-theme-selector`)

### py3status

py3status enables you to easily customize status bars via python modules or custom scripts.

See:

https://py3status.readthedocs.io/en/3.5/intro.html#installation

### OpenWeatherMap

In `i3status-bottom`, see `weather_owm`.

Replace `YOUR API KEY` with your OpenWeatherMap API key.

You can sign up for an account, and get a key here:
https://home.openweathermap.org/api_keys

Replace `(0, 0)` with your X, Y coordinates. You can find this info on Google maps.

```
weather_owm {
	api_key = "<YOUR API KEY>"
  location = (0, 0)
  forecast_days = 0
  unit_temperature = "C"
}
```

## Optional Stuff

Here are some obvious things you might want to change.

### Cryptocurrency

I display crypto price movements in my top bar.

In i3status-top, replace `<YOUR API KEY>` with your coinmarketcap API key:

```
coin_market = "<YOUR API KEY>"
```

Add your favorite cryptos to the `markets` / `thresholds`.

### Emojis

I love to abuse emojis - So much so that I have an emoji browser shortcut.

See rofimoji install here method here:

https://github.com/fdw/rofimoji#insertion-method

## Customization

### Drives

You probably want to change your drives.

I have two drives: 
- NVMe SSD; and
- SATA SSD

Use the following command to identify your drives:
`df -h -t ext4 -t vfat -t fuse.sshfs | grep -v "boot"`

Use the output name as the `disk` (don't include `/dev/`).

```
diskdata nvme {
  disk = nvme0n1p2
  prefix_type = decimal
  format = "nvme{used_percent}%"
  thresholds = {
	  'used_percent': [(0, 'good'), (60, 'degraded'), (80, 'bad')]
  }
}

diskdata sda {
	disk = sda
	prefix_type = decimal
	format = "sata{used_percent}%"
}
```

### Conky

Conky is the application which displays system information on your desktop.

Copy the `conky` dir to `~/.config/conky/custom`.


#### CPU bars

Depending on how many CPU cores you have, you might want to modify the appearance `conky/conky.conf` (search for the line `${color}CPU 1`).

#### File systems

If you search for `${color1}File systems:`, you'll find again find hard-coded references to my disks. You probably also want to change these.
