# Kubernetes Cluster with Raspberry Pi

## About The Project
I started this project to learn Kubernetes. I decided to create k8s cluster with raspberry pi because I had those already. I will be using  [K3s](https://k3s.io/) because it is lightweight kubernetes. I am going use RPI4 as master and RPI3 as worker nodes. Because I am using RPI3 HA mode (High Availability) is not possible. RPI3 cannot handle it. It wont be problem because aim of this project is to learn Kubernetes.

## Hardware
- 1x Raspberry Pi 4 4GB
- 2x Raspberry Pi 3 1GB
- 3x SD-Card 32GB

## Setting Kubernetes Cluster Up
- Install operation system to SD-cards. I Used Raspberry Pi OS Lite (64-bit) and flashed it with Raspberry Pi Imager. [(How to use Raspberry Pi Imager)](https://www.youtube.com/watch?v=ntaXWS8Lk34&t=5s)
- Enable SSH. After flashing SD-card open sd card and add `ssh` file without extension to root of the directory of the card.
- Insert SD-card to raspberry pi and power it up. connect via ssh `ssh pi@address`. Default password is `raspberry`. After login you should change password with `passwd`
- Setup Static IP to each raspberry pi [Great guide by PiMyLifeUp](https://pimylifeup.com/raspberry-pi-static-ip-address/)
- Update `/etc/hosts` file with new information example: `STATIC-IP hostname` for every raspberry pi 
- Change hostname to each raspberry pi `sudo hostnamectl set-hostname newhostname`. I named raspberrys as following: rpi4=kmaster, rpi3=knode0, knode1...
- Add `cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1` to `/boot/cmdline.txt`
- Reboot raspberry pi and reconnect

More will be added later: installing k3s, connecting workers to master, etc. 
