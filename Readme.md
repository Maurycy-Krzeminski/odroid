# Installing k3s

```
curl -sfL https://get.k3s.io | sh -s - --write-kubeconfig-mode 644 
```

# Uninstalling k3s
```
/usr/local/bin/k3s-uninstall.sh
```


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

# Script for running docker registry
```
podman run -d -p 5000:5000 --name docker_registry -v /local/folder:/var/lib/registry registry
```

# Adding insecure registry to podman on Windows
```
wsl --distribution podman-machine-default
sudo vi /etc/containers/registries.conf
```
add insecure registry example:
```
[[registry]]
location = "example:5000"
insecure = true
```

To be sure it is updated run:
```
podman machine stop
podman machine start
```
