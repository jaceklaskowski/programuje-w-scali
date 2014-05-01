Metody - Dzień 6
================
Scala jest językiem obiektowo-funkcyjnym, w którym paradygmat programowania obiektowego miesza się z funkcyjnym (ku szczęśliwości programistów).

Wszystko w Scali jest obiektem, który ma swój typ. Typ posiada metody, które oferują pewną funkcjonalność. Dokumentacja scaladoc typu opisuje dostępne metody.

Weźmy za przykład typ [scala.collection.Seq](http://www.scala-lang.org/api/current/#scala.collection.Seq$).

Utworzenie wartości `Seq` jest możliwe za pomocą metody specjalnej `def apply[A](elems: A*): Seq[A]` w obiekcie `Seq`.

scala> Seq.apply(1, 2, 3)
res0: Seq[Int] = List(1, 2, 3)

Scala udostępnia *lukier składniowy*, który pozwala na krótszy zapis powyższego wywołania metody `apply`.

    scala> Seq(1, 2, 3)
    res1: Seq[Int] = List(1, 2, 3)

**Pamiętaj** Wywołanie `Typ(parametry)` odpowiada wywołaniu `Typ.apply(parametry)`.

Obie nazwy `res0` oraz `res1` odpowiadają sekwencji liczb całkowitych `1`, `2` i `3`.

Scaladoc dla typu [scala.collection.Seq](http://www.scala-lang.org/api/current/#scala.collection.Seq) udostępnia wiele innych metod, np. `apply(idx: Int): A`, `def length: Int` czy `def count(p: (A) => Boolean): Int`.

Pamiętasz, że `apply(...)` to po prostu `(...)`, a więc wykonanie `apply(idx: Int): A` na `res0` będzie po prostu:

    scala> res0(0)
    res2: Int = 1

    scala> res0(1)
    res3: Int = 2

Obliczenie długości sekwencji z `def length: Int`:

    scala> res0.length
    res4: Int = 3

Zliczenie elementów spełniających warunek z `def count(p: (A) => Boolean): Int`:

    scala> res0.count(e => e % 2 != 0)
    res6: Int = 2

Nie spodziewam się zrozumienia ostatniego przykładu, bo zawiera wykonanie `count` z...*literałem funkcyjnym*. Liczę wyłącznie na obycie się z takimi konstrukcjami przez częstszy kontakt z nimi. Będzie o nich niebawem.