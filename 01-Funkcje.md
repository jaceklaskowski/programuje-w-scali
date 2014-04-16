Funkcje - Dzień 2
=================
Poprzednie spotkanie z językiem Scala zakończyliśmy w Scala REPL "zlecając" mu obliczanie prostych wyrażeń matematycznych.

Kolejnym istotnym elementem języka Scala są funkcje. Intuicja matematyczna bardzo dobrze służy wyjaśnieniu, czym są funkcje w Scali. Istnieją odstępstwa, jednak na nasze, obecne potrzeby zakładamy, że funkcja jest odwzorowaniem danych wejściowych na pewien wynik.

W matematyce funkcja przedstawiana jest w postaci `f(x) = x * 2`.

W Scali funkcja wygląda podobnie, z tym że wymaga poprzedzenia matematycznego odpowiednika słówkiem kluczowym **def** oraz określenia **typów** parametrów wejściowych.

    scala> def f(x: Int) = x * 2
    f: (x: Int)Int

Tak zdefiniowaną funkcję można wykonać, podobnie jak w matematyce, wpisując nazwę funkcji z argumentami.

    scala> f(2)
    res0: Int = 4

Funkcje służą zgrupowaniu kilku obliczeń w jedną całość i zamiast pisać wiele wyrażeń wystarczy funkcja.

"Wiele wyrażeń?" - zapytasz? Tak, wielu i mimo, że powyższy przykład tego nie prezentuje, kolejny już tak.

    scala> def f(x: Int) = {
         |   val y = x * 2
         |   y * 5
         | }
    f: (x: Int)Int

Zgrupowanie wielu wyrażeń w postaci funkcji odbywa się z pomocą nawiasów klamrowych, które w ten sposób wyznaczają granice zasięgu **ciała funkcji**.

Spróbuj ponownie wykonać tę funkcję. Czy domyślasz się wyniku? Poprzedni wynik przyłożenia funkcji `f` do argumentu `2` dał wynik `4`. A jak będzie z powyższą definicją funkcji `f`?

    scala> f(2)
    res1: Int = 20

Spróbuj zdefiniować inne funkcje. Baw się i poczuj Scalę!

Gratulacje spędzenia kolejnych minut z nową konstrukcją w języku Scala - funkcjami.
