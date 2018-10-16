---
title: Impostare un'espressione di controllo sulle variabili in Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/11/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad08799c0dce3792e096291dfaf62d52e2515df4
ms.sourcegitcommit: 48bc8492973e93612e5afaba3b47d0f98aecf97c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2018
ms.locfileid: "49325016"
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Impostare un'espressione di controllo per le variabili con le finestre Espressioni di controllo e controllo immediato in Visual Studio

Durante il debug, è possibile usare la **Watch** e **controllo immediato** windows per controllare variabili ed espressioni.  La differenza è che la finestra **Espressioni di controllo** può visualizzare più variabili, mentre la finestra **Controllo immediato** visualizza una singola variabile alla volta.

Le finestre sono disponibili solo durante una sessione di debug. Per aprire la **Watch** finestra, scegliere **Debug** > **Windows** > **Watch**e quindi scegliere **Espressione di controllo 1**, **guarda 2**, **guarda 3**, o **guarda 4**. Per aprire la **controllo immediato** finestra: pulsante destro del mouse la variabile e scegliere **controllo immediato**, oppure scegliere **Debug** > **controllo immediato** .

## <a name="observe-variables-with-the-watch-window"></a>Osservare le variabili con la finestra Espressioni di controllo

È possibile osservare più variabili con il **Watch** finestra. Si supponga, ad esempio, di avere il codice seguente:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

Aggiungere i valori delle tre variabili per il **Watch** finestra come illustrato di seguito:

1. Selezionare il `c = a + b;` riga.

2. Impostare un punto di interruzione (scegliendo **Debug** > **Attiva/Disattiva punto di interruzione** o premere F9).

3. Avviare i debug (F5). L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.

4. Aprire il **Watch** finestra (scegliendo **Debug** > **Windows** > **Watch**  >   **Espressione di controllo 1**, o premendo Ctrl + Alt + W, 1).

5. Selezionare una riga vuota e la variabile di tipo `a`. Quindi eseguire la stessa operazione per le variabili `b` e `c`.

   ![Controllare le variabili](../debugger/media/watchvariables.png "WatchVariables")

6. Continuare il debug premendo F11 in base alle esigenze per far avanzare il debugger.

I valori delle variabili cambieranno durante l'iterazione del ciclo `for` .

Se si programma in codice nativo, è talvolta necessario qualificare il contesto di un nome di variabile o un'espressione con un nome di variabile. Il contesto è rappresentato dalla funzione, il file di origine e il modulo in cui risiede una variabile. Se è necessario qualificare il contesto, è possibile usare la sintassi dell'operatore di contesto. Per altre informazioni, vedere [operatore di contesto (C++)](../debugger/context-operator-cpp.md).

## <a name="observe-expressions-with-the-watch-window"></a>Osservare le espressioni con la finestra Espressioni di controllo

A questo punto è possibile provare a usare invece un'espressione. È possibile aggiungere qualsiasi espressione valida riconosciuta dal debugger.

Ad esempio, se hai il codice riportato nella sezione precedente, è possibile ottenere la media dei tre valori usando questa espressione:

![Espressione di controllo](../debugger/media/watchexpression.png "WatchExpression")

Le regole per la valutazione delle espressioni nel **Watch** finestra sono in genere le stesse regole per la valutazione delle espressioni nel linguaggio di codifica. Se l'espressione contiene un errore di sintassi, è probabile che lo stesso errore del compilatore che verrebbe visualizzata in editor del codice. Di seguito è riportato un esempio:

