Wartości i typy - Dzień 3
=========================
Już wiesz, jak napisać prostą funkcję w Scali. Pewnie nie zabierze Ci dużo czasu, kiedy trafisz na problem, którego nie będziesz mogła wyrazić korzystając z dotychczasowego zasobu wiedzy dotyczącej języka Scala. W tej części przedstawię pojęcie **wartości** (ang. *value*) oraz jej **typu** (ang. *type*).

Pamiętasz następujące wyrażenia, które wpisywałaś w Scala REPL?

    scala> def f(x: Int) = x * 2
    f: (x: Int)Int

oraz

    scala> 1+1
    res0: Int = 2

Zwróć uwagę na odpowiedzi, które REPL wypisuje na ekran, w linii następującej po wpisanym wyrażeniu i wciśnięciu ENTER.

W pierwszym przypadku jest to `f: (x: Int)Int`, podczas gdy w drugim `res0: Int = 2`. Coś mi podpowiada, że drugi przypadek jest prostszy do wyjaśnienia, a mimo wszystko, upieram się przy wyjaśnieniu pierwszego. Trzymam kciuki, że nam się wspólnie uda (bez względu na wybór "problemu").

Jaki był zamysł, kiedy wpisywałaś `def f(x: Int) = x * 2`? Deklaracja funkcji `f`, która akceptuje pojedynczy parametr typu `Int`. Mimo wielu niewyjaśnionych jeszcze kwestii - deklaracja, funkcja, typ - nasz zapis sprowadził się do utworzenia symbolu `f`, który wskazuje na ciało `x * 2`. W ten sposób zamiast wpisywać każdorazowo `x * 2`, możesz korzystać z symbolu `f`.

	scala> def f(x: Int) = x * 2
	f: (x: Int)Int

	scala> f(2)
	res0: Int = 4

Przyjrzyjmy się owemu symbolowi `f`. Po dwukropku w języku Scala następuje określenie typu symbolu, który wymiennie będziemy również nazywać wartością.

Wartość `f` jest typu `(x: Int)Int` i jest to specjalny (wewnętrzny) zapis typu metody (prawie funkcyjnego) określającego metodę jednego parametru - przypisanego do kolejnego symbolu `x` typu `Int` - która zwraca typ `Int`.

Ogólna postać metody, opisanej przez Scala REPL, będzie wyglądała następująco:

    [nazwa-metody]: ( [lista-parametrów-z-typami] )typ-wartości-zwracanej

gdzie *nazwa-metody* to symbol, którym będziemy się posługiwać do operowania blokiem kodu, który występuje po znaku równości *=*, oraz *lista-parametrów-z-typami* jest listą par - nazwa parametru (kolejnego symbolu dostępnego w ramach bloku funkcji) i jego typu po dwukropku. Po nawiasie okrągłym występuje typ zwracanej wartości z metody.

W przypadku drugiego wyrażenia `1+1`, Scala REPL odpowiedział `res0: Int = 2`. W ten sposób zdefiniowałaś symbol `res0` typu `Int` z wartością `2`.

Podsumowanie
Każdy symbol związany jest z pewnym typem, który (jeśli określony) występuje po dwukropku. Symbol wskazuje na wartość i jest jej reprezentantem - inną nazwą.

Pytanie kontrolne:
1. Czy kilkukrotne wpisanie wyrażenia `1+1` definiuje ten sam symbol?