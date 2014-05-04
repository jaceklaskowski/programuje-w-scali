O literałach dokładniej - Dzień 9
==================================

Spotkałaś się już z literałem funkcyjnym `(parametry) => wartość`, literałami liczb całkowitych `5`, literałem logicznym `true` i kilkoma innymi, których nie nazywaliśmy literałami.

Za Wikipedią:

> *Literał* – w językach programowania, to jednostka leksykalna reprezentująca na stałe ustaloną wartość 
> wpisaną przez programistę bezpośrednio w danym miejscu w kod programu. Różni się od stałej tym, że 
> stała jest identyfikatorem, a nie wartością.

Specyfikacja języka Scala (w rozdziale 1.3 Literals) opisuje dostępne literały: literał liczbowy dla liczb całkowitych i zmiennoprzecinkowych, literał logiczny, znakowy, napisowy (łańcuchowy) oraz wieloliniowy.

# Literał całkowity - liczba

Poważnie wyglądająca nazwa *literał liczb całkowitych* zwykle występuje pod nazwą *stała liczbowa* lub po prostu *liczba* (patrz [Literał liczbowy](http://pl.wikipedia.org/wiki/Litera%C5%82_liczbowy)).

Ze względu na zapis wyróżniamy w Scali liczby dziesiętne lub szesnastkowe. Rozróżnienie ich polega na prefiksie `0x`, który opisuje liczby szesnastkowe, po którym następują dozwolone liczby z systemu. Liczby dziesiętne to `0` (zero) lub ciąg liczb `0`-`9`, który rozpoczyna się nie-zerem - dowolną liczbą z przedziału `1`-`9`.

	scala> 0
	res1: Int = 0

	scala> 10
	res2: Int = 10

	scala> 98
	res3: Int = 98

	scala> :type 98
	Int

	scala> 0x78
	res4: Int = 120

	scala> 0xAA
	res5: Int = 170

	scala> :type 0xABBA
	Int

Liczby należą do typu `Int`, jeśli należą do przedziału `-2^31`-`2^31 - 1`, włącznie.

Liczba, po której występuje litera `L` (duże `L`) lub `l` (małe `L`), jest typu `Long`, który zawiera przedział `-2^63`-`2^63 - 1`, włącznie.

	scala> 0L
	res6: Long = 0

	scala> :type 5L
	Long

Do dyspozycji mamy jeszcze typy `Byte` (przedział `-2^7`-`2^7 - 1`), `Short` (przedział `-2^15`-`2^15 - 1`) oraz `Char` (przedział `0`-`2^16 - 1`). Użycie tych typów dla wartości musi być jednak jawne, co oznacza, jawne opisanie typu dla liczby.

**Pamiętaj** Określenie typu w Scali występuje po dwukropku.

	scala> 5: Byte
	res7: Byte = 5

	scala> :type 5: Byte
	Byte

	scala> 5: Char
	res8: Char = ?

	scala> 5: Short
	res9: Short = 5

# Literał zmiennoprzecinkowy

Liczba, po której występuje sufiks `F` (duże `F`) lub `f` (małe `F`), jest liczbą typu `Float`, która zawiera wartości opisane w specyfikacji IEEE 754 dla 32-bitowych liczb.

W przeciwnym przypadku liczba zmiennoprzecinkowa jest typu `Double` lub jeśli sufiksem jest `D` lub `d` (małe `D`).

Separatorem części podstawowej a częścią wykładniczą jest kropka `.`.

	scala> 1234.876
	res11: Double = 1234.876

	scala> 1234.876f
	res12: Float = 1234.876

Dozwolony jest zapis liczby zmiennoprzecinkowej rozpoczynając od kropki.

	scala> :type .129
	Double

	scala> :type .129f
	Float

# Literał logiczny

Istnieją dwa literały logiczne, które należą do typu `Boolean` -- `true` oraz `false`.

	scala> :type true
	Boolean

	scala> :type false
	Boolean

# Literał znakowy

Literał znakowy przedstawiony jest w postaci ciągu znaków rozpoczynającego i kończącego się pojedynczym cudzysłowem `'`, który zawiera znaki (drukowalne) Unicode.

	scala> :type 'a'
	Char

	scala> :type 'B'
	Char

	scala> :type '\n'
	Char

# Literał łańcuchowy - napis

Napis w Scali przedstawiony jest w postaci ciągu znaków rozpoczynającego i kończącego się znakami cudzysłowu `"`. Typ napisu to `String`.

	scala> :type "Ala ma kota"
	String

	scala> :type "A"
	String

Jeśli chciałabyś umieścić znak cudzysłowu w napisie, musisz go poprzedzić znakiem `\`.

	scala> :type "To jest \"napis\" z cudzysłowami"
	String

# Literał znakowy wieloliniowy

Blok znakowy, w którym występuje wiele linii, między potrójnymi znakami cudzysłowu `"""` nazywamy *literałem znakowym wielolionym*.

W ramach bloku znakowego może występować dowolny znak, poza potrójnymi cudzysłowami, który kończy blok.

	scala> """To jest linia pierwsza
	     | a to druga
	     | kolejna
	     | i tak dalej
	     |
	     | była również pusta w międzyczasie"
	     | i cudzysłów pojedynczy
	     | """
	res14: String =
	"To jest linia pierwsza
	a to druga
	kolejna
	i tak dalej

	była również pusta w międzyczasie"
	i cudzysłów pojedynczy
	"

Blok znakowy jest typu `String`, który udostępnia metodę `stripMargin`, która usuwa wiodące białe znaki (spacje, tabulacje) z bloku, jeśli po nich występuje znak `|` (pionowa kreska).

Skorzystajmy ze specjalnego trybu Scala REPL - `:paste`, w którym możliwe jest wklejanie całych wyrażeń scalowych, co pozwoli nam na wklejenie poniższego bloku.

	"""Pierwsza linia
	  |Druga linia, z wiodącymi spacjami""".stripMargin

W Scala REPL wpisz `:paste`, aby przejść do trybu wklejania.

	scala> :paste
	// Entering paste mode (ctrl-D to finish)

	"""Pierwsza linia
	  |Druga linia, z wiodącymi spacjami""".stripMargin

Zakończenie wklejania (również możliwe jest wpisywanie kodu) następuje za pomocą kombinacji klawiszy `Ctrl` i `d`. Wciśnij jednocześnie `Ctrl` i `d`.

	// Exiting paste mode, now interpreting.

	res17: String =
	Pierwsza linia
	Druga linia, z wiodącymi spacjami

# Znaki ucieczki

Specjalne niedrukowane znaki nazywane *znakami ucieczki* są dozwolone w literałach znakowych i napisowych.

	\b \u0008: znak kasowania znaku poprzedzającego kursor
	\t \u0009: tabulacja pozioma
	\n \u000a: znak nowej linii
	\f \u000c: znak wysunięcia
	\r \u000d: znak powrotu karetki
	\" \u0022: podwójny cudzysłów
	'  \u0027: pojedynczy cudzysłów
	\\ \u005c: ukośnik wstecz

Scala pozwala na opisanie znaku Unicode między `0` a `255` w postaci ósemkowej jako ciąg znaków rozpoczynający się od znaku ukośnika wstecz `\`, po którym następuje sekwencja jednego lub co najwyżej trzech znaków z systemu ósemkowego.

...TODO przykłady

# Literał symbolu

Zapis rozpoczynający się od pojedynczego cudzysłowu `'x` jest literałem dla wyrażenia `scala.Symbol("x")`.

	scala> :type 'A
	Symbol

	scala> :type 'Ala_ma_kota
	Symbol

	scala> 'A == Symbol("A")
	res18: Boolean = true