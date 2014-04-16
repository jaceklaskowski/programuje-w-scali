Środowisko - Dzień 1
====================
Początki nie zawsze należą do najmilszych momentów w naszym życiu. Z nauką programowania jest podobnie. Zakładam, że nie masz jakiegokolwiek pojęcia o programowaniu, a coś podowiada Ci, że warto przeznaczyć na to trochę czasu. Wybieramy język programowania [Scala](http://scala-lang.org). O powodach później.

Do pracy z językiem Scala potrzebne są **wirtualna maszyna Javy** (ang. *JVM*) oraz (na początku) środowisko nazywane **Scala REPL**. REPL jest akronimem pierwszych liter angielskich słów, które odpowiadają polskim: wpisz wyrażenie (ang. *Read*), wykonaj je (ang. *Eval*), wyświetl (ang. *Print*) i tak na okrągło (ang. *Loop*). Jest to najczęściej pierwsze środowisko pracy programisty języka Scala i to również będzie Twoje środowisko na kilka najbliższych tygodni. Nie ma nic przyjemniejszego niż "odpalić" Scala REPL i móc natychmiast przetestować swój pomysł na kolejną wspaniałą aplikację.

Pobierz **Java SE Development Kit 8** z wirtualną maszyną Javy ze [strony producenta Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). Zanim paczka znajdzie się na Twoim komputerze, należy zaakceptować warunki licencyjne produktu (ang. *Accept License Agreement*) i wcisnąć komórkę z czerwoną strzałką i nazwą paczki w wierszu odpowiadającemu systemowi operacyjnemu, z którego korzystasz, np. Mac OS X x64 czy Windows x64. W moim przypadku będzie to Mac OS X x64 i takie też znajdziesz tutaj zrzuty ekranu i wycinki z linii poleceń. W przypadku wspomnianych systemów - Mac OS czy Windows - instalacja przebiega przez dwukrotne kliknięcie pobranej paczki i przejście kroków instalatora.

Poprawna instalacja pozwoli Ci wykonać polecenie `java -version` z poziomu linii poleceń.

    $ java -version
    java version "1.8.0"
    Java(TM) SE Runtime Environment (build 1.8.0-b132)
    Java HotSpot(TM) 64-Bit Server VM (build 25.0-b70, mixed mode)

Kolejnym krokiem jest pobranie paczki dystrybucyjnej Scali ze strony http://www.scala-lang.org/. Wciśnij przycisk [DOWNLOAD](http://www.scala-lang.org/download/), a następnie wciśnij `Scala 2.10.4`. Wersja 2.10.4 jest najnowszą wersją języka Scala, która dostarcza m.in. środowisko Scala REPL.

Bez względu na system operacyjny, z którego korzystasz, sposób instalacji będzie podobny - sprowadza się do rozpakowania pobranego pliku, np. `scala-2.10.4.tgz`, poleceniem `unzip` lub `tar` do wybranego katalogu, którego będziemy od tej pory wskazywać zmienną środowiskową `SCALA_HOME`.

    jacek:~/apps
    $ tar -zxf ~/Downloads/scala-2.10.4.tgz
    jacek:~/apps
    $ ln -s scala-2.10.4 scala
    jacek:~/apps
    $ export SCALA_HOME=~/apps/scala
    jacek:~/apps
    $ export PATH=$SCALA_HOME/bin:$PATH

Od tej pory, kiedykolwiek wydasz polecenie `scala` pojawi się znak zachęty (ang. *prompt*) Scala REPL.

    $ scala
    Welcome to Scala version 2.10.4 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0).
    Type in expressions to have them evaluated.
    Type :help for more information.

    scala>

Gratulacje! Właśnie przygotowałaś swoje nowe miejsce pracy z językiem Scala. Znajomość tego języka pozwoliłaby Ci skorzystać z dobrodziejstw środowiska REPL, ale nie trzymając Cię zbyt długo, zanim nauczysz się Scali, wpisz dowolne wyrażenie matematyczne, które pamiętasz z lekcji matematyki (tylko, proszę, niech to będzie matematyka na poziomie klasy 6 podstawówki - bez różniczek proszę!)

Mała podpowiedź: po wprowadzeniu wyrażenia zatwierdzasz je wciskając przycisk ENTER.

    scala> 1+1
    res0: Int = 2

Spróbuj kolejne. Niech będzie trochę dłuższe.

    scala> 1+2*3-4%5

Ciekawi mnie, czy znasz wynik tego wyrażenia? 1? 3? 9? Sprawdź!

    scala> 1+2*3-4%5
    res1: Int = 3

Jak zapewne pamiętasz z lekcji matematyki (i trudno o tym zapomnieć po tych wszystkich latach wyrzeczeń), poszczególne składowe powyższego wyrażenia można pogrupować nawiasami. Za pomocą nawiasów nadajesz większą ważność operacji matematycznej, która w przeciwnym przypadku byłaby mniejszego znaczenia i obliczana później.

    scala> (1 + (2 * 3)) - (4 % 5)
    res2: Int = 3

Jak mogłaś zauważyć powyżej, do powyższego wyrażenia dodałem nie tylko nawiasy, ale i odstępy (spacje) między jego elementami, co wygląda zgrabniej, a i być może bardziej znajomo.

Pozwól sobie na chwilkę ze Scala REPL i sprawdź, jak bardzo Twoja znajomość matematyki pozwala Ci na poprawną pracę w tym środowisku. Ten moment ma oswoić Cię ze Scala REPL, abyś nabrała pewności przed kolejnymi zadaniami.

Po zakończonej pracy, warto po sobie posprzątać. Wyjście ze Scala REPL sprowadza się do wydania polecenia `:quit`.

    scala> :quit

Ta...dam! Właśnie zakończyłaś swój pierwszy dzień z programowaniem w Scali korzystając ze środowiska Scala REPL. Gratulacje postępów!
