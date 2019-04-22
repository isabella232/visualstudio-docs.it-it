---
title: Impostare un'espressione di controllo sulle variabili | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8cd119ab39939de6562adcb962679874d528283
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366811"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Controllare le variabili con finestre Espressioni di controllo e controllo immediato

Durante il debug, è possibile usare **Watch** windows e **controllo immediato** per controllare variabili ed espressioni. Le finestre sono disponibili solo durante una sessione di debug.

**Espressioni di controllo** windows può visualizzare più variabili in un momento durante il debug. Il **controllo immediato** finestra di dialogo Visualizza una singola variabile alla volta e deve essere chiuso prima di proseguire con il debug.

Se questa è la prima volta che si è provato a eseguire il debug di codice, è possibile leggere [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) e [tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md) prima di procedere con questo articolo.

## <a name="observe-variables-with-a-watch-window"></a>Osservare le variabili con una finestra Espressioni di controllo

È possibile aprire più di uno **Watch** finestra e osservare più variabili in un **Watch** finestra.

Ad esempio, per impostare un'espressione di controllo sui valori degli `a`, `b`, e `c` nel codice seguente:

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

1. Impostare un punto di interruzione per il `c = a + b;` riga facendo clic sul margine sinistro, selezionando **Debug** > **Attiva/Disattiva punto di interruzione**, o premendo **F9**.

1. Avviare il debug, selezionare il colore verde **avviare** freccia oppure **Debug** > **Avvia debug**, o premere **F5**. Consente di sospendere l'esecuzione nel punto di interruzione.

1. Aprire una **Watch** finestra selezionando **Debug** > **Windows** > **Watch**  >   **Espressione di controllo 1**, o premendo **Ctrl**+**Alt**+**W** > **1**.

   È possibile aprire ulteriori **Watch** windows selezionando windows **2**, **3**, oppure **4**.

1. Nel **Watch** finestra, selezionare una riga vuota e variabile di tipo `a`. Eseguire la stessa operazione per `b` e `c`.

   ![Controllare le variabili](../debugger/media/watchvariables.png "WatchVariables")

1. Continuare il debug scegliendo **eseguire il Debug** > **Esegui istruzione** oppure premendo **F11** in base alle esigenze per far avanzare. I valori delle variabili nel **Watch** finestra modificata mentre si scorre la `for` ciclo.

