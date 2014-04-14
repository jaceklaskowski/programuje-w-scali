Początki z jakimkolwiek językiem są trudne. Z językiem programowania również. Zakładam, że nie masz żadnego pojęcia o programowaniu, a coś podowiada Ci, że warto przeznaczyć na to trochę czasu. Wybieramy język programowania [Scala](http://scala-lang.org). O powodach później (może nawet wcale).

Do pracy z językiem Scala potrzebne są **wirtualna maszyna Javy** (ang. *JVM*) oraz na początku środowisko nazywane **Scala REPL**, co jest akronimem pierwszych liter angielskich słów, które odpowiadają polskim: wpisz wyrażenie (ang. *Read*), wykonaj je (ang. *Eval*), wyświetl (ang. *Print*) i tak na okrągło (ang. *Loop*). To będzie Twoje środowisko na kilka najbliższych dni, a może nawet i tygodni.

Pobierz **Java SE Development Kit 8** z wirtualną maszyną Javy ze [strony producenta Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). Należy zaakceptować warunki licencyjne produktu (ang. *Accept License Agreement*) i wcisnąć czerwoną strzałkę z nazwą paczki w wierszu stosownego systemu operacyjnego, np. Mac OS X x64 czy Windows x64. W przypadku wspomnianych systemów - Mac OS czy Windows - instalacja przebiega przez dwukrotne kliknięcie pobranej paczki i przejście kroków instalatora.

Kolejnym krokiem jest pobranie Scala REPL ze strony http://www.scala-lang.org/. Wciśnij przycisk [DOWNLOAD](http://www.scala-lang.org/download/) i wciśnij `Scala 2.10.4`. 2.10.4 jest najnowszą wersją języka (w tym i Scala REPL).

W zależności od systemu operacyjnego sposób instalacji będzie różny, ale we wszystkich przypadkach sprowadza się do rozpakowania pobranego pliku, np. `scala-2.10.4.tgz`, poleceniem `unzip` lub `tar` do dowolnego katalogu, który nazwiemy `SCALA_HOME`.

    jacek:~/apps
    $ tar -zxf ~/Downloads/scala-2.10.4.tgz
    jacek:~/apps
    $ ln -s scala-2.10.4 scala
    jacek:~/apps
    $ export SCALA_HOME=~/apps/scala
    jacek:~/apps
    $ export PATH=$SCALA_HOME/bin:$PATH

Od tej pory wydając polecenie `scala` pojawi się znak zachęty (ang. *prompt*) Scala REPL.

    $ scala
    Welcome to Scala version 2.10.4 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0).
    Type in expressions to have them evaluated.
    Type :help for more information.

    scala>