![Guarda l'errore di espressione](../debugger/media/watchexpressionerror.png "WatchExpressionError")

## <a name="bkmk_refreshWatch"></a> Aggiornare i valori di espressioni di controllo che non sono aggiornati

Un'icona di aggiornamento (una freccia circolare) potrebbe essere visualizzato quando un'espressione viene valutata nel **Watch** finestra. Se hai attivato la valutazione delle proprietà (scegliendo **degli strumenti** > **opzioni** > **debug**  >   **Generali**, quindi deselezionando **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**), ed è stato scritto il codice seguente:

```csharp
static void Main(string[] args)
{
    List<string> list = new List<string>();
    list.Add("hello");
    list.Add("goodbye");
}

```

Verrà visualizzato qualcosa di simile all'immagine seguente se si imposta un'espressione di controllo per il `Count` proprietà dell'elenco:

![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")

La figura precedente mostra un errore o un valore che non è aggiornato. È possibile aggiornare il valore in genere selezionando l'icona, ma in alcuni casi è preferibile non aggiornarlo. Prima di tutto è necessario conoscere il motivo per cui non è stato valutato il valore.

Una descrizione comando fornisce informazioni sui motivi per cui non è stata valutata l'espressione se scegliere l'icona. Se vengono visualizzate le frecce che girano in cerchio, l'espressione non è stata valutata per uno dei motivi seguenti:

- Si è verificato un errore durante la valutazione dell'espressione. Ad esempio, è possibile che si sia verificato un timeout o che una variabile fosse esterna all'ambito.

- L'espressione contiene una chiamata di funzione, che potrebbe attivare un effetto collaterale dell'applicazione (vedere la [effetti collaterali ed espressioni](#bkmk_sideEffects) sezione).

- È stata disattivata la valutazione automatica delle proprietà e chiamate a funzioni implicite dal debugger (scegliendo **degli strumenti** > **opzioni** > **debug**  >  **Generali**, quindi deselezionando **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**). L'espressione non può essere valutata una automaticamente quindi.

Per aggiornare il valore, selezionare l'icona di aggiornamento oppure premere la barra spaziatrice. Il debugger tenta di rivalutare l'espressione. Verrà visualizzata l'icona di aggiornamento perché la valutazione automatica delle proprietà e altre chiamate di funzione implicite è disattivata. In questo caso, il debugger è possibile valutare l'espressione.

Venga visualizzata un'icona che è un cerchio con due linee ondulate che assomigliano a thread. Questa icona indica che il debugger non valuta l'espressione a causa di una potenziale dipendenza cross-thread. In altre parole, la valutazione del codice richiede l'esecuzione temporanea di altri thread nell'applicazione. Quando ci si trova in modalità di interruzione, in genere tutti i thread nell'applicazione vengono arrestati. L'esecuzione temporanea di altri thread può avere effetti imprevisti sullo stato del programma e può far sì che il debugger ignori alcuni eventi quali i punti di interruzione e le eccezioni generate in tali thread.

## <a name="bkmk_sideEffects"></a> Effetti collaterali ed espressioni

La valutazione di alcune espressioni può comportare la modifica del valore di una variabile o altri effetti sullo stato del programma. La valutazione della seguente espressione, ad esempio, comporta la modifica del valore di `var1`:

```csharp
var1 = var2
```

Questo codice può causare una [effetto collaterale](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Gli effetti collaterali possono rendere più difficile il debug modificando la modalità di funzionamento del programma.

Solo una volta, quando si immette lo prima di tutto, viene valutata un'espressione che nota presentano effetti collaterali. Ulteriori valutazioni vengono disabilitate. È possibile eseguire manualmente l'override di questo comportamento selezionando l'icona di aggiornamento visualizzata accanto al valore.

Un modo per evitare gli effetti collaterali consiste nel disattivare la valutazione automatica della funzione (scegliendo **degli strumenti** > **opzioni** > **debug**  >  **Generali**, quindi deselezionando **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**).

Quando la valutazione delle proprietà o delle chiamate di funzione implicite è disattivata, è possibile forzarla con il modificatore di formato **ac** (solo per C#). Visualizzare [Format specifiers in c#](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Usare gli ID oggetto nella finestra Espressioni di controllo (c# e Visual Basic)

In alcuni casi si vuole osservare il comportamento di un oggetto specifico. Ad esempio, è possibile tenere traccia di un oggetto a cui fa riferimento una variabile locale dopo la variabile esce dall'ambito. In c# e Visual Basic, è possibile creare ID oggetto per istanze specifiche dei tipi di riferimento e usarle nel **Watch** finestra e nelle condizioni punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.

> [!NOTE]
> ID oggetto creano riferimenti deboli che non impediscano l'oggetto venga sottoposto a garbage collection. Sono validi solo per la sessione di debug corrente.

Nel codice seguente, un metodo crea un `Person` usando una variabile locale, ma si desidera scoprire cosa la `Person`del nome è in un metodo diverso:

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}

```

È possibile aggiungere un riferimento all'oggetto `Person` nella finestra **Espressioni di controllo** come segue:

1. Selezionare una riga nel codice che si verifica che l'oggetto è stato creato.

2. Impostare un punto di interruzione (scegliendo **Debug** > **Attiva/Disattiva punto di interruzione** o premere F9).

3. Avviare il debug.

4. Quando l'esecuzione si arresta nel punto di interruzione, aprire il **variabili locali** finestra (scegliendo **Debug** > **Windows** > **variabililocali**), la variabile e scegliere **Crea ID oggetto**.

   Verrà visualizzato un segno di dollaro (**$**) insieme a un numero il **variabili locali** finestra, che è l'ID oggetto.

   > [!NOTE]
   > Se si desidera visualizzare le proprietà dell'oggetto, ad esempio `Person.Name`, è necessario abilitare la valutazione delle proprietà, scegliendo **Tools** > **opzioni**  >   **Debugging** > **generali**, quindi impostare **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**.

5. Aggiungere l'ID di oggetto per il **Watch** finestra facendo il segno di dollaro e il numero, quindi scegliendo **Aggiungi espressione di controllo**.

6. Impostare un punto di interruzione in cui si vuole osservare il comportamento dell'oggetto.  Nel codice precedente, che sarebbe nel `DoSomething()` (metodo).

7. Continuare il debug. Quando l'esecuzione viene arrestata nel `DoSomething()` metodo, il **Watch** finestra viene visualizzato il `Person` oggetto.

## <a name="use-registers-in-the-watch-window-c-only"></a>Usare i registri nella finestra Espressioni di controllo (solo C++)

È possibile aggiungere i nomi di registro e i nomi delle variabili usando  **$ \<registrare&nbsp;nome >** oppure  **@ \<registrare&nbsp;nome >** durante il debug del codice nativo. Per altre informazioni, vedere [Pseudovariables](../debugger/pseudovariables.md).

## <a name="dynamic-view-and-the-watch-window"></a>Visualizzazione dinamica e la finestra Espressioni di controllo

Alcuni linguaggi di script (ad esempio, JavaScript o Python) usano dinamico oppure [Duck Typing digitando](https://en.wikipedia.org/wiki/Duck_typing), e i linguaggi .NET (nella versione 4.0 e versioni successive) supportano gli oggetti che sono difficili da osservare con le normali finestre di debug, poiché sono possono contenere proprietà runtime e i metodi che non possono essere visualizzati.

Il **Watch** finestra potrebbe visualizzare un oggetto dinamico, viene creato da un tipo che implementa il <xref:System.Dynamic.IDynamicMetaObjectProvider> interfaccia. Quando questo oggetto viene visualizzato, il debugger aggiunge una speciale **visualizzazione dinamica** nodo figlio del nome dell'oggetto, se si apre il **Auto** finestra (scegliendo **Debug**  >  **Windows** > **Auto**). Questo nodo Mostra i membri dinamici dell'oggetto dinamico, ma non consente la modifica dei valori dei membri.

Per inserire un'espressione di controllo nuova variabile che esegue il cast di un oggetto in un oggetto dinamico:

1. Fare doppio clic su qualsiasi elemento figlio di un **visualizzazione dinamica**.
2. Scegli **Aggiungi espressione di controllo**. Quindi `object.name` diventa `((dynamic) object).name`.

La valutazione dei membri di una **Visualizzazione dinamica** può avere degli effetti collaterali. Per una spiegazione degli effetti collaterali, vedere la [effetti collaterali ed espressioni](#bkmk_sideEffects) sezione. Per c#, il debugger non rivaluta automaticamente i valori visualizzati nei **visualizzazione dinamica** quando si passa a una nuova riga di codice. Per Visual Basic le espressioni aggiunte tramite la **Visualizzazione dinamica** vengono aggiornate automaticamente.

Per istruzioni su come aggiornare il **visualizzazione dinamica** valori, vedere la [valori di espressioni di controllo di aggiornamento che non sono aggiornati](#bkmk_refreshWatch) sezione.

Se si desidera visualizzare solo le **visualizzazione dinamica** per un oggetto, è possibile usare il **dinamica** nell'identificatore di formato il **Watch** finestra:

- C#: `ObjectName, dynamic`
- Visual Basic: `$dynamic, ObjectName`

La **Visualizzazione dinamica** migliora anche l'esperienza di debug per gli oggetti COM. Quando il debugger ottiene un oggetto COM racchiuso **ComObject**, viene aggiunto un **visualizzazione dinamica** nodo per l'oggetto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Osservare una singola variabile o espressione con controllo immediato

È possibile usare la finestra **Controllo immediato** per osservare una singola variabile. Si supponga, ad esempio, di avere il codice seguente:

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

È possibile osservare una variabile nel **controllo immediato** finestra come illustrato di seguito:

1. Impostare un punto di interruzione nella riga `a = a + b;` .

2. Avviare il debug. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.

3. Selezionare la variabile `a`.

4. Scegliere **Debug** > **controllo immediato** oppure premere **MAIUSC+F9**. Il **controllo immediato** verrà visualizzata la finestra. Nel **valore** finestra di `a` variabile viene visualizzata con un valore pari a 1.

   ![Variabile di controllo immediato](../debugger/media/quickwatchvariable.png "QuickWatchVariable")

   Per valutare un'espressione che usa la variabile, digitare un'espressione, ad esempio `a + b` per il **espressione** casella e fare clic su **Rivaluta**.

   ![Espressione di controllo immediato](../debugger/media/quickwatchexpression.png "QuickWatchExpression")

   Per aggiungere la variabile o l'espressione per il **Watch** finestra dal **controllo immediato**, scegliere **Aggiungi espressione di controllo**.

   > [!NOTE]
   > Il **controllo immediato** finestra è una finestra di dialogo modale, cui non è possibile continuare il debug finché è aperta.

5. Chiudere la finestra **Controllo immediato** . È ora possibile continuare il debug osservando il valore nella finestra **Espressioni di controllo** .

## <a name="see-also"></a>Vedere anche

[Finestre del debugger](../debugger/debugger-windows.md)
