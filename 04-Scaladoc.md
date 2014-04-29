Scaladoc - Dzień 5
==================
W poprzednim dniu omówiliśmy znaczenie typów, które określają dostępne wartości oraz metody, które operują na nich.

Język programowania nie byłby użyteczny bez gotowego zbioru typów, które pozwalają programiście - Tobie - wyrazić swoje pomysły programem komputerowym. Zbiór typów w języku programowania nazywamy biblioteką standardową i można w niej oczekiwać typów podstawowych (jak String, Int, Double), obsługi wejścia-wyjścia (z zapisem do i odczytem z pliku lub zasobu sieciowego), mechanizmu wątków, kolekcji, strumieni, itp.

Poznanie zawartości biblioteki standardowej dowolnego języka programowania jest krokiem koniecznym, aby "wejść" w język. Scala nie jest wyjątkiem. Spędzisz całe godziny wertując dokumentację biblioteki standardowej, bo w przeciwnym przypadku będziesz poświęcała czas na tworzenie typów własnoręcznie, kiedy są one już gotowe do użycia.

**Zapamiętaj** Nauka języka Scala to dogłębne poznanie standardowej biblioteki języka.

Standardowa biblioteka języka Scala opisana jest w dokumentacji nazywanej **ScalaDoc**. Opisuje ona dostępne typy, metody i inne elementy, z których programista może skorzystać do pisania programów w Scali.

Dokumentacja standardowej biblioteki języka Scala dostępna jest pod adresem http://www.scala-lang.org/api.

Po lewej stronie dokumentacji znajdziesz dostępne pakiety (mechanizm grupowania typów, o którym później) oraz ich zawartość - typy. Klikając nazwę pakietu, np. `scala`, przejdziemy do jego opisu w części po prawej stronie. Podobnie z kliknięciem typu, które otworzy jego opis po prawej.

Zapoznaj się ze wszystkimi typami w pakiecie scala, który dostępny jest bez jakichkolwiek dodatkowych działań z Twojej strony.

Dla uatrakcyjnienia naszej dzisiejszej nauki, weźmy "na tapetę" typ [scala.Int](http://www.scala-lang.org/api/current/#scala.Int). Jest to ten znany i lubiany `Int`, z którym mieliśmy do czynienia już wcześniej, a przez fakt przynależności do pakietu `scala` nie wymagał dodatkowych czynności, aby z niego korzystać - po prostu był dostępny.

Kiedy wpiszesz dowolną liczbę całkowitą w Scala REPL, np. `5`, otrzymasz pojedynczą wartość typu `Int`.

    scala> 5
    res2: Int = 5

Od tej pory `res2` jest reprezentantem typu `Int` o ustalonej wartości `5`. Podobnie jak wartość `5` jest symboliczną reprezentacją liczby pięć - zwanym **literałem całkowitym** - tak od tej pory `res2` jest reprezentantem typu `Int` o wartości `5`.

Sprawdź dokumentację dla typu [scala.Int](http://www.scala-lang.org/api/current/#scala.Int) i wybierz jedną z wielu metodę, którą oferuje, np. `!=`, `%`, `&`, `*` lub coś bardziej "opisowego", np. `toChar()`.

    scala> 5 != 5
    res3: Boolean = false

    scala> 5 % 7
    res4: Int = 5

    scala> 7 % 5
    res5: Int = 2

    scala> 5 ^ 6
    res6: Int = 3

    scala> 5 & 6
    res7: Int = 4

    scala> 5 * 6
    res8: Int = 30

    scala> 65.toChar
    res9: Char = A

    scala> 97.toChar
    res10: Char = a

Dzięki dostępności biblioteki standardowej języka Scala nie musisz pisać wspomnianych metod, a korzystać z nich, bo są Ci dane. To część języka Scala i ScalaDoc jest dokumentacją, w której znajdziesz, co masz (a czego nie musisz pisać od zera).

W kolejnym dniu zapoznasz się bliżej z mechanizmem działania metod w języku Scala.