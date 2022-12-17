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
