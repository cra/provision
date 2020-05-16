# provision
ansible playbooks for my machines

galaxy roles:
```
ansible-galaxy install kewlfft.aur
```

## Arch packages 

Initial installation should include only basic packages:

```
pacstrap /mnt base linux linux-firmware vim wpa_supplicant dhcpcd openssh grub efibootmgr wget python
```

Log in, enable sshd
```
systemctl start sshd.service
systemctl enable sshd.service
```

Copy keys

```
mkdir --mode=755 .ssh
wget https://github.com/cra.keys -O .ssh/authorized_keys
chmod 600 .ssh/authorized_keys
```

Uncomment `ansible_user=root` in `hosts.ini` file and comment it back once `base` role was completed succesfully.

You will still need to set your password by direct login.

## Video driver

```
lspci | grep -e VGA -e 3D
```

But, most likely, you going to use `xf86-video-intel`