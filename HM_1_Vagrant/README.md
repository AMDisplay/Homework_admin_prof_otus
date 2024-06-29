# vagrant_repo

## Скачиваем box centos8 и закидываем его в папку рядом с Vagrant файлом

https://app.vagrantup.com/centos/boxes/8

## Добавляем бокс

vagrant box add 'centos/8' CentOS-8-Vagrant-8.3.2011-20201204.2.x86_64.vagrant-virtualbox.box

## Выключаем автоматически обновления centos8

sudo sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-Linux-*
sudo yum install -y https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm

## Скачиваем обновление ядра

sudo yum install -y https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm

## Устанавливаем скаченное ядро

sudo yum --enablerepo elrepo-kernel install kernel-ml -y

## Обновляем конфигурация загрузчика

sudo grub2-mkconfig -o /boot/grub2/grub.cfg

## Ребутаем ВМ

sudo reboot
