Literały funkcyjny - Dzień 7
============================
Pamiętasz metodę `def count(p: (A) => Boolean): Int` z [scala.collection.Seq](http://www.scala-lang.org/api/current/#scala.collection.Seq)? Nie byłbym wcale zdziwiony odpowiedzią *"Nie"*. I nie ma to większego znaczenia (!)

Zakładam jednak, że potrafisz określić typ parametru wejściowego `p` metody `count`. Przypomnę, że typ zawsze występuje po prawej stronie dwukropka. Znasz odpowiedź? Jaki to będzie typ?

Typem parametru wejściowego `p` metody `count` jest `(A) => Boolean`, czyli *funkcja* pojedynczego parametru typu `A`, której typem wartości zwracanej jest `Boolean`. Proste?! Zacznijmy od początku.

W rozdziale 3. "Types" specyfikacji języka Scala, typ określony jest dwojako:

    Type ::= FunctionArgTypes '=>' Type
           | InfixType [ExistentialClause]

Nas interesuje przypadek pierwszy - `FunctionArgTypes '=>' Type`, w którym "separatorem" między opisem parametrów wejściowych a typem wartości zwracanej z funkcji jest `=>`.

Zwróć uwagę, że typ wartości zwracanej z funkcji jest ponownie `Type`, czyli może to być ponownie funkcja i...końca nie widać. Ma to niebagatelne skutki w programowaniu w Scali i czym prędzej zapamiętasz o tej cesze Scali, tym szybciej zasmakujesz najsmaczniejszych kawałków języka. To jest kwintesencja programowania funkcyjnego, która mówi, że funkcja nie tylko może przyjmować funkcje, ale również je zwracać. Zapis `Type ::= FunctionArgTypes '=>' Type` właśnie o tym mówi, a warunkiem końcowym owej rekurencji w definiowaniu typów jest warunek drugi `InfixType [ExistentialClause]`.

Na potrzeby naszej nauki Scali lewą stronę `FunctionArgTypes '=>' Type` - `FunctionArgTypes`, potraktujemy bardzo zgrubnie i założymy, że jest to nic innego niż seria `ParamType` między nawiasami okrągłymi `(` i `)`, które oddzielone są między sobą przecinkiem `,`.

    FunctionArgTypes = '(' [ ParamType {',' ParamType } ] ')'

gdzie `ParamType` jest dowolnym typem, który zechciałabyś użyć w definicji swojej funkcji.

W ten sposób zdefiniowaliśmy **typ funkcyjny**, który określa typ swoich wartości.

**Pamiętaj** Typ jest zbiorem wartości, a każda wartość w Scali ma swój typ.

Sprawdźmy naszą znajomość tematu i zdefiniujmy kilka typów funkcyjnych. Co proponujesz na początek? Może typ funkcyjny przeprowadzający wartości typu `Int` na `Boolean`?

    Int => Boolean

A jakby wyglądał typ funkcyjny przeprowadzający pary `(String, Int)` na `String`?

    (String, Int) => String

A czy potrafisz opisać typ funkcyjny przyjmujący inny typ funkcyjny i przeprowadzający go na kolejny typ funkcyjny?

    (String, Int) => String => Int => Boolean

I tu ważna informacja (jakby ich było mało dzisiaj) - siła wiązania `=>` jest od prawej do lewej, więc powyższy zapis jest tłumaczony przez kompilator Scali na:

    ((String, Int) => (String => (Int => Boolean)))

który czytamy: typ funkcyjny akceptuje wartości typu `(String, Int)` i przenosi je na wartości typu `(String => (Int => Boolean))`, które są również typu funkcyjnego, którego wartości akceptują na wejściu wartości typu `String` i przenoszą je na wartości typu `Int => Boolean`, które ponownie są typu funkcyjnego, którego wartości typu Int przenoszone są na odpowiednie wartości typu `Boolean`. Proste? Niedługo będzie. Spokojnie.

Jakby tego było mało, w Scali typ funkcyjny jest skrótem dla typów z metodą `apply` (mieliśmy z nią do czynienia wcale nie tak dawno temu). Zapis `(T1, ..., Tn) => U` jest skrótem dla typu `scala.Function*n*[T1, ..., Tn, U]`, gdzie `n` należy do przedziału `0 - 9`.

Wszystko to dotyczyło typu funkcyjnego, a **literał funkcyjny** jest niczym innym jak zapisem wartości takiego typu, czyli `(s: String) => 5`, który jest typu `String => Int` i po wpisaniu do Scala REPL przedstawia się następująco:

    scala> (s: String) => 5
    res3: String => Int = <function1>

`res3` jest od tej pory funkcją pojedynczego argumentu typu `String`, która zwraca wartość typu `Int`.

Pewnie zastanawiasz się, jak możnaby wywołać tak zdefiniowaną funkcję?! Wystarczy podać jej nazwę i zestaw parametrów w nawiasach zwykłych:

    scala> res3("napis")
    res4: Int = 5

Jak można było się domyśleć, każdy napis jest przeprowadzany na wartość `5`, więc jakąkolwiek wartość wejściową podasz, znam wynik.

Wracając do naszego przykładu z początku - `def count(p: (A) => Boolean): Int`. Już rozumiesz ten zapis? Wiesz, że definiuje metodę `count`, która przyjmuje na wejściu funkcję `p: A => Boolean`, która przyjmuje typ `A` i zwraca `Boolean`, a całość `Int`?

**Pamiętaj** Typ wartości, jeśli określony jawnie, występuje po dwukropku.

Mógłbyś zapytać skąd bierze się ów typ `A`. Jest to typ elementów przechowywanych w kolekcji, która pozwala na określenie typu przy jej tworzeniu. Nie jest to na tę chwilę istotne, a warte odnotowania jest to, że jest typem dowolnym, ale jednakowym dla wszystkich elementów kolekcji.

Zdefiniuj sekwencję `Int`ów.

    scala> Seq(1,2,3)
    res5: Seq[Int] = List(1, 2, 3)

A teraz wykonaj na `res5` metodę `def count(p: (A) => Boolean): Int`.

    scala> res5.count((n: Int) => true)
    res6: Int = 3

Jedyną rzeczą, z którą mogłabyś mieć trudność, mogło być określenie wartości typu `Boolean`. Istnieją dwie, które odpowiadają wartościom `boolean` z języka Java - `true` oraz `false`. Mając tę wiedzę, z pewnością łatwiej czyta się powyższy przykład.

Scala pozwala na opuszczanie deklarowania typu jawnie, kiedy typ może zostać wywnioskowany z kontekstu. W powyższym przykładzie, parametry sekwencji są typu `Int` i ta informacja jest znana kompilatorowi, więc nie jest konieczne określenie typu parametru wejściowego funkcji `(n: Int) => true` wewnątrz `count`. Wystarczyłoby:

    scala> res5.count(n => true)
    res7: Int = 3

I aż mnie świerzbi, aby kontynuować temat upraszczania, ale wystarczy na dzisiaj. Zrelaksuj się. Jest jeszcze wiele poznawania przed nami, więc nie ma co się forsować. Pora oderwać się od komputera i zaczerpnąć świeżego powietrza.