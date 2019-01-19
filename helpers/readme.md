#### hosts2hosts:   
Скриптът архивира /etc/hosts като /etc/hosts.back, после премахва адресите от Unmedia
списъка от него (ако ги намери вътре), след което сваля актуалния списък Unmedia от
GitHub и го добавя към /etc/hosts. 
Скрипта трябва да се изпълнява като root и може да бъде конфигуриран като cron задача.

#### hosts2unbound:   
Скрипта взима от Github последната актуална версия на hosts.txt файла и генерира unmedia.conf
файл, който може да бъде включен в конфигурацията на [unbound](https://unbound.net/):   
`include: /path/to/unmedia.conf`   
Подходящо за рутери, на които е инсталиран unbound.   
Скрипта трябва да се изпълнява като root и може да бъде конфигуриран като cron задача.

#### hosts2dnsmasq:   
Като hosts2unbound ама за [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html).
Сваля hosts.txt файла, рестартира dnsmasq с опцията --addn-hosts=, за да зареди И hosts.txt
Подходящо за рутери, които използват dnsmasq (OpenWRT, DD-WRT, etc.)
Скрипта трябва да се изпълнява като root и може да бъде конфигуриран като cron задача.

#### hosts2mikrotik:
Изтегля от GitHub [unmedia.src](https://github.com/yradunchev/unmedia/blob/master/mikrotik/unmedia.src)
скрипт и го изпълнява, за да ъпдейтне статичните записи в dns на
Mikrotik. hosts2mikrotik трябва да се инсталира на Mikrotik рутера и да се
изпълнява през scheduler на определен интервал от време.
