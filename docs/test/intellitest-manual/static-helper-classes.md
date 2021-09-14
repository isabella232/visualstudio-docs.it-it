---
title: Classi helper statiche | Strumento di test per sviluppatori Microsoft IntelliTest
description: Informazioni sulle classi helper statiche fornite da IntelliTest per la creazione di unit test con parametri.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: fa4c088543775a55b0ec9b2bedea07a92b44cc9b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710117"
---
# <a name="static-helper-classes"></a>Classi helper statiche

IntelliTest specifica un set di classi helper statiche che possono essere usate durante la creazione di [unit test con parametri](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): usata per definire i presupposti per gli input, utile per filtrare gli input indesiderati
* [PexAssert](#pexassert): classe di asserzione semplice da usare se il framework di test non dispone di una classe di questo tipo
* [PexChoose](#pexchoose): flusso di input di test aggiuntivi gestiti da IntelliTest
* [PexObserve](#pexobserve): registra valori concreti e facoltativamente li convalida nel codice generato

Alcune classi consentono di interagire con il motore di elaborazione IntelliTest a livello basso:

* [PexSymbolicValue](#pexsymbolicvalue): utilità che controllano o modificano vincoli simbolici nelle variabili

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Classe statica usata per esprimere presupposti, ad esempio [precondizioni](test-generation.md#precondition), negli [unit test con parametri](test-generation.md#parameterized-unit-testing). I metodi di questa classe possono essere usati per escludere gli input di test indesiderati.

Se la condizione presupposta non è vera per una parte dell'input di test, viene generata un'eccezione **PexAssumeFailedException**. In seguito a tale eccezione il test viene ignorato senza alcun avviso.

**Esempio**

Il seguente test con parametri non considera **j=0**:

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Osservazioni:**

Il codice sopra riportato è quasi equivalente a:

```csharp
     if (j==0)
          return;
```

salvo per il fatto che un errore di **PexAssume** non origina nessun test case. Nel caso di un'istruzione **if** IntelliTest genera un test case separato per includere il ramo **then** dell'istruzione **if**.

**PexAssume** include anche classi annidate specializzate per presupposti su stringhe, matrici e raccolte.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Classe statica usata per esprimere asserzioni, ad esempio [postcondizioni](test-generation.md#postcondition), negli [unit test con parametri](test-generation.md#parameterized-unit-testing).

Se la condizione asserita non è vera per una parte dell'input di test, viene generata un'eccezione **PexAssertFailedException** e il test ha esito negativo.

**Esempio**

Il seguente codice asserisce che il valore assoluto di un numero intero è positivo:

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Classe statica che trasmette a un test valori di input ausiliari usabili per implementare [oggetti fittizi con parametri](input-generation.md#parameterized-mocks).

La classe **PexChoose** non consente di determinare se un test è stato superato per determinati valori di input. **PexChoose** si limita a offrire i valori di input, detti anche *scelte*. Spetta comunque all'utente limitare i valori di input e scrivere asserzioni che definiscono quando un test viene o non viene superato.

**Modalità di funzionamento**

La classe **PexChoose** può funzionare in due modi:

* Mentre IntelliTest esegue un'analisi simbolica del test e del codice testato durante la [generazione dell'input](input-generation.md), il modulo di selezione restituisce valori arbitrari e IntelliTest rileva come ogni valore viene usato nel test e nel codice testato. IntelliTest genera valori rilevanti per l'attivazione di diversi percorsi di esecuzione del test e del codice testato.

* Il codice generato per determinati test case imposta il provider scelto in un modo specifico, per far sì che la nuova esecuzione di questo test case applichi scelte specifiche in modo da attivare un percorso di esecuzione particolare.

**Utilizzo**

* Chiamata semplice di **PexChoose.Value** per generare un nuovo valore:

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Classe statica per registrare valori denominati.

Quando IntelliTest esplora il codice, **PexObserve** viene usata per registrare i valori calcolati usando le rappresentazioni stringa formattate di tali valori. I valori sono associati a nomi univoci.

```csharp
PexObserve.Value<string>("result", result);
```

**Esempio**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}

// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a);
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Classe statica usata per ignorare i vincoli sui parametri e per stampare le informazioni simboliche associate a valori.

**Utilizzo**

In genere IntelliTest prova a raggiungere tutti i percorsi di esecuzione del codice durante l'esecuzione. Tuttavia, specie per il calcolo di condizioni di presupposto e asserzione, è opportuno che non esplori tutti i casi possibili.

**Esempio**

Questo esempio visualizza l'implementazione del metodo **PexAssume.Arrays.ElementsAreNotNull**.
Nel metodo si ignorano i vincoli relativi alla lunghezza del valore della matrice, per evitare che IntelliTest tenti di generare diverse dimensioni di matrice. I vincoli vengono ignorati solo in questo contesto. Se il codice testato funziona in modo diverso per lunghezze della matrice diverse, IntelliTest non può generare matrici con dimensioni diverse dai vincoli del codice testato.

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>Per eventuali commenti,

Pubblicare idee e richieste di funzionalità nella [community degli sviluppatori](https://aka.ms/feedback/suggest?space=8).
