# Linux

## Task 1. OS Installation
```
First task was to install and configure Ubuntu 20.04 using virtual machine (using VirtualBox)
```
We can check if OS installed successfully running `cat /etc/issue` command.
![part1](./img/part1.png "Part 1")

## Task 2. Creating a user
```
Second task was to create a new user
```
To create a new user we can call `sudo useradd $USERNAME` command. After new user created we can check its data running `cat etc/passwd` command.
![part2](./img/part2.png "Part 2")

## Task 3. Setting up the OS network
```
Here we are to set up the OS network
```
- First we need to change machine's name to `user-1`. We can do it with `sudo hostnamectl set-hostname $HOSTNAME` command.
![part3_hostname](./img/part3/hostname.png "Part 3 - hostname")

- Then we are to set up current timezone. To do it we can run `sudo timedatectl set-timezone $TIMEZONE` command.
![part3_timezone](./img/part3/timezone.png "Part 3 - timezone")

- After timezone is setted up we can get network interfaces names running `ip -br link show` command.
![part3_ninterface](./img/part3/ninterface.png "Part 3 - ninterface")
IO - is a virtual interface included **by default** in any Linux. It is used to debug network programs and run server applications on a local machine. The address 127.0.0.1 is always associated with this interface. It has a dns name - localhost.

- Then we are to check machine's IP addres. We can do it running `ip a` command
![part3_ipaddress](./img/part3/ipaddress.png "Part 3 - ipaddress")

- And get address from DHCP server (eliminates human error so that address conflicts, configuration errors, or simple typos are minimized) using `sudo dhclient -v enp0s3`.
![part3_dhcp](./img/part3/dhcp.png "Part 3 - dhcp")

- After we got address from DHCP server we can get internal and external gateway IP addresses running `wget -qO- eth0.me` (external) and `ip route | grep default` (internal) commands.
![part3_gateway](./img/part3/gateway.png "Part 3 - gateway")

- To set static setting for IP, DNS and gw first we need to off DHCP. To do it simply change DHCP state and add static IPs in `/etc/netplan/00-installer-config.yaml`
![part3_vimdhcp](./img/part3/vimdhcp.png "Part 3 - vimdhcp")

    So now we got static IP, DNS and gw
    ![part3_staticip](./img/part3/staticip.png "Part 3 - staticip")

- After running `ping $ADDRESS` command we got
![part3_pingtest](./img/part3/pingtest.png "Part 3 - pingtest")





