# Домашнее задание к занятию "3.1. Работа в терминале, лекция 1"

1. Установите средство виртуализации [Oracle VirtualBox](https://www.virtualbox.org/).
   * *установлен*


2. Установите средство автоматизации [Hashicorp Vagrant](https://www.vagrantup.com/).
   * *установлен*


3. В вашем основном окружении подготовьте удобный для дальнейшей работы терминал. Можно предложить:

    * Windows Terminal в Windows
       * *установлен*
      


4. С помощью базового файла конфигурации запустите Ubuntu 20.04 в VirtualBox посредством Vagrant:
 
	* *вм создана и запущена*
   

5. Ознакомьтесь с графическим интерфейсом VirtualBox, посмотрите как выглядит виртуальная машина, которую создал для вас Vagrant, какие аппаратные ресурсы ей выделены. Какие ресурсы выделены по-умолчанию?
   * 2 процессора, 1 ГБ оперативной памяти, 64 ГБ жёсткий диск, 4 МБ вдеопамять, 1 гигабитный сетевой адаптер.*
   

6. Ознакомьтесь с возможностями конфигурации VirtualBox через Vagrantfile: [документация](https://www.vagrantup.com/docs/providers/virtualbox/configuration.html). Как добавить оперативной памяти или ресурсов процессора виртуальной машине?
   * Добавить в вагрант файла следующие строки:

     * config.vm.provider "virtualbox" do |v|
       * v.memory = 2024
       * v.cpus = 4
     * end


7. Команда `vagrant ssh` из директории, в которой содержится Vagrantfile, позволит вам оказаться внутри виртуальной машины без каких-либо дополнительных настроек. Попрактикуйтесь в выполнении обсуждаемых команд в терминале Ubuntu.

8. Ознакомиться с разделами `man bash`, почитать о настройках самого bash:
    * какой переменной можно задать длину журнала `history`, и на какой строчке manual это описывается?
      * *man bash | grep -n -i -2 HISTFILESIZE*
      * *586:       HISTFILESIZE   The maximum number of lines contained in the history file*
    * 
    * что делает директива `ignoreboth` в bash?
      * *ignoreboth is shorthand for ignorespace(lines which begin with a space character are not saved in the history list) and ignoredups(lines matching the previous history entry to not be saved).*
    * 
9. В каких сценариях использования применимы скобки `{}` и на какой строчке `man bash` это описано?
   * *списки:*     
   * *197:       { list; }*
   
10. Основываясь на предыдущем вопросе, как создать однократным вызовом `touch` 100000 файлов? А получилось ли создать 300000? Если нет, то почему?
    * *touch {1..100000}*
    
    А получилось ли создать 300000? Если нет, то почему?
    * *Не получилось*
    * *-bash: /usr/bin/touch: Argument list too long*
    

11. В man bash поищите по `/\[\[`. Что делает конструкция `[[ -d /tmp ]]`
    * *Конструкция [[ -d /tmp ]] возвращает истину если директория /tmp существует.*
        

12. Основываясь на знаниях о просмотре текущих (например, PATH) и установке новых переменных; командах, которые мы рассматривали, добейтесь в выводе type -a bash в виртуальной машине наличия первым пунктом в списке:

    * *dbaksheev@dbaksheev:/mnt/c/Users/usr$ type -a bash*
    * *bash is /usr/bin/bash*
    * *bash is /bin/bash*
    * *dbaksheev@dbaksheev:/mnt/c/Users/usr$ mkdir /tmp/homework*
    * *dbaksheev@dbaksheev:/mnt/c/Users/usr$ ln -s /usr/bin/bash /tmp/homework*
    * *dbaksheev@dbaksheev:/mnt/c/Users/usr$ export PATH=/tmp/homework:$PATH*
    * *dbaksheev@dbaksheev:/mnt/c/Users/usr$ type -a bash*
    * *bash is /tmp/homework/bash*
    * *bash is /usr/bin/bash*
    * *bash is /bin/bash*

 
14. Чем отличается планирование команд с помощью `batch` и `at`?
    * *Команда at предназначена для выполнения задач в заданное время, а команда batch предназанчена для запуска задач, когда уровень средней загрузки падает ниже 1.5, либо значения указанного в atd.*

