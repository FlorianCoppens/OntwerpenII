# Test Driven Development (TTD): JUnit
Enkele voordelen om te testen:
* kleine feedback
* maakt stevige code (simplificatie)
* minder tijd verspillen aan debuggen, het probleem kan makkelijk gevonden worden
* ...

Schrijf code met als doel
1. test te doen lukken
2. kwaliteit van de code te verbeteren

## tests schrijven
Test schrijven gebeurt voor we functionaliteiten uitcoderen. Bij het schrijven van tests denk je dan na over de te coderen functionaliteiten, op basis van de analyse. Code waatover je vooraf nadenkt, is betere code.Je voert deze tests uit (alle tests moeten falen aangezien er nog geen functionaliteit is uitgewerkt).

Als je tests schrijft nadat je functionaliteit codeert, heb je de neiging deze tests te baseren op de code van de functionaliteit, niet op de oorspronkelijke analyse. Je maakt dan regelmatig dezelfde denkfouten in je test als in je code.

Door eerst de test te schrijven, kijk je naar een klasse als een gebruiker van een klasse.
Als je op basis van de UML design van een klasse, moeilijk een test kan schrijven, is deze design verkeerd. Je krijgt dus snel feedback op de UML design van de klasse.

TTD -> Je schrijft een stukje functionaliteit en test dit. (= continu feedback)
klassiek -> je schrijft eerst veel functionaliteit, daarna test je pas (= lange tijd geen feedback!)

> Je schrijft de methode met een minimum aan code!
  (1) maak de klasse
  (2) Schrijf nog geen functionele code maar werp een `UnsupportedOperationException`
  
### De te testen klasse
```sh
package domein;
import java.math.BigDecimal;

public class Zichtrekening{
    private BigDecimal saldo;
    
    public BigDecimal getSaldo{
        return this.saldo;
    }
    public void storten(BigDecimal bedrag){
        throw new UnsupportedOperationException();
    }
}
```
# JUnit Test Case
Test case: een klasse die tests bevat
JUnit aanziet iedere methode van een Test Case die voorzien is van `@Test` als een methode die iets test.

**Normale flow in een test methode**
1. Maak een object van de te testen klasse
2. Roep de te testen methode op
3. Controleer of die methode correct uitgevoerd werd

> Opmerking: `import static org.junit.jupiter.api.Assertions.*` wijzigen naar `import org.junit.jupiter.api.Assertions`!

### voorbeeld van een testMethode
```sh
@Test
public void stortenMoetSaldoAanpassen(){
    BigDecimal bedrag = new BigDecimal(200);
    Zichtrekening rekening = new Zichtrekening();
    rekening.storten(bedrag);
    Assertions.assertEquals(bedrag, rekening.getSaldo());
}
```
## Static-methoden in klasse Assertions
`assertEquals(expected, actual)`
Test of expected gelijk is aan actual. 

`assertEquals(expected, actual, String message)`
Test of expected gelijk is aan actual, Toont message als dit niet zo is.

`assertEquals(expected, actual, delta)`
Test of expected actual benadert
delta = maximaal verschil expected, actual en delta zijn van het type double of float.

`assertFalse(boolean conditie)`
Test of conditie gelijk is aan false.

`assertFalse(boolean conditie, String message)`
Test of conditie gelijk is aan false, toont message als dit niet zo is.

`assertTrue(boolean conditie)`
Test of conditie gelijk is aan true.

`assertTrue(boolean conditie, String message)`
Test of conditie gelijk is aan true, toont message als dit niet zo is.

`assertNull(Object object)`
Test of object gelijk is aan null.

`assertNull(Object object, String message)`
Test of object gelijk is aan null, toont message als dit niet zo is.

`assertNotNull(Object object)`
Test of object verschillend is van null.

`assertNotNull(Object object, String message)`
Test of object verschillend is van null, toont message als dit niet zo is.

`assertThrows(IllegalArgumentException.class, () -> {...}`
Werpt een exceptie

### @Test methode tips
Schrijf niet te veel assertions in één @Test methode. Hier zijn enkele nadelen van te veel testen in @Test methode:
* Als een assertions methode binnen een @Test methode faalt, voert JUnit de rest van die @Test methode niet uit
* De methode wordt moeilijk te lezen
* de kans dat je in de methode een bug schrijft is groot
* De kans dat je de methode moet debuggen is groot

De werking van één @Test methode mag niet afhangen van de werking van een andere @Test methode. Ze moeten ook in willekeurige volgorde uitgevoerd kunnen worden.

### Herhalende code vermijden (Test fixtures)
We kunnen gebruik maken van enkele Test fixtures om herhalende code te vermijden.
* `@BeforeAll`: voert deze methode 1 keer uit (in het begin)
* `@AfterAll`: voert deze methode 1 keer uit (op het einde)
* `@BeforeEach`: voert deze methode voor elke `@Test` uit
* `@AftereEach`: voert deze methode na elke `@Test` uit

### Parameterized test
Een test methode meerdere keren uitvoeren met verschillende parameters
```sh
@ParameterizedTest
@CsvSource({/*Alle waarden die getest worden*/})
public void methode(double expected, double valueOne, double valueTwo){
    // test
}
```

andere mogelijkheden
* `@NullAndEmptySource` (null en lege string)
* `@NullSource` (null)
* `@EmptySource` (lege string)
* `@ValueSource(strings = {...})` (opsomming van 1 waarde)

Voor meerdere parameterized tests gebruiken we `@MethodSource` (opsomming hergebruiken)
## Test Suite
```sh
// @RunWith(Suite.class)
@RunWith(JUnitPlatform.class)
// @SuiteClasses({})
@SelectClasses({OneTest.class, AnotherTest.class})
public class AllTests{
    
}
```

