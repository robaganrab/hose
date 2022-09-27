# Add a WSL2 worker node

Due to differences on how WSL is working (systemd is not running by default),
this is separated into another document as more experimentation is needed.

## Add a worker node

Add the WSL2 as a worker node.
Create the node YAML similarly to above, but note the architecture node label.

```yaml
node-name: hose-wsl
write-kubeconfig-mode: 0644
write-kubeconfig: /etc/rancher/k3s/kubeconfig
tls-san:
  - "hose-wsl.local"
node-label:
  - "node-architecture=amd64"
```

Run the install script with worker only mode.
The K3S_TOKEN is stored by default at `/var/lib/rancher/k3s/server/node-token`.

```sh
curl -sfL https://get.k3s.io | K3S_URL=https://X:6443 K3S_TOKEN="X" sh -
```
