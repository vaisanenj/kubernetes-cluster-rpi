# Kubernetes Cluster with Raspberry Pi

## About The Project
I started this project to learn Kubernetes. I decided to create k8s cluster with raspberry pi because I had those already. I will be using  [K3s](https://k3s.io/) because it is lightweight kubernetes. I am going use Rpi4 as master and Rpi3 as worker nodes. Because I am using Rpi3 HA mode (High Availability) is not possible because Rpi3 cannot handle it. It wont be problem because aim of this project is to learn Kubernetes.

## Hardware
- 1x Raspberry Pi 4 4GB
- 2x Raspberry Pi 3 1GB
- 3x SD-Card 32GB
- 3x Ethernet cable (wifi is also possible)

## Setting Kubernetes Cluster Up
On Internet there is lot great guides how to do these things. I won't be writing new one because I am lazy. Instead I will include tutorials from others that have done same things. 

- Install operation system to SD-cards. I Used Raspberry Pi OS Lite (64-bit) and flashed it with Raspberry Pi Imager. [How to use Raspberry Pi Imager](https://www.youtube.com/watch?v=ntaXWS8Lk34&t=5s)
- Enable SSH. After flashing SD-card open sd card and add `ssh` file without extension to root of the directory of the card. [PiMyLifeUp - How to Enable SSH on Boot of the Raspberry Pi](https://pimylifeup.com/raspberry-pi-enable-ssh-boot/)
- Insert SD-card to raspberry pi, power it up and connect with SSH [PiMyLife - Raspberry Pi SSH](https://pimylifeup.com/raspberry-pi-ssh/)
- Change default password [PiMyFileUp - Default Raspbian Username and Password](https://pimylifeup.com/default-raspbian-username-and-password/)
- Setup Static IP to each raspberry pi [PiMyLifeUp - How to Setup a Raspberry Pi Static IP Address](https://pimylifeup.com/raspberry-pi-static-ip-address/)
- Change hostname [PiMyLifeUp - Raspberry Pi Hostname](https://pimylifeup.com/raspberry-pi-hostname/)
- Add to `/etc/hosts` each raspberry pi static ip and hostname. Example: `192.168.1.100 kmaster` etc..
- Add `cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1` to `/boot/cmdline.txt`
- Reboot raspberry pi and reconnect `sudo reboot`
- After reboot install k3s to master node and connect workers. [Rancher - Quick-Start Guide](https://rancher.com/docs/k3s/latest/en/quick-start/)
- Run `kubectl get nodes`. Output should show all nodes in ready status.
