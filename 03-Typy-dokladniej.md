Typy dokładniej - Dzień 4
=========================
Bazuję na specyfikacji języka Scala - [ScalaReference.pdf](http://www.scala-lang.org/files/archive/nightly/pdfs/ScalaReference.pdf) - rozdział 3. "Types".

Każda wartość w Scali ma określony typ - jawnie lub niejawnie. Scala posiada **mechanizm wnioskowania** (ang. *type inferencer*), który pozwala programiście zakładać typ niejawnie, jeśli takowy może być wyznaczony przez kontekst użycia wartości. Typ wyznacza zbiór dostępnych operacjach wartości.

Przyjrzyjmy się kilku znanym wartościom i sprawdźmy ich typ w Scali.

    scala> 0
    res1: Int = 0

Jak mogłaś zauważyć, wpisując `0` otrzymujemy odpowiedź od Scala REPL, że typem `0` jest `Int`, który występuje po nazwie wartości nazwanej `res1` i dwukropku.

Typ wartości w Scali, jeśli podany jawnie, występuje po dwukropku.

Istnieje inny sposób, aby dowiedzieć się o typie wartości w Scala REPL - korzystając z polecenia `:type`.

    scala> :type 0
    Int

Sprawdźmy inną wartość - napis `"Scala"`.

    scala> :t "Scala"
    String

Napis w Scali ma typ `String` i jest definiowany przez ciąg znaków między cudzysłowami.

**Ciekawostka** Baczne oko zauważy, że skorzystałem ze skrótu `:t`, który podobnie jak `:type`, służy do odczytania typu wartości w Scala REPL. Tak po prawdzie, wszystkie podciągi początkowe - `:t`, `:ty`, `:typ` oraz `:type` - pozwalają na wykonanie tego polecenia, gdyż środowisko pozwala na skróty, jeśli są jednoznaczne. W przypadku `:t` żadne inne polecenie, poza `:type`, nie rozpoczyna się od `:t`, więc jedynym kandydatem jest właśnie `:type`.

Sprawdźmy liczbę zmiennoprzecinkową `0.4`.

    scala> :t 0.4
    Double

Liczba składająca się z ciągu liczb oddzielonych pojedynczą kropką `.` jest typu `Double`.

Poza typami Int, String oraz Double istnieje jeszcze całkiem sporo innych, którymi zajmiemy się niebawem. Co jednak istotne to wymienione typy są **typami podstawowymi**. Do nich należą jeszcze (alfabetycznie): Boolean, Byte, Char, Float, Long, Short, Symbol, Tuple2, Unit.

*"I co z tego?"* - zapytasz. *"Po co mi znajomość typów?"*

Typ określa możliwe wartości - dziedzinę, z której możemy wybierać wartości, które możemy operować. Jeśli nasza metoda wymaga wartości typu `String`, to z pewnością nie chciałabyś, aby przekazano jej wartość typu `Int` lub `Byte` lub `Long` lub...i tak dalej. Jeśli typy nie są zgodne, chcielibyśmy, aby *ktoś* zadbał o poprawność naszego programowania i takim *kimś* jest **kompilator Scali**. Niezgodność typów kończy się błędem kompilacji naszej aplikacji.

Typ określa również dostępne metody - operacje, które możemy wykonywać na nim, a przez to i wartościach, które do niego należą. Czy nie chciałabyś móc zamienić "ala ma kota" na "Ala ma kota"?! Szczęśliwie, **standardowa biblioteka Scali** udostępnia metodę `def capitalize: String`, która ([za dokumentacją](http://www.scala-lang.org/api/current/#scala.collection.immutable.StringOps)) zwraca napis z pierwszą literą zamienioną na wielką.

    scala> "ala ma kota".capitalize
    res3: String = Ala ma kota

Od tej pory `res3` będzie napisem z pierwszą literą wielką (bez zmiany pozostałych).

Dostępne metody na typach standardowej biblioteki Scala opisane są w oficjalnym dokumencie [the documentation for the Scala standard library](http://www.scala-lang.org/api/current/#package). To jednak będzie przedmiotem naszej dalszej nauki języka Scala w kolejnym dniu.