## Config NVIDIA-SMI + CUDA

### **Archlinux + sway**

- **Requisitos**

```bash
rm -rf ~/.nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
nvm install 20.13.1
nvm use 20.13.1
# yay
cp /etc/sway/config ~/.config/sway/config
# add
bindsym $mod+Shift+c exec chromium --start-maximized
cp /etc/xdg/foot/foot.ini ~/.config/foot
# read modify copy + paste + others

sudo pacman -S openssh

ssh-keygen -t rsa -b 4096 -C "correo@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
ssh -T git@hostname
# repositorio de yay
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

- **Archlinux + sway**

```bash
# config nvidia-smi
yay -S nvidia-470xx-dkms nvidia-470xx-utils lib32-nvidia-470xx-utils

sudo nano /etc/modprobe.d/blacklist-nouveau.conf
blacklist nouveau
options nouveau modeset=0
sudo mkinitcpio -P
sudo reboot
# config docker with nvidia-smi
sudo pacman -S nvidia-container-toolkit
sudo mkdir -p /etc/docker
sudo nano /etc/docker/daemon.json
# paste json
{
  "runtimes": {
    "nvidia": {
      "path": "/usr/bin/nvidia-container-runtime",
      "runtimeArgs": []
    }
  },
  "default-runtime": "nvidia"
}

# continue

sudo systemctl restart docker
sudo usermod -aG docker $USER
docker run --rm --gpus all nvidia/cuda:11.4.3-base-ubuntu20.04 nvidia-smi
```

- **cortex + unsloth + huggingface**

```bash
# opcion 4 Llama-3.2-3B
docker run --gpus all -it menloltd/cortex
docker exec -it cortex /usr/local/bin/cortex run unsloth/Llama-3.2-3B-Instruct-GGUF

docker exec -it cortex /usr/local/bin/cortex ps
docker exec -it cortex /usr/local/bin/cortex models start unsloth:Llama-3.2-3B-Instruct-GGUF:Llama-3.2-3B-Instruct-Q4_K_M.gguf
```

#### Referencias

[menloltd](https://hub.docker.com/r/menloltd/cortex)
