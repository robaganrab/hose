# Preparing the OS

Based on the [k3s documentation][k2s-prep-rpi], we need some
OS level setting to be prepared to run k3s:

* Enable legacy iptables.
* Enable cgroups.
* Change inputrc for history search.

```sh
sudo iptables -F
sudo update-alternatives --set iptables /usr/sbin/iptables-legacy
sudo update-alternatives --set ip6tables /usr/sbin/ip6tables-legacy

sudo perl -i -pe 'chomp; $_ .= " cgroup_memory=1 cgroup_enable=memory"' /boot/cmdline.txt

sudo perl -i -pe 's/# ("\\e\[[56].+history-search-(?:forward|backward))/$1/' /etc/inputrc

sudo reboot
```

## References

* k3s preparations: [link][k3s-prep-rpi]

[k3s-prep-rpi][https://rancher.com/docs/k3s/latest/en/advanced/#additional-preparation-for-raspberry-pi-os-setup]
