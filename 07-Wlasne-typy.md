Definiowanie własnych typów - Dzień 8
=====================================

Nowe typy w języku Scala definiowane są za pomocą słów kluczowych `class` lub `object`, które dodatkowo mogą być poprzedzone słowem `case`.

    class
    object
    case class
    case object

Po `class` lub `object` występuje nazwa typu. Zwyczajowo, nazwa typu pisana jest wielką literą, np. `List`.

Zdefiniujmy kilka nowych typów w Scala REPL.

	scala> case object A
	defined module A

	scala> case class B
	defined class B

	scala> object C
	defined module C

	scala> class D
	defined class D

Dla naszych potrzeb, poznanie tych konstrukcji sprowadzimy do pojedynczego `object C`, który będzie służył jako "kontener" metod.
