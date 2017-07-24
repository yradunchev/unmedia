Списък на сайтове, произвеждащи и разпространяващи фалшиви новини на български език.

Списъкът е във формат на hosts файл, това дава възможност да бъде добавен към hosts файла на всеки компютър, в резултат на което достъпът до сайтовете в списъка ще бъде ефективно блокиран за *всеки* потребител и браузър на компютъра.

- За Linux: /etc/hosts   
- За Windows: %SystemRoot%\System32\drivers\etc\hosts   
- За Mac OS: /etc/hosts (symbolic link към файла /private/etc/hosts)   
- За Android: /etc/hosts (symbolic link към файла /system/etc/hosts)   
- За iOS: /etc/hosts (symbolic link към файла /private/etc/hosts)   

_**ВНИМАНИЕ**_: съдържанието на hosts.txt следва да се добави _**СЛЕД**_ последния ред на съществуващия hosts файл!

Списъка отразява единствено моето лично мнение и е съставен за моя лична употреба.

Използвани източници:
- [BG-List-Fake-News.pdf](https://app.box.com/s/1467cn3s3n0l45zfqdvxxjqr13pfq28a) на Борис Луканов

---
За добавка към Google Chrome която блокира сайтовете от списъка виж: [unmedia_chrome](https://github.com/yradunchev/unmedia_chrome)   

---
Папката helpers съдържа скриптове, които преработват hosts.txt файла в различни формати за
използване с различни приложения.

**helpers/hosts2unbound:**

Скрипта взима от Github последната актуална версия на hosts.txt файла и генерира unmedia.conf файл,
който може да бъде включен в конфигурацията на [unbound](https://unbound.net/):   
      (include: /path/to/unmedia.conf)   
Подходящо за рутери, на които е инсталиран unbound.   
Скрипта трябва да се изпълнява като root и може да бъде конфигуриран като cron задача.

