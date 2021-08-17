---
title: Impostare un controllo sulle variabili | Microsoft Docs
description: Durante il debug, vedere variabili ed espressioni in Espressioni di controllo e Controllo immediato. L'oggetto Watch può visualizzare diverse variabili, una sola di Controllo immediato e solo durante l'interruzione.
ms.custom: SEO-VS-2020
ms.date: 10/11/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 178bb177015ba191f4f31af7eb24116b34d84f77080f091f8418b42f6e86d442
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404194"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Variabili di controllo con le finestre Espressioni di controllo e Controllo immediato

Durante il debug, è possibile usare le finestre **Espressioni** di controllo e **Controllo immediato** per controllare variabili ed espressioni. Le finestre sono disponibili solo durante una sessione di debug.

**Le** finestre espressioni di controllo possono visualizzare diverse variabili alla volta durante il debug. La **finestra di dialogo** Controllo immediato visualizza una singola variabile alla volta e deve essere chiusa prima che il debug possa continuare.

> [!NOTE]
> Se è la prima volta che si prova a eseguire [](../debugger/debugging-absolute-beginners.md) il debug del codice, è possibile leggere Debug per principianti assoluti e Tecniche e strumenti di debug prima di passare a questo articolo. [](../debugger/write-better-code-with-visual-studio.md)

## <a name="observe-variables-with-a-watch-window"></a>Osservare le variabili con un finestra Espressioni di controllo

È possibile aprire più di una **finestra Espressioni** di controllo e osservare più variabili in una finestra **Espressioni di** controllo.

Ad esempio, per impostare un controllo sui valori di `a` , e nel codice `b` `c` seguente:

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

1. Impostare un punto di interruzione sulla riga facendo clic sul margine sinistro, selezionando Debug Attiva/Disattiva punto di `c = a + b;`   >  interruzione o premendo **F9.**

1. Avviare il debug selezionando la freccia **verde Avvia** o **Avvia**  >  **debug oppure** premere **F5.** L'esecuzione viene sospesa in corrispondenza del punto di interruzione.

1. Aprire una **finestra Espressioni** di controllo selezionando **Debug**  >  **Windows**  >  **Watch**  >  **Watch 1** o premendo **CTRL** +  + **ALT+W**  >  **1.**

   È possibile aprire altre **finestre Espressioni** di controllo selezionando windows **2,** **3** o **4.**

1. Nella finestra **Espressione di** controllo selezionare una riga vuota e digitare variabile `a` . Eseguire la stessa operazione per `b` e `c` .

   ![Controllare le variabili](../debugger/media/watchvariables.png "WatchVariables")

1. Continuare il debug selezionando **Esegui**  >  **debug in** o premendo **F11** in base alle esigenze per procedere. I valori delle variabili nella **finestra Espressioni** di controllo cambiano durante l'iterazione del `for` ciclo.

