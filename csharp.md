# C Sharp Style-Guide

## Formatierungsrichtlinien

### Namensgebungs Regeln
- Es werden **NIE** umlaute in Namen benutzt. Immer die Englische schreib variante benutzen.

#### Code
- Namen von Klassen, Methoden, Enumerations, Öffentliche Eigenschaften, Lokale Eigenschaften, Namespaces : ` ExampleName `
- Namen von Privaten, geschützte, interne und geschützte interne Felder und Eigenschaften : `_ExampleName`
- Die Namenskonvention wird von Modifikatoren wie const, static, readonly usw. nicht beeinflusst.
- Für Groß- und Kleinschreibung ist ein „Wort“ alles, was ohne Leerzeichen geschrieben wird, einschließlich Akronyme. Beispiel : `MyRb` statt `MyRB`.
- Namen von Interfaces starten mit einem `I_` : `I_ExampleInterface`

#### Datein/Ordner
- Datein/Ordner Namen werden **NICHT** Abgekürtzt.
- Der Skript Ordner in Unity Projekten hat immer den Namen : `_scripts`.

### Leerzeichen Regeln
- Maximal eine Aussage pro Zeile.
- Maximal eine Zuordnung pro Aussage.
- Spaltenlimit: 300.
- Kein Zeilenumbruch vor dem Öffnen der geschweiften Klammer.
- Kein Zeilenumbruch zwischen schließender geschweifter Klammer und sonst.
- Klammern werden verwendet, auch wenn sie optional sind.
- Leerzeichen nach `if/for/while` usw. und nach Kommas.
- Ein Leerzeichen nach einer öffnenden Klammer oder vor einer schließenden Klammer.
- Ein Leerzeichen zwischen dem Operator und jedem Operanden aller anderen Operatoren.
- Der Zeilenumbruch wurde anhand der Stilrichtlinien von Google C++ entwickelt, mit geringfügigen Änderungen für die Kompatibilität mit den C#-Formatierungstools von Microsoft:
- Generell werden Zeilenfortsetzungen um 4 Leerzeichen eingerückt.
- Zeilenumbrüche mit geschweiften Klammern (z. B. Listeninitialisierer, Lambdas, Objektinitialisierer usw.) zählen nicht als Fortsetzungen.
- Wenn bei Funktionsdefinitionen und -aufrufen die Argumente nicht alle in eine Zeile passen, sollten sie auf mehrere Zeilen aufgeteilt werden, wobei jede nachfolgende Zeile am ersten Argument ausgerichtet ist. Wenn der Platz dafür nicht ausreicht, können Argumente stattdessen mit einem Einzug von vier Leerzeichen in nachfolgenden Zeilen platziert werden. Das folgende Codebeispiel veranschaulicht dies.

### Beispiel

```csharp
using System;                                       // `using` goes at the top, outside the
                                                    // namespace.

namespace MyNamespace {                             // Namespaces are PascalCase.
                                                    // Indent after namespace.
  public interface I_MyInterface {                   // Interfaces start with 'I'
    public int calculate(float value, float exp);   // Methods are PascalCase
                                                    // ...and space after comma.
  }

  public enum MyEnum {                              // Enumerations are PascalCase.
    Yes,                                            // Enumerators are PascalCase.
    No,
  }

  public class MyClass {                            // Classes are PascalCase.
    public int Foo = 0;                             // Public member variables are
                                                    // PascalCase.
    public bool NoCounting = false;                 // Field initializers are encouraged.

    private class Results {
      public int NumNegativeResults = 0;
      public int NumPositiveResults = 0;
    }

    private Results results;                       // Private member variables are
                                                    // _camelCase.
    public static int NumTimesCalled = 0;
    private const int bar = 100;                   // const does not affect naming
                                                    // convention.
    private int[] SomeTable = {                    // Container initializers use a 2
      2, 3, 4,                                      // space indent.
    }

    public MyClass() {
      results = new _Results {
        NumNegativeResults = 1,                     // Object initializers use a 2 space
        NumPositiveResults = 1,                     // indent.
      };
    }

    public int CalculateValue(int mulNumber) {      // No line break before opening brace.
      private var ResultValue = Foo * MulNumber;            // Local variables are camelCase.
      NumTimesCalled++;
      Foo += Bar;

      if (!NoCounting) {                            // No space after unary operator and
                                                    // space after 'if'.
        if (eRsultValue < 0) {                      // Braces used even when optional and
                                                    // spaces around comparison operator.
          Results.NumNegativeResults++;
        } else if (resultValue > 0) {               // No newline between brace and else.
          results.NumPositiveResults++;
        }
      }

      return resultValue;
    }

    public void doNothing() {}                             // Empty blocks may be concise.

    // If possible, wrap arguments by aligning newlines with the first argument.
    private void _aVeryLongFunctionNameThatCausesLineWrappingProblems(int longArgumentName,
                                                                      int p1, int p2) {}

    // If aligning argument lines with the first argument doesn't fit, or is difficult to
    // read, wrap all arguments on new lines with a 4 space indent.
    private void _anotherLongFunctionNameThatCausesLineWrappingProblems(
        int longArgumentName, int longArgumentName2, int longArgumentName3) {}

    public void callingLongFunctionName() {
      int veryLongArgumentName = 1234;
      int shortArg = 1;
      // If possible, wrap arguments by aligning newlines with the first argument.
      _anotherLongFunctionNameThatCausesLineWrappingProblems(shortArg, shortArg,
                                                            veryLongArgumentName);
      // If aligning argument lines with the first argument doesn't fit, or is difficult to
      // read, wrap all arguments on new lines with a 4 space indent.
      _anotherLongFunctionNameThatCausesLineWrappingProblems(
          veryLongArgumentName, veryLongArgumentName, veryLongArgumentName);
    }
  }
}
```
