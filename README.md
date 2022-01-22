
# Домашнее задание к занятию "5.2. Применение принципов IaaC в работе с виртуальными машинами"


## Задача 1

- Опишите своими словами основные преимущества применения на практике IaaC паттернов.  
Непрерывная интеграция позволяет быстро находить ошибки в коде за счет постоянного тестирования небольшими объемами. Непрерывная доставка также позволяет легко исправить или откатиться на недавнее состояние в случае ошибок. 
- Какой из принципов IaaC является основополагающим?  
Получение стабильного и предсказуемого результата каждый раз при использовании(запуске) кода. 

## Задача 2

- Чем Ansible выгодно отличается от других систем управление конфигурациями?  
Его основные преимущества это использование SSH инфраструктуры без установки дополнительного окружения, а также наличие большого количества модулей.  
- Какой, на ваш взгляд, метод работы систем конфигурации более надёжный push или pull?  
Думаю тот, что лучше протестирован и проверен в каком-то конкретном окружении :) Но в целом управление push мне кажется более надёжным. В этом случае одновременно получаем нужные конфигурации на машинах в нужный момент времени. 

## Задача 3

Установить на личный компьютер:

- VirtualBox  
```
Графический интерфейс VirtualBox
Версия 6.1.30 r148432 (Qt5.6.2)
```
- Vagrant  
```
C:\WINDOWS\system32>vagrant -v
Vagrant 2.2.19
```
- Ansible  
```
yuriy@k55vd ~
$  ansible --version
ansible 2.8.4
  config file = /etc/ansible/ansible.cfg
```
*Приложить вывод команд установленных версий каждой из программ, оформленный в markdown.*

## Задача 4 (*)

Воспроизвести практическую часть лекции самостоятельно.

- Создать виртуальную машину.
- Зайти внутрь ВМ, убедиться, что Docker установлен с помощью команды
```
docker ps
```

К сожалению выполнить это задание не удалось.
Старт vagrant зависает на этапе ssh
У меня win 10. Установил virtualbox, в ней поднял ubuntu 18.04 server, в ubuntu установил virtualbox+vagrant+ansible. При попытке запустить “vagrant up” прогресс зависает на этапе настройки ssh. В чате telegram видел похожие проблемы у ребят, но решения не увидел.

При установке через cygwin ошибка: c:\HashiCorp\Vagrant\VM>vagrant provision
==> server1.netology: Running provisioner: ansible…
Windows is not officially supported for the Ansible Control Machine.
Please check docs.ansible.com...quirements
Vagrant gathered an unknown Ansible version:

and falls back on the compatibility mode ‘1.8’.

Alternatively, the compatibility mode can be specified in your Vagrantfile:
www.vagrantup.com...ility_mode
server1.netology: Running ansible-playbook…
The Ansible software could not be found! Please verify
that Ansible is correctly installed on your host system.

Т.е ansible система не видит. Конфиг менял, в строке  поправил
```Vagrant.configure(2) do |config|
  config.vm.synced_folder "C:/cygwin64/etc/ansible", "/vagrant", type: "smb", disabled: false, smb_password: "password", smb_username: "username"
  ```
  Ошибка та же
