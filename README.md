# ALPINE SERVER

- ALPINE LINUX: [Download](https://alpinelinux.org/downloads/) run: setup-alpine

/root/
```
crontabs.txt
install-bash-autosuggestions.sh
lazydocker
lazydocker_0.24.1_Linux_arm64.tar.gz
ngrok-v3-stable-linux-arm64.tgz
ookla-speedtest-1.2.0-linux-aarch64.tgz
remove-auto-shutdown.sh
speedtest
tcpapp-init.sh
```

/boot/config.txt
```
# RASPBERRY PI
usb_max_current_enable=1
```

remove-auto-shutdown.sh
```
ps aux | grep -E 'acpid|powerd|sleep|hibernate'
rc-update del acpid
rc-service acpid stop
rc-status
```

crontab -l # crontabs.txt
```
@reboot echo 1 | sudo tee /sys/class/thermal/cooling_device0/cur_state # CPU FAN
*	*	*	*	*	rm /var/lib/docker/containers/**/*-json.log
```

install-bash-autosuggestions.sh
```
#!/bin/bash
echo 'cd '"$(dirname "$0")"
cd "$(dirname "$0")"

# sudo apt install gcc make gawk
bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh)"
sudo rm -R ~/.ble.sh
git clone --recursive https://github.com/akinomyoga/ble.sh.git ~/.ble.sh
make -C ~/.ble.sh
source ~/.ble.sh/out/ble.sh

if [[ $(grep "~/.ble.sh/out/ble.sh" ~/.bashrc) == "source ~/.ble.sh/out/ble.sh" ]]; then
  echo "--------------------------------------------------------------"
  echo "Exists ~/.ble.sh/out/ble.sh ==> ~/.bashrc"
  echo "--------------------------------------------------------------"
else
  echo "source ~/.ble.sh/out/ble.sh" >> ~/.bashrc
fi
```

tcpapp-init.sh
```
#!/bin/bash
echo 'cd '"$(dirname "$0")"
cd "$(dirname "$0")"

 docker stop tcpapp22
 docker rm tcpapp22
 docker rmi manhavn/tcpapp:v0.0.1
 docker run -d \
  --restart always \
  --name tcpapp22 \
  -e GO_APP_ENDPOINT_SERVER=iot.zii.ovh:4000 \
  -e GO_APP_ENDPOINT_TARGET=172.17.0.1:22 \
  -e GO_APP_ENDPOINT_PORT=55588 \
  -it manhavn/tcpapp:v0.0.1
```

.ash_history
```
	ip a
	apk add nano
	nano /etc/apk/repositories
	apk update
	apk add --update docker openrc
	rc-update add docker boot
	service docker start
	service docker status
	docker ps
	mkdir .ssh
	nano .ssh/authorized_keys
	passwd root
	apk add lsblk
	lsblk
	reboot
	nano tcpapp-init.sh
	sh tcpapp-init.sh
	apk add htop
	htop
	wget https://github.com/jesseduffield/lazydocker/releases/download/v0.24.1/lazydocker_0.24.1_Linux_arm64.tar.gz
	tar xf lazydocker_0.24.1_Linux_arm64.tar.gz 
	install lazydocker /usr/local/bin/
	lazydocker
	wpa_supplicant
	nano /etc/wpa_supplicant/wpa_supplicant.conf
	# poweroff
	ip a
	apk add git
	apk add gawk
	apk add gcc
	apk add make
	apk add zip
	apk add curl
	apk add bash
	apk add bash-doc
	apk add bash-completion
	apk add sudo
	nano /etc/passwd # root:x:0:0:root:/root:/bin/bash
	exit
	nano install-bash-autosuggestions.sh
	sh install-bash-autosuggestions.sh 
	source ~/.ble.sh/out/ble.sh
	cat ~/.bash_profile
	cat ~/.bashrc
	nano ~/.bashrc
	ls -a
	apk add awake
	awake 7C:10:C9:1F:E0:31
	ngrok config add-authtoken xxxxxxxxxxxxxxxxxxxxxxxxxxx
	ngrok tcp 22
```
