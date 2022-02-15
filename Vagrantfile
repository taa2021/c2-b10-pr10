# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Требование задания п.4
  # Создать Vagrantfile, при использовании которого будет создаваться ВМ под управлением Ubuntu 18.04.
  config.vm.box = "hashicorp/bionic64"

  # Пусть будет (двустороннее взаимодействие хоста и виртуальной машины)
  config.vm.synced_folder "./sync2vm", "/vagrant_data"

  # Требование задания п.6:
  # Дополнить Vagrantfile командой копирования созданного нами пустого файла на файловую 
  # систему созданной машины (в будущем при реальной работе с тестовым окружением, 
  # разработчики будут вместо этого пустого файла копировать на создаваемую ВМ 
  # свои скрипты и запускать их там).
  config.vm.provision "file", source: "./cp2vm", destination: "$HOME/vagrant_scripts"


  # Требование задания п.5:
  # Настроить Vagrantfile таким образом, чтобы на эту машину при ее создании 
  # установились python3- и python3-pip-пакеты, а также Python-библиотеки psycopg2 
  # (для подключения к PostgreSQL СУБД) и Django (для работы с фронтендом).
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "vm-deploy.yml"
  end

  # Требование задания п.5 - выполнены ранее, не нужны (уже установлены), но так тоже можно было бы
  # config.vm.provision "shell", inline: <<-SHELL
  #   echo "Don't need - already installed via OS packages (ansible)"
  #   pip3 install django psycopg2
  # SHELL
end
