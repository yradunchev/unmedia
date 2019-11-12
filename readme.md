Списък на сайтове, произвеждащи и възпроизвеждащи фалшиви новини на български език.

Списъкът е във формата на hosts файл, това дава възможност да бъде добавен към hosts файла на всеки
компютър, в резултат на което достъпът до сайтовете в списъка ще бъде ефективно блокиран за всеки
потребител и браузър на компютъра.

- За Linux: /etc/hosts   
- За Windows: %SystemRoot%\System32\drivers\etc\hosts   
- За Mac OS: /etc/hosts (symbolic link към файла /private/etc/hosts)   
- За Android: /etc/hosts (symbolic link към файла /system/etc/hosts)   
- За iOS: /etc/hosts (symbolic link към файла /private/etc/hosts)   

Списъка отразява единствено моето лично мнение и е съставен за моя лична употреба.

_**ВНИМАНИЕ**_: съдържанието на hosts.src следва да се добави _**СЛЕД**_ последния ред на
съществуващия hosts файл!

Папката helpers съдържа скриптове, които преработват hosts.txt файла в различни формати за
използване с различни приложения.

hosts2hosts:   

Скриптът архивира /etc/hosts като /etc/hosts.back, после премахва адресите от Unmedia
списъка от него (ако ги намери вътре), след което сваля актуалния списък Unmedia от
GitHub и го добавя към /etc/hosts.
Скрипта трябва да се изпълнява като root и може да бъде конфигуриран като cron задача.

helpers/hosts2unbound:

Скрипта взима от Github последната актуална версия на hosts.txt файла и генерира unmedia.conf файл,
който може да бъде включен в конфигурацията на unbound (include: /path/to/unmedia.conf). Подходящо
за рутери, на които е инсталиран unbound. Скрипта трябва да се изпълнява като root и може да бъде
конфигуриран като cron задача.

helpers/hosts2dnsmasq

Като hosts2unbound ама за dnsmasq.
Сваля hosts файла, рестартира dnsmasq с опцията --addn-hosts=, за да зареди И hosts.txt
Подходящо за рутери, които използват dnsmasq (OpenWRT, DD-WRT, etc.)

helpers/hosts2mikrotik:   

Изтегля от GitHub
[unmedia.src](https://github.com/yradunchev/unmedia/blob/master/mikrotik/unmedia.src)
скрипт и го изпълнява, за да ъпдейтне статичните записи в dns на
Mikrotik. hosts2mikrotik трябва да се инсталира на Mikrotik рутера и да се
изпълнява през scheduler на определен интервал от време. Не е препоръчително да
използвате Mikrotik за блокиране на сайтове заради ефекта върху
производителността на рутера. Инвестирайте в [PiHole](https://pi-hole.net/).

_Как да инсталирате hosts2mikrotik на рутера си и да го подготвите за работа:_   
На конзолата на Mikrotik изпълнете следните команди:
```
/ system script add name=unmedia
/ system script add name=hosts2mikrotik
/ system script edit hosts2mikrotik source
```
копирайте съдържанието на
[hosts2mikrotik](https://github.com/yradunchev/unmedia/blob/master/helpers/hosts2mikrotik.scr)
и го пейстнете в конзолата, запишете с ctrl+o. Стартирайте hosts2mikrotik:
```
/ system script run hosts2mikrotik
```
Може да проверите дали са добавени статичните dns записи:
```
/ ip dns static print
```
Можете да добавите скрипта в scheduler:
```
/ system scheduler add interval=7d name="unmedia-update" on-event=hosts2mikrotik
```

Използвани източници:
- https://app.box.com/s/1467cn3s3n0l45zfqdvxxjqr13pfq28a

