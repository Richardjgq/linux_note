# 重要目录

在 Linux 系统中，有几个目录是特别需要注意的，以下提供几个需要注意的目录，以及预设相关的用途：　

/etc：这个目录相当重要，如前所述，你的开机与系统数据文件均在这个目录之下，因此当这个目录被破坏，那你的系统大概也就差不多该死掉了！而在往后的文件中，你会发现我们常常使用这个目录下的 /etc/rc.d/init.d 这个子目录，因为这个 init.d 子目录是开启一些 Linux 系统服务的 scripts （可以想成是批次檔 ）的地方。而在 /etc/rc.d/rc.local 这个文件是开机的执行档。　

/bin, /sbin, /usr/bin, /usr/sbin：这是系统预设的执行文件的放置目录，例如 root 常常使用的 userconf, netconf, perl, gcc, c++ 等等的数据都放在这几个目录中，所以如果你在提示字符下找不到某个执行档时，可以在这四个目录中查一查！其中， /bin, /usr/bin 是给系统使用者使用的指令，而 /sbin, /usr/sbin 则是给系统管理员使用的指令！ 

/usr/local：这是系统预设的让你安装你后来升级的套件的目录。例如，当你发现有更新的 Web 套件（如 Apache ）可以安装，而你又不想以 rpm 的方式升级你的套件，则你可以将 apache 这个套件安装在 /usr/local 底下。安装在这里有个好处，因为目前大家的系统都是差不多的，所以如果你的系统要让别人接管的话，也比较容易上手呀！也比较容易找的到数据喔！因此，如果你有需要的话，通常我都会将 /usr/local/bin 这个路径加到我的 path 中。

/home：这个是系统将有账号的人口的家目录设置的地方。 　

/var：这个路径就重要了！不论是登入、各类服务的问题发生时的记录、以及常态性的服务记录等等的记录目录，所以当你的系统有问题时，就需要来这个目录记录的文件数据中察看问题的所在啰！而 mail 的预设放置也是在这里，所以他是很重要的 。

/usr/share/man, /usr/local/man： 这两个目录为放置各类套件说明档的地方，例如你如果执行 man man，则系统会自动去找这两个目录下的所有说明文件。