>[!NOTE]
>Solo per C++,
>- Potrebbe essere necessario qualificare il contesto di un nome di variabile o di un'espressione che usa un nome di variabile. Il contesto è la funzione, il file di origine o il modulo in cui si trova una variabile. Se è necessario qualificare il contesto, usare la sintassi dell'operatore di contesto [(C++)](../debugger/context-operator-cpp.md) in **Nome** nella finestra **Espressione di** controllo.
>
>- È possibile aggiungere nomi di registro e nomi di variabili **$\<register&nbsp;name>** usando o al **@\<register&nbsp;name>** **nome** nella finestra **Espressioni di** controllo. Per altre informazioni, vedere [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Usare espressioni in un finestra Espressioni di controllo

È possibile osservare qualsiasi espressione valida riconosciuta dal debugger in una **finestra Espressione di** controllo.

Ad esempio, per il codice nella sezione precedente, è possibile ottenere la media dei tre valori immettendo `(a + b + c) / 3` nella finestra Espressioni **di** controllo:

![Espressione di controllo](../debugger/media/watchexpression.png "Espressione di controllo")

Le regole per la valutazione delle espressioni nella finestra **Espressione** di controllo sono in genere le stesse regole per la valutazione delle espressioni nel linguaggio del codice. Se un'espressione presenta un errore di sintassi, prevedere lo stesso errore del compilatore nell'editor di codice. Ad esempio, un errore di digitazione nell'espressione precedente genera questo errore nella **finestra Espressioni di** controllo:

![Errore dell'espressione di controllo](../debugger/media/watchexpressionerror.png "Errore dell'espressione di controllo")

Nella finestra Espressioni di controllo può  essere visualizzato un cerchio con due linee ondulate. Questa icona indica che il debugger non valuta l'espressione a causa di una potenziale dipendenza tra thread. La valutazione del codice richiede l'esecuzione temporanea di altri thread nell'app, ma poiché si è in modalità di interruzione, tutti i thread nell'app vengono in genere arrestati. Consentire l'esecuzione temporanea di altri thread può avere effetti imprevisti sullo stato dell'app e il debugger può ignorare eventi come punti di interruzione ed eccezioni su tali thread.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Cercare nel finestra Espressioni di controllo

È possibile cercare parole chiave nelle colonne Nome, Valore e Tipo della finestra **Espressioni** di controllo usando la barra di ricerca sopra ogni finestra. Premere INVIO o selezionare una delle frecce per eseguire una ricerca. Per annullare una ricerca in corso, selezionare l'icona "x" nella barra di ricerca.

Usare rispettivamente le frecce sinistra e destra (MAIUSC+F3 e F3) per spostarsi tra le corrispondenze trovate.

![Cerca nella finestra Espressioni di controllo](../debugger/media/ee-search-watch.png "Cerca nella finestra Espressioni di controllo")

Per rendere la ricerca più o  meno completa, usare  l'elenco a discesa Cerca più in profondità nella parte superiore della finestra Espressioni di controllo per selezionare il numero di livelli di profondità in cui eseguire la ricerca in oggetti annidati. 

## <a name="pin-properties-in-the-watch-window"></a>Aggiungere le proprietà nel finestra Espressioni di controllo

>[!NOTE]
> Questa funzionalità è supportata in .NET Core 3.0 o versione successiva.

È possibile esaminare rapidamente gli oggetti in base alle relative proprietà nel finestra Espressioni di controllo con lo **strumento Proprietà pinnable.**  Per usare questo strumento, passare il puntatore del mouse su una  proprietà e selezionare l'icona della puntina visualizzata oppure fare clic con il pulsante destro del mouse e scegliere l'opzione Aggiungi membro come preferito nel menu di scelta rapida risultante.  Questa proprietà viene visualizzata nella parte superiore dell'elenco delle proprietà dell'oggetto e il nome e il valore della proprietà vengono visualizzati nella **colonna** Valore.  Per rimuovere una proprietà, selezionare di nuovo l'icona aggiungi o selezionare l'opzione Rimuovi membro **come** preferito nel menu di scelta rapida.

![Aggiungere le proprietà nel finestra Espressioni di controllo](../debugger/media/basic-pin-watch.gif "Aggiungere le proprietà nel finestra Espressioni di controllo")

È anche possibile attivare o disattivare i nomi delle proprietà e filtrare le proprietà non bloccate quando si visualizza l'elenco delle proprietà dell'oggetto nel finestra Espressioni di controllo.  È possibile accedere a entrambe le opzioni selezionando i pulsanti nella barra degli strumenti sopra la finestra espressioni di controllo.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> Aggiornare i valori delle espressioni di controllo

Quando viene valutata un'espressione, nella finestra **Espressione di** controllo potrebbe essere visualizzata un'icona di aggiornamento (freccia circolare). L'icona di aggiornamento indica un errore o un valore non aggiornato.

Per aggiornare il valore, selezionare l'icona di aggiornamento o premere la barra spaziatrice. Il debugger tenta di rivalutare l'espressione. Tuttavia, potrebbe non essere necessario o essere in grado di rivalutare l'espressione, a seconda del motivo per cui il valore non è stato valutato.

Passare il mouse sull'icona di aggiornamento o vedere la colonna **Valore** per il motivo per cui l'espressione non è stata valutata. I motivi includono:

- Si è verificato un errore durante la valutazione dell'espressione, come nell'esempio precedente. È possibile che si verifichi un timeout o che una variabile non sia in ambito.

- L'espressione ha una chiamata di funzione che può attivare un effetto collaterale nell'app. Vedere [Effetti collaterali delle espressioni](#bkmk_sideEffects).

- La valutazione automatica delle proprietà e delle chiamate di funzione implicite è disabilitata.

Se l'icona di aggiornamento viene visualizzata perché la valutazione automatica delle proprietà e delle chiamate di funzione implicite è disabilitata, è possibile abilitarla selezionando Abilita valutazione proprietà e altre chiamate di funzione **implicite** **in** Opzioni degli strumenti  >    >  **Debug**  >  **generale**.

Per illustrare l'uso dell'icona di aggiornamento:

1. In **Opzioni degli** strumenti Debug generale deselezionare la casella di controllo Abilita valutazione delle proprietà e altre chiamate di funzione  >    >    >   **implicite.**

1. Immettere il codice seguente e nella finestra **Espressioni** di controllo impostare un controllo sulla `list.Count` proprietà .

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Avviare il debug. La **finestra Espressioni** di controllo mostra un messaggio simile al seguente:

   ![Aggiornare l'orologio](../debugger/media/refreshwatch.png "Aggiornare l'orologio")

1. Per aggiornare il valore, selezionare l'icona di aggiornamento o premere la barra spaziatrice. Il debugger rivaluta l'espressione.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> Effetti collaterali delle espressioni

La valutazione di alcune espressioni può modificare il valore di una variabile o influire in altro modo sullo stato dell'app. La valutazione della seguente espressione, ad esempio, comporta la modifica del valore di `var1`:

```csharp
var1 = var2
```

Questo codice può causare un [effetto collaterale.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) Gli effetti collaterali possono rendere più difficile il debug modificando il funzionamento dell'app.

Un'espressione con effetti collaterali viene valutata una sola volta, quando viene immessa per la prima volta. Successivamente, l'espressione viene visualizzata in grigio nella finestra **Espressione di** controllo e altre valutazioni sono disabilitate. La descrizione **comando o** la colonna Valore spiega che l'espressione causa un effetto collaterale. È possibile forzare la rivalutazione selezionando l'icona di aggiornamento visualizzata accanto al valore.

Un modo per impedire la designazione degli effetti collaterali è disattivare la valutazione automatica delle funzioni. In **Opzioni degli strumenti**  >    >  **Debug**  >  **generale** deselezionare **Abilita valutazione delle proprietà e altre chiamate di funzione implicite.**

Solo per C#, quando la valutazione delle proprietà o delle chiamate di funzione implicite  è disattivata, è possibile forzare la valutazione aggiungendo il modificatore di formato **ac** a un nome di variabile nella **finestra Espressione di** controllo. Vedere [Identificatori di formato in C#.](../debugger/format-specifiers-in-csharp.md)

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>Usare gli ID oggetto nel finestra Espressioni di controllo (C# e Visual Basic)

A volte si vuole osservare il comportamento di un oggetto specifico. Ad esempio, potrebbe essere necessario tenere traccia di un oggetto a cui fa riferimento una variabile locale dopo che tale variabile è uscita dall'ambito. In C# e Visual Basic è possibile creare ID oggetto per istanze specifiche di tipi riferimento e usarli nella finestra **Espressioni** di controllo e nelle condizioni del punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.

> [!NOTE]
> Gli ID oggetto creano riferimenti deboli che non impediscono il Garbage Collection dell'oggetto. Sono validi solo per la sessione di debug corrente.

Nel codice seguente il metodo `MakePerson()` crea un oggetto usando una variabile `Person` locale:

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

Per trovare il nome di nel metodo , è possibile aggiungere un riferimento `Person` `DoSomething()` `Person` all'ID oggetto nella finestra Espressioni **di** controllo.

1. Impostare un punto di interruzione nel codice dopo la `Person` creazione dell'oggetto .

1. Avviare il debug.

1. Quando l'esecuzione viene sospesa in corrispondenza del punto di interruzione, aprire la finestra Variabili **locali** scegliendo  >  **Debug Windows**  >  **Variabili locali**.

1. Nella finestra **Variabili locali fare** clic con il pulsante destro del mouse sulla variabile e scegliere Crea ID `Person` **oggetto**.

   Verrà visualizzato un segno di dollaro ( ) più un numero nella finestra Variabili **$** locali, ovvero  l'ID oggetto.

1. Aggiungere l'ID oggetto alla finestra **Espressioni di** controllo facendo clic con il pulsante destro del mouse sull'ID oggetto e scegliendo Aggiungi espressioni **di controllo**.

1. Impostare un altro punto di interruzione nel `DoSomething()` metodo .

1. Continuare il debug. Quando l'esecuzione viene sospesa `DoSomething()` nel metodo , nella finestra Espressioni **di** controllo viene visualizzato l'oggetto `Person` .

   > [!NOTE]
   > Per visualizzare le proprietà dell'oggetto, ad esempio , è necessario abilitare la valutazione delle proprietà selezionando Opzioni degli strumenti Debug Generale Abilitare la valutazione delle proprietà e `Person.Name`   >    >    >    >  **altre chiamate di funzione implicite.**

## <a name="dynamic-view-and-the-watch-window"></a>Visualizzazione dinamica e finestra Espressioni di controllo

Alcuni linguaggi di scripting (ad esempio JavaScript o Python) usano la digitazione dinamica o [papera](https://en.wikipedia.org/wiki/Duck_typing) e .NET versione 4.0 e successive supporta oggetti difficili da osservare nelle normali finestre di debug.

Nella **finestra Espressioni** di controllo questi oggetti vengono visualizzati come oggetti dinamici, creati dai tipi che implementano l'interfaccia <xref:System.Dynamic.IDynamicMetaObjectProvider> . I nodi oggetto dinamico mostrano i membri dinamici degli oggetti dinamici, ma non consentono la modifica dei valori dei membri.

Per aggiornare **i valori di Visualizzazione** dinamica, selezionare [l'icona di aggiornamento](#bkmk_refreshWatch) accanto al nodo oggetto dinamico.

Per visualizzare solo la **visualizzazione dinamica per** un oggetto, aggiungere un identificatore di formato dinamico dopo il nome dell'oggetto dinamico nella finestra Espressione **di** controllo: 

- Per C#: `ObjectName, dynamic`
- Per Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Il debugger C# non rivaluta automaticamente i valori in **Visualizzazione** dinamica quando si esegue un'istruzione alla riga di codice successiva.
>- Il debugger Visual Basic aggiorna automaticamente le espressioni aggiunte tramite **la visualizzazione dinamica.**
>- La valutazione dei membri di una **visualizzazione dinamica** può avere [effetti collaterali.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))

**Per inserire una nuova variabile watch che esegue il cast di un oggetto in un oggetto dinamico:**

1. Fare clic con il pulsante destro del mouse su qualsiasi elemento figlio **di una visualizzazione dinamica.**
1. Scegliere **Aggiungi espressioni di controllo**. Diventa `object.name` e viene visualizzato in una nuova finestra Espressioni `((dynamic) object).name` **di** controllo.

Il debugger aggiunge anche un **nodo figlio di** Visualizzazione dinamica dell'oggetto alla finestra **Auto.** Per aprire la **finestra Auto,** durante il debug selezionare  >  **Debug Windows** auto  >  **.**

**La visualizzazione dinamica** migliora anche il debug per gli oggetti COM. Quando il debugger arriva a un oggetto COM di cui è stato eseguito **il wrapping** in System.__ComObject , aggiunge un nodo **di visualizzazione** dinamica per l'oggetto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Osservare una singola variabile o espressione con QuickWatch

È possibile usare **QuickWatch** per osservare una singola variabile.

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

Per osservare la `a` variabile,

1. Impostare un punto di interruzione nella riga `a = a + b;` .

1. Avviare il debug. L'esecuzione viene sospesa in corrispondenza del punto di interruzione.

1. Selezionare la `a` variabile nel codice.

1. Selezionare **Debug**  >  **QuickWatch**, premere **MAIUSC** + **F9** oppure fare clic con il pulsante destro del mouse e **scegliere QuickWatch**.

   Verrà **visualizzata la finestra di** dialogo Controllo immediato. La `a` variabile si trova nella casella **Espressione** con **valore** pari a **1.**

   ![Variabile QuickWatch](../debugger/media/quickwatchvariable.png "Variabile QuickWatch")

1. Per valutare un'espressione usando la variabile , digitare un'espressione come nella casella Espressione e `a + b` selezionare **Rivaluta .** 

   ![Espressione controllo immediato](../debugger/media/quickwatchexpression.png "Espressione di controllo immediato")

1. Per aggiungere la variabile o l'espressione **da Controllo immediato** alla finestra Espressione **di** controllo, selezionare Aggiungi espressione **di controllo**.

1. Selezionare **Chiudi** per chiudere la **finestra Controllo** immediato. **(QuickWatch** è una finestra di dialogo modale, quindi non è possibile continuare a eseguire il debug finché è aperta).

1. Continuare il debug. È possibile osservare la variabile nella **finestra Espressioni di** controllo.

## <a name="see-also"></a>Vedi anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
- [Prima di tutto esaminare il debug](../debugger/debugger-feature-tour.md)
- [Finestre del debugger](../debugger/debugger-windows.md)
