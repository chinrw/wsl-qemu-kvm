# wsl-qemu-kvm

### Enable WSL2 and install Ubuntu

`https://learn.microsoft.com/en-us/windows/wsl/install`

### Edit /etc/wsl.conf

```
[boot]
systemd=true

[wsl2]
nestedVirtualization=true
```

Remember to restart WSL2 `wsl --shutdown` after editing wsl.conf

#### Check kvm is enabled

Run `kvm-ok`

### Install deps for kernel compiling

` sudo apt-get install libncurses-dev gawk flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf bc pahole attr openssh-server xterm`

### Install qemu
`sudo apt install qemu-kvm virt-manager virtinst libvirt-clients bridge-utils libvirt-daemon-system -y`

### Compile kernel
Prepare your config or just use https://github.com/cs423-uiuc/qemu-script/blob/main/.config for kernel 5.15
```
make -j`nproc`
```

### Run qemu script

```
git clone git@github.com:chinrw/qemu-script.git
cd qemu-script
chmod +x run_qemu.sh
sudo usermod -aG kvm $USER
```

 goto kernel dir
`/path/to/script/qemu-script/run_qemu.sh -s`
