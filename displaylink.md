source: https://askubuntu.com/questions/1507373/install-displaylink-drivers-on-ubuntu-22-04-lts-fix-the-square-around-mouse-err

```bash
wget https://www.synaptics.com/sites/default/files/Ubuntu/pool/stable/main/all/synaptics-repository-keyring.deb
sudo dpkg -i synaptics-repository-keyring.deb
sudo apt update
sudo apt install displaylink-driver
sudo reboot
```