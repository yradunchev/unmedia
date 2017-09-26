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
