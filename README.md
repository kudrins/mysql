## Домашнее задание Репликация mysql

### Описание домашнего задания
```
- Dump базы bet.dmp развернуть на мастере и настроить репликацию таблиц:
  bookmaker, competition, market, odds, outcome.
- Настроить GTID репликацию
- VMs разворачивается в среде VMware vSphere 7 из шаблона Centos 8 Stream
  
Файлы:

- network.yml:           ansible playbook развертывания VMs,
                         установки и настройки percona-server
- vars.yml:              переменные для создания и натройки VMs
- host:                  inventory
- mysql1.cnf:            VM mysql1 /etc/my.cnf
- mysql2.cnf:            VM mysql2 /etc/my.cnf
- bet.dmp:               дамп базы 

в скриншотах:
- screens\ansible.jpg:   работа ansible-playbook

mysql1:   
- screens\myqsl1_1.jpg:  задание пароля ползователю mysql: root
                         проверка server_id
                         проверка gtid_mode
						 
- screens\myqsl1_2.jpg:  show master status;
                         создание пользоватнля mysql: repl
                         задание прав пользователю repl
                         создание базы: bet	
						 
- screens\myqsl1_3.jpg:  восстановление базы bet из дампа
                         просмотр таблиц базы bet    
                         дампим базу для последующего залива на mysql2,
                         игнорируя заданные таблицы
                         копируем дамп на mysql2

mysql2:           
- screens\myqsl2_1.jpg:  задание пароля ползователю mysql: root
                         проверка server_id
                         заливаем дамп базы с mysql1
						 
- screens\myqsl2_2.jpg:  смотрим базу bet, убеждаемся, что заданных таблиц нет
                         подключаем и запускаем реплику 
						 
- screens\myqsl2_3.jpg:  смотрим статус реаликации        

mysql1:  
- screens\myqsl1_4.jpg:  создаем базу и таблицу на mysql1
mysql2:            
- screens\myqsl2_4.jpg:  убеждаемся, что база с таблицей реплицировались          
 
