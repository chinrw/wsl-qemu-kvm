# wsl-qemu-kvm

### Enable WSL2 and install Ubuntu

`https://learn.microsoft.com/en-us/windows/wsl/install`

### Install `attr` package on Linux guest
`sudo apt install attr` For Ubuntu

### Edit /etc/wsl.conf on Linux guest
```
[boot]
systemd=true
command = /bin/bash -c 'chown -v root:kvm /dev/kvm && chmod 660 /dev/kvm'


[wsl2]
nestedVirtualization=true
```

Remember to restart WSL2 `wsl --shutdown` after editing wsl.conf

### Adding yourself to the kvm group
`sudo usermod -a -G kvm ${USER}`

#### Check kvm is enabled

Run `kvm-ok` on guest. For this to work, you need to have installed the `cpu-checker` package, otherwise, you will bump into the error `Command 'kvm-ok' not found`.


### Install deps for kernel compiling
Then you could follow the instructions on MP0
