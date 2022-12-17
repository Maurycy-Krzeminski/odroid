# script for printing temps
```
# Print date
date
# CPU and GPU terms from /sys/class/thermal and ssd nvme0
paste <(cat /sys/class/thermal/thermal_zone*/type) <(cat /sys/class/thermal/thermal_zone*/temp) \
| column -s $'\t' -t | sed 's/\(.\)..$/.\1°C/' && \
echo -n ssd-thermal\ && sudo nvme smart-log /dev/nvme0 \
| grep -o [[:space:]][[:digit:]][[:digit:]][[:space:]] | column -s $'\t' -t | sed 's/\(.\)$/°C/'
```