>[!NOTE]
>Per C++ solo,
>- Potrebbe essere necessario qualificare il contesto di un nome di variabile o un'espressione che utilizza un nome di variabile. Il contesto è la funzione, file di origine o modulo in cui si trova una variabile. Se è necessario qualificare il contesto, usare il [operatore di contesto (C++)](../debugger/context-operator-cpp.md) sintassi nel **nome** nel **Watch** finestra.
>
>- È possibile aggiungere i nomi di registro e i nomi delle variabili usando  **$ \<registrare&nbsp;nome >** oppure  **@ \<registrare&nbsp;nome >** per il **Name** nel **Watch** finestra. Per altre informazioni, vedere [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Utilizzo delle espressioni in una finestra Espressioni di controllo

È possibile osservare qualsiasi espressione valida riconosciuta dal debugger in un **Watch** finestra.

Ad esempio, per il codice nella sezione precedente, è possibile ottenere la media dei tre valori immettendo `(a + b + c) / 3` nella **Watch** finestra:

![Espressione di controllo](../debugger/media/watchexpression.png "espressione di controllo")

Le regole per la valutazione delle espressioni nel **Watch** finestra sono in genere le stesse regole per la valutazione delle espressioni nel linguaggio di codice. Se un'espressione contiene un errore di sintassi, è probabile che l'errore del compilatore stesso come editor di codice. Ad esempio, un errore di digitazione nell'espressione precedente produce l'errore nel **Watch** finestra:

![Guarda l'errore di espressione](../debugger/media/watchexpressionerror.png "guarda errore di espressione")

Potrebbe essere visualizzato un cerchio con due linee ondulate nella **Watch** finestra. Questa icona indica che il debugger non valuta l'espressione a causa di una potenziale dipendenza cross-thread. La valutazione del codice richiede altri thread di eseguire temporaneamente l'app, ma poiché si è in modalità di interruzione, tutti i thread nell'app vengono in genere interrotti. L'esecuzione temporanea di altri thread può avere effetti imprevisti sullo stato dell'app e il debugger potrebbero ignori alcuni eventi quali i punti di interruzione ed eccezioni nei thread.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Nella finestra Espressioni di controllo di ricerca

È possibile cercare parole chiave nelle colonne del nome, valore e tipo di **Watch** finestra usando la barra di ricerca sopra ogni finestra. Premere INVIO o selezionare una delle frecce per eseguire una ricerca. Per annullare una ricerca in corso, selezionare l'icona "x" nella barra di ricerca.

Utilizzare le frecce sinistra e destra (MAIUSC+F3 e F3, rispettivamente) per spostarsi tra trovare corrispondenze.

![Ricerca nella finestra Espressioni di controllo](../debugger/media/ee-search-watch.png "ricerca nella finestra Espressioni di controllo")

Per eseguire una ricerca più o meno approfonditi, usare il **ricerca più approfondita** elenco a discesa nella parte superiore del **Watch** finestra consente di selezionare quanti livelli di nidificazione per la ricerca in oggetti nidificati. 

::: moniker-end

### <a name="bkmk_refreshWatch"></a> Aggiornare i valori di espressioni di controllo

Un'icona di aggiornamento (freccia circolare) potrebbero essere visualizzati nel **Watch** finestra quando viene valutata un'espressione. L'icona di aggiornamento indica un errore o un valore che non è aggiornato.

Per aggiornare il valore, selezionare l'icona di aggiornamento oppure premere la barra spaziatrice. Il debugger tenta di rivalutare l'espressione. Tuttavia, può non desidera o essere in grado di rivalutare l'espressione, a seconda del motivo per cui non è stato valutato il valore.

Passaggio del mouse sull'icona di aggiornamento o vedere i **valore** colonna per il motivo non è stata valutata l'espressione. I motivi includono:

- Si è verificato un errore durante la valutazione dell'espressione, come nell'esempio precedente. Potrebbe verificarsi un timeout o una variabile potrebbe essere esterni all'ambito.

- L'espressione include una chiamata di funzione che potrebbe attivare un effetto collaterale nell'app. Visualizzare [effetti collaterali espressione](#bkmk_sideEffects).

- La valutazione automatica delle proprietà e chiamate di funzione implicite è disattivata.

Se l'icona di aggiornamento viene visualizzato perché la valutazione automatica delle proprietà e chiamate di funzione implicite è disattivata, è possibile abilitarlo selezionando **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite** in **strumenti**   >  **Opzioni** > **debug** > **generale**.

Per illustrare l'utilizzo l'icona di aggiornamento:

1. Nella **degli strumenti** > **opzioni** > **debug** > **generale**, cancellare il **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite** casella di controllo.

1. Immettere il codice seguente e nel **Watch** impostare un'espressione di controllo nella finestra di `list.Count` proprietà.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Avviare il debug. Il **Watch** finestra qualcosa, ad esempio il messaggio seguente:

   ![Espressioni di controllo di aggiornamento](../debugger/media/refreshwatch.png "aggiornare espressioni di controllo")

1. Per aggiornare il valore, selezionare l'icona di aggiornamento oppure premere la barra spaziatrice. Il debugger rivaluta l'espressione.

### <a name="bkmk_sideEffects"></a> Effetti collaterali di espressione

La valutazione di alcune espressioni possono modificare il valore di una variabile o in caso contrario influiscono sullo stato dell'app. La valutazione della seguente espressione, ad esempio, comporta la modifica del valore di `var1`:

```csharp
var1 = var2
```

Questo codice può causare una [effetto collaterale](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Effetti collaterali possono complicare il debug modificando la modalità che App opera.

Solo una volta, quando si immette lo prima di tutto, viene valutata un'espressione con effetti collaterali. Successivamente, l'espressione viene visualizzato disattivato nella **Watch** finestra e altre versioni di valutazione sono disabilitati. La descrizione comando o **valore** colonna spiega che l'espressione genera un effetto collaterale. È possibile forzare una nuova valutazione selezionando l'icona di aggiornamento visualizzata accanto al valore.

Un modo per impedire la designazione di effetti collaterali consiste nel disattivare la valutazione automatica della funzione. Nelle **degli strumenti** > **opzioni** > **debug** > **generale**, deselezionare **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**.

Per C# , solo quando la valutazione delle proprietà o chiamate di funzione implicite è disattivata, è possibile imporla aggiungendo il **ac** modificatore di formato a una variabile **nome** nel **espressioni di controllo**  finestra. Vedere [Identificatori di formato in C#](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Usare gli ID oggetto nella finestra Espressioni di controllo (C# e Visual Basic)

A volte si vuole osservare il comportamento di un oggetto specifico. Ad esempio, è possibile tenere traccia di un oggetto a cui fa riferimento una variabile locale dopo la variabile esce dall'ambito. In C# e Visual Basic è possibile creare ID oggetto per istanze specifiche dei tipi di riferimento e usarle nella finestra **Espressioni di controllo** e nelle condizioni del punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.

> [!NOTE]
> ID oggetto creano riferimenti deboli che non impediscano l'oggetto venga sottoposto a garbage collection. Sono validi solo per la sessione di debug corrente.

Nel codice seguente, il `MakePerson()` metodo crea un `Person` utilizzando una variabile locale:

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

Per individuare il nome del `Person` nella `DoSomething()` metodo, è possibile aggiungere un riferimento al `Person` ID oggetto nel **Watch** finestra.

1. Impostare un punto di interruzione nel codice dopo il `Person` oggetto è stato creato.

1. Avviare il debug.

1. Quando si mette in pausa l'esecuzione nel punto di interruzione, aprire il **variabili locali** finestra scegliendo **Debug** > **Windows** > **variabililocali**.

1. Nel **variabili locali** finestra, fare doppio clic il `Person` variabile e selezionare **Crea ID oggetto**.

   Verrà visualizzato un segno di dollaro (**$**) insieme a un numero il **variabili locali** finestra, che è l'ID di oggetto.

1. Aggiungere l'ID di oggetto per il **Watch** finestra facendo clic su ID di oggetto e selezionando **Aggiungi espressione di controllo**.

1. Impostare un altro punto di interruzione il `DoSomething()` (metodo).

1. Continuare il debug. Quando l'esecuzione viene sospesa nel `DoSomething()` metodo, il **Watch** finestra vengono visualizzate le `Person` oggetto.

   > [!NOTE]
   > Se si desidera visualizzare le proprietà dell'oggetto, ad esempio `Person.Name`, è necessario abilitare la valutazione delle proprietà, selezionando **Tools** > **opzioni**  >   **Debugging** > **generali** > **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**.

## <a name="dynamic-view-and-the-watch-window"></a>Visualizzazione dinamica e la finestra Espressioni di controllo

Alcuni linguaggi di script (ad esempio, JavaScript o Python) usano dinamico oppure [Duck Typing](https://en.wikipedia.org/wiki/Duck_typing) digitando e .NET 4.0 e versioni successive supporta gli oggetti che sono difficili da osservare le normali finestre di debug.

Il **Watch** finestra consente di visualizzare questi oggetti come oggetti dinamici, che vengono creati dai tipi che implementano il <xref:System.Dynamic.IDynamicMetaObjectProvider> interfaccia. Oggetto dinamico nodi mostrano i membri dinamici dell'oggetto dinamico, ma non consentono la modifica dei valori dei membri.

Per aggiornare **visualizzazione dinamica** valori, selezionare la [icona di aggiornamento](#bkmk_refreshWatch) accanto al nodo oggetto dinamico.

Per visualizzare solo le **visualizzazione dinamica** per un oggetto, aggiungere un **dinamica** identificatore di formato dopo il nome dell'oggetto dinamico nel **Watch** finestra:

- Per C#: `ObjectName, dynamic`
- Per Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Il C# debugger non rivaluta automaticamente i valori di **visualizzazione dinamica** quando si passa alla riga successiva del codice.
>- Il debugger di Visual Basic consente di aggiornare automaticamente le espressioni aggiunte tramite il **visualizzazione dinamica**.
>- La valutazione dei membri di un **visualizzazione dinamica** può avere [effetti collaterali](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Per inserire un'espressione di controllo nuova variabile che esegue il cast di un oggetto in un oggetto dinamico:**

1. Fare doppio clic su qualsiasi elemento figlio di un **visualizzazione dinamica**.
1. Scegli **Aggiungi espressione di controllo**. Il `object.name` diviene `((dynamic) object).name` e viene visualizzato un nuovo oggetto **Watch** finestra.

Il debugger aggiunge anche un **visualizzazione dinamica** nodo figlio dell'oggetto per il **Auto** finestra. Per aprire la **Auto** finestra durante il debug, selezionare **Debug** > **Windows** > **Auto**.

**Visualizzazione dinamica** migliora anche il debug per gli oggetti COM. Quando il debugger ottiene un oggetto COM racchiuso **ComObject**, viene aggiunto un **visualizzazione dinamica** nodo per l'oggetto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Osservare una singola variabile o espressione con controllo immediato

È possibile usare **controllo immediato** per osservare una singola variabile.

Ad esempio, per il codice seguente:

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

Per osservare il `a` variabile,

1. Impostare un punto di interruzione nella riga `a = a + b;` .

1. Avviare il debug. Consente di sospendere l'esecuzione nel punto di interruzione.

1. Selezionare la variabile `a` nel codice.

1. Selezionare **Debug** > **controllo immediato**, premere **MAIUSC**+**F9**, o fare doppio clic e selezionare **Controllo immediato**.

   Il **controllo immediato** viene visualizzata la finestra. Il `a` variabile si trova nella **espressione** casella con un **valore** dei **1**.

   ![Variabile di controllo immediato](../debugger/media/quickwatchvariable.png "variabile di controllo immediato")

1. Per valutare un'espressione che usa la variabile, digitare un'espressione, ad esempio `a + b` nella **espressione** , quindi selezionare **Rivaluta**.

   ![Espressione di controllo immediato](../debugger/media/quickwatchexpression.png "espressione di controllo immediato")

1. Per aggiungere la variabile o espressione dagli **controllo immediato** per il **Watch** finestra, seleziona **Aggiungi espressione di controllo**.

1. Selezionare **chiudere** per chiudere la **controllo immediato** finestra. (**Controllo immediato** è una finestra di dialogo modale, pertanto non è possibile continuare il debug finché è aperta.)

1. Continuare il debug. È possibile osservare la variabile nel **Watch** finestra.

## <a name="see-also"></a>Vedere anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md)
- [Presentazione di debug](../debugger/debugger-feature-tour.md)
- [Finestre del debugger](../debugger/debugger-windows.md)
