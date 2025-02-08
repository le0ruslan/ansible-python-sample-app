# -*- mode: ruby -*-
# vi: set ft=ruby :

#Подключение к стороннему репозитарию
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

Vagrant.configure("2") do |config|
  # Название образа
  config.vm.box = "ubuntu/jammy64"
  # Отключение проверки обновлений в репозитарии
  config.vm.box_check_update = false
  # Название машины
  config.vm.hostname = "server1"  
  # Настройка сетевого адаптера
  config.vm.network "private_network", ip: "192.168.56.11"
  # Название для машины для Vagrant и Virtualbox
  config.vm.define "server1"
  # Указываем провайдера, количество оперативной памяти и количество ядер
  config.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = "1"    
  end
end