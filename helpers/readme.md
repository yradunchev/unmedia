####hosts2unbound:
Скрипта взима от Github последната актуална версия на hosts.txt файла и генерира unmedia.conf
файл, който може да бъде включен в конфигурацията на [unbound](https://unbound.net/):   
`include: /path/to/unmedia.conf`   
Подходящо за рутери, на които е инсталиран unbound.   
Скрипта трябва да се изпълнява като root и може да бъде конфигуриран като cron задача.

