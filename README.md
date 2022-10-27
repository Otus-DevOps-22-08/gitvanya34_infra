# gitvanya34_infra
gitvanya34 Infra repository

1)Подключения к someinternalhost в одну команду из вашего рабочего устройства ssh -i ~/.ssh/id_rsa -A -t gitvanya34@51.250.2.97 ssh 10.128.0.18 или ssh -A -t gitvanya34@51.250.2.97 ssh 10.128.0.18
2)Предложить вариант решения для подключения из консоли при помощи
команды вида ssh someinternalhost из локальной консоли рабочего
устройства.
2.1) прописываем конфиг файл в папке .ssh:
Host *
ForwardAgent yes

Host bastion
HostName 51.250.72.36
User gitvanya34

Host someinternalhost
HostName 10.128.0.18
User gitvanya34
ProxyCommand ssh -t -A bastion -W %h:%p
-
Затем вызываем в консоли ssh someinternalhost

bastion_IP = 51.250.2.97
someinternalhost_IP =10.128.0.18
