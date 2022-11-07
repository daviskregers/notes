# Increase swap

Swap memory is used where operating system temporarily stores data when it runs out of RAM memory. It uses hard drive space to save this data.

```
sudo fallocate -l 10G /swapfile
ls -lh /swapfile
sudo chmod 600 /swapfile
ls -lh /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo swapon --show
free -h
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```