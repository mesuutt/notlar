
### Mevcut ekranlari listele
xrandr --current

### External Monitoru ekranin soluna koy:

xrandr --output HDMI1 --mode 1920x1080 --left-of LVDS1

### Laptop ekranini kapat

xrandr --output LVDS1 --off

### Ekranin parlakligini dusurmek icin

redshift -l -70.0:10.2 -t 3000:2000  -m randr -b 0.5 -O 3500
