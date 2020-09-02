---
title: Impostare un'espressione di controllo sulle variabili | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: how-to
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
ms.openlocfilehash: 6ab66089de25b7648b13e1ba05f88ab55b7868df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348028"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Osservare le variabili con le finestre espressioni di controllo e controllo immediato

Durante il debug, è possibile usare le finestre **espressioni di controllo** e controllo **immediato** per controllare variabili ed espressioni. Le finestre sono disponibili solo durante una sessione di debug.

Le finestre **espressioni di controllo** possono visualizzare diverse variabili alla volta durante il debug. La finestra di dialogo controllo **immediato** Visualizza una singola variabile alla volta e deve essere chiusa prima che il debug possa continuare.

Se è la prima volta che si tenta di eseguire il debug del codice, è consigliabile leggere il [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) e [tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md) prima di procedere con questo articolo.

## <a name="observe-variables-with-a-watch-window"></a>Osservare le variabili con una finestra Espressioni di controllo

È possibile aprire più di una finestra **espressioni di controllo** e osservare più di una variabile in una finestra espressioni di **controllo** .

Ad esempio, per impostare un'espressione di controllo sui valori di `a` , `b` e `c` nel codice seguente:

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

1. Impostare un punto di interruzione sulla `c = a + b;` riga facendo clic sul margine sinistro, selezionando **debug**  >  **Imposta/Rimuovi**punto di interruzione oppure premendo **F9**.

1. Avviare il debug selezionando la freccia di **avvio** verde o **debug**  >  **Avvia debug**o premere **F5**. L'esecuzione viene sospesa in corrispondenza del punto di interruzione.

1. Aprire una finestra **espressioni di controllo** selezionando **debug**  >  **Windows**  >  **Watch**  >  **Watch 1**o premendo **CTRL** + **ALT** + **W**  >  **1**.

   È possibile aprire finestre **espressioni di controllo** aggiuntive selezionando Windows **2**, **3**o **4**.

1. Nella finestra **espressioni di controllo** selezionare una riga vuota e digitare Variable `a` . Eseguire la stessa operazione per `b` e `c` .

   ![Controllare le variabili](../debugger/media/watchvariables.png "WatchVariables")

1. Continuare il debug selezionando **debug**  >  **Esegui istruzione** o premendo **F11** secondo le necessità per avanzare. I valori delle variabili nella finestra **espressioni di controllo** cambiano durante l'iterazione del `for` ciclo.

>[!NOTE]
>Solo per C++,
>- Potrebbe essere necessario qualificare il contesto di un nome di variabile oppure un'espressione che utilizza un nome di variabile. Il contesto è la funzione, il file di origine o il modulo in cui si trova una variabile. Se è necessario qualificare il contesto, usare la sintassi dell' [operatore di contesto (C++)](../debugger/context-operator-cpp.md) nel **nome** nella finestra **espressioni di controllo** .
>
>- È possibile aggiungere nomi di registro e nomi di variabili usando **$\<register&nbsp;name>** o **@\<register&nbsp;name>** al **nome** nella finestra **espressioni di controllo** . Per altre informazioni, vedere [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Usare espressioni in un finestra Espressioni di controllo

È possibile osservare qualsiasi espressione valida riconosciuta dal debugger in una finestra **espressioni di controllo** .

Per il codice nella sezione precedente, ad esempio, è possibile ottenere la media dei tre valori immettendo `(a + b + c) / 3` nella finestra **espressioni di controllo** :

![Espressione espressione di controllo](../debugger/media/watchexpression.png "Espressione espressione di controllo")

Le regole per la valutazione delle espressioni nella finestra espressioni di **controllo** sono in genere le stesse delle regole per la valutazione delle espressioni nel linguaggio del codice. Se un'espressione presenta un errore di sintassi, prevedere lo stesso errore del compilatore dell'editor di codice. Ad esempio, un errore di digitazione nell'espressione precedente genera questo errore nella finestra **espressioni di controllo** :

![Errore espressione espressione di controllo](../debugger/media/watchexpressionerror.png "Errore espressione espressione di controllo")

Un cerchio con due icone ondulate può essere visualizzato nella finestra **espressioni di controllo** . Questa icona indica che il debugger non valuta l'espressione a causa di una potenziale dipendenza cross-thread. La valutazione del codice richiede l'esecuzione temporanea di altri thread nell'app, ma poiché ci si trova in modalità di interruzione, in genere tutti i thread nell'app vengono arrestati. Consentire l'esecuzione temporanea di altri thread può avere effetti imprevisti sullo stato dell'app e il debugger può ignorare eventi quali i punti di interruzione e le eccezioni in tali thread.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Cerca nel finestra Espressioni di controllo

È possibile cercare le parole chiave nelle colonne nome, valore e tipo della finestra **espressioni di controllo** usando la barra di ricerca sopra ogni finestra. Premere INVIO o selezionare una delle frecce per eseguire una ricerca. Per annullare una ricerca in corso, selezionare l'icona "x" nella barra di ricerca.

Utilizzare le frecce sinistra e destra (MAIUSC + F3 e F3 rispettivamente) per spostarsi tra le corrispondenze trovate.

![Cerca nella finestra espressioni di controllo](../debugger/media/ee-search-watch.png "Cerca nella finestra espressioni di controllo")

Per rendere la ricerca più o meno completa, usare l'elenco a discesa Cerca più a **fondo** nella parte superiore della finestra **espressioni di controllo** per selezionare il numero di livelli che si desidera cercare negli oggetti annidati. 

## <a name="pin-properties-in-the-watch-window"></a>Aggiungere le proprietà nella finestra Espressioni di controllo

>[!NOTE]
> Questa funzionalità è supportata in .NET Core 3,0 o versione successiva.

È possibile esaminare rapidamente gli oggetti in base alle relative proprietà nel finestra Espressioni di controllo con lo strumento **Proprietà aggiungibili** .  Per usare questo strumento, passare il puntatore del mouse su una proprietà e selezionare l'icona a forma di puntina visualizzata oppure fare clic con il pulsante destro del mouse e selezionare l'opzione **Aggiungi membro come preferito** nel menu di scelta rapida risultante.  Questa operazione consente di eseguire il bubbling della proprietà nella parte superiore dell'elenco delle proprietà dell'oggetto e il nome e il valore della proprietà vengono visualizzati nella colonna **valore** .  Per Rimuovi una proprietà, selezionare di nuovo l'icona del PIN oppure selezionare il **membro Rimuovi come opzione preferita** nel menu di scelta rapida.

![Aggiungere le proprietà nella finestra Espressioni di controllo](../debugger/media/basic-pin-watch.gif "Aggiungere le proprietà nella finestra Espressioni di controllo")

È anche possibile impostare i nomi delle proprietà e filtrare le proprietà non bloccate quando si visualizza l'elenco delle proprietà dell'oggetto nel finestra Espressioni di controllo.  È possibile accedere a entrambe le opzioni selezionando i pulsanti sulla barra degli strumenti sopra la finestra espressioni di controllo.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> Aggiornare i valori delle espressioni di controllo

Quando viene valutata un'espressione, è possibile che venga visualizzata un'icona di aggiornamento (freccia circolare) nella finestra **espressioni di controllo** . L'icona di aggiornamento indica un errore o un valore non aggiornato.

Per aggiornare il valore, selezionare l'icona di aggiornamento o premere la barra spaziatrice. Il debugger tenta di rivalutare l'espressione. Tuttavia, potrebbe non essere necessario o essere in grado di rivalutare l'espressione, a seconda del motivo per cui il valore non è stato valutato.

Passare il mouse sull'icona di aggiornamento o visualizzare la colonna **valore** per il motivo per cui l'espressione non è stata valutata. I motivi includono:

- Si è verificato un errore durante la valutazione dell'espressione, come nell'esempio precedente. È possibile che si verifichi un timeout o che una variabile sia fuori dall'ambito.

- L'espressione ha una chiamata di funzione che può attivare un effetto collaterale nell'app. Vedere [effetti collaterali dell'espressione](#bkmk_sideEffects).

- La valutazione automatica delle proprietà e delle chiamate di funzione implicite è disabilitata.

Se viene visualizzata l'icona di aggiornamento perché la valutazione automatica delle proprietà e delle chiamate di funzione implicite è disabilitata, è possibile abilitarla selezionando **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite** in **strumenti**  >  **Opzioni**  >  **debug**  >  **generale**.

Per illustrare l'uso dell'icona di aggiornamento:

1. In **strumenti**  >  **Opzioni**  >  **debug**  >  **generale**deselezionare la casella di controllo **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite** .

1. Immettere il codice seguente e nella finestra **espressioni di controllo** impostare un'espressione di controllo sulla `list.Count` Proprietà.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Avviare il debug. Nella finestra **espressioni di controllo** viene visualizzato un messaggio simile al seguente:

   ![Aggiorna espressione di controllo](../debugger/media/refreshwatch.png "Aggiorna espressione di controllo")

1. Per aggiornare il valore, selezionare l'icona di aggiornamento o premere la barra spaziatrice. Il debugger rivaluterà l'espressione.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> Effetti collaterali dell'espressione

La valutazione di alcune espressioni può modificare il valore di una variabile o influire in altro modo sullo stato dell'app. La valutazione della seguente espressione, ad esempio, comporta la modifica del valore di `var1`:

```csharp
var1 = var2
```

Questo codice può causare un [effetto collaterale](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Gli effetti collaterali possono rendere più difficile il debug modificando la modalità di funzionamento dell'app.

Un'espressione con effetti collaterali viene valutata una sola volta, al momento della prima immissione. Successivamente, l'espressione viene visualizzata in grigio nella finestra **espressioni di controllo** e altre valutazioni sono disabilitate. Nella colonna Descrizione comando o **valore** viene illustrato che l'espressione causa un effetto collaterale. È possibile forzare la rivalutazione selezionando l'icona di aggiornamento visualizzata accanto al valore.

Un modo per evitare la designazione degli effetti collaterali consiste nel disattivare la valutazione automatica della funzione. In **strumenti**  >  **Opzioni**  >  **debug**  >  **generale**deselezionare **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**.

Solo per C#, quando la valutazione delle proprietà o delle chiamate di funzione implicite è disattivata, è possibile forzare la valutazione aggiungendo il modificatore di formato **AC** a un **nome** di variabile nella finestra **espressioni di controllo** . Vedere [identificatori di formato in C#](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> Usare gli ID oggetto nel finestra Espressioni di controllo (C# e Visual Basic)

A volte si vuole osservare il comportamento di un oggetto specifico. Ad esempio, potrebbe essere necessario tenere traccia di un oggetto a cui fa riferimento una variabile locale dopo che la variabile è uscita dall'ambito. In C# e Visual Basic è possibile creare ID oggetto per istanze specifiche dei tipi di riferimento e usarle nella finestra **espressioni di controllo** e nelle condizioni del punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.

> [!NOTE]
> Gli ID oggetto creano riferimenti deboli che non impediscono che l'oggetto venga sottoposta a Garbage Collection. Sono validi solo per la sessione di debug corrente.

Nel codice seguente il `MakePerson()` metodo crea un oggetto `Person` usando una variabile locale:

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

Per individuare il nome dell' `Person` `DoSomething()` oggetto nel metodo, è possibile aggiungere un riferimento all' `Person` ID oggetto nella finestra **espressioni di controllo** .

1. Impostare un punto di interruzione nel codice dopo la `Person` creazione dell'oggetto.

1. Avviare il debug.

1. Quando l'esecuzione viene sospesa in corrispondenza del punto di interruzione, aprire la finestra **variabili locali** scegliendo **debug**  >  **Windows**  >  **variabili locali**di Windows.

1. Nella finestra variabili **locali** , fare clic con il pulsante destro del mouse sulla `Person` variabile e scegliere **Crea ID oggetto**.

   Verrà visualizzato un segno di dollaro ( **$** ) più un numero nella finestra **variabili locali** , ovvero l'ID oggetto.

1. Aggiungere l'ID oggetto alla finestra **espressioni di controllo** facendo clic con il pulsante destro del mouse sull'ID oggetto e scegliendo Aggiungi espressione di **controllo**.

1. Impostare un altro punto di interruzione nel `DoSomething()` metodo.

1. Continuare il debug. Quando l'esecuzione viene sospesa nel `DoSomething()` metodo, nella finestra **espressioni di controllo** viene visualizzato l' `Person` oggetto.

   > [!NOTE]
   > Se si desidera visualizzare le proprietà dell'oggetto, ad esempio `Person.Name` , è necessario abilitare la valutazione delle proprietà selezionando **strumenti**  >  **Opzioni**  >  **debug**  >  **generale**  >  **Abilita valutazione proprietà e altre chiamate di funzioni implicite**.

## <a name="dynamic-view-and-the-watch-window"></a>Visualizzazione dinamica e finestra Espressioni di controllo

Alcuni linguaggi di script (ad esempio, JavaScript o Python) usano la tipizzazione dinamica o [Duck](https://en.wikipedia.org/wiki/Duck_typing) e .net versione 4,0 e successive supporta oggetti difficili da osservare nelle normali finestre di debug.

La finestra **espressioni di controllo** Visualizza questi oggetti come oggetti dinamici, che vengono creati da tipi che implementano l' <xref:System.Dynamic.IDynamicMetaObjectProvider> interfaccia. I nodi oggetto dinamici mostrano i membri dinamici degli oggetti dinamici, ma non consentono la modifica dei valori dei membri.

Per aggiornare i valori della **visualizzazione dinamica** , selezionare l' [icona di aggiornamento](#bkmk_refreshWatch) accanto al nodo oggetto dinamico.

Per visualizzare solo la **visualizzazione dinamica** per un oggetto, aggiungere un identificatore di formato **dinamico** dopo il nome dell'oggetto dinamico nella finestra **espressioni di controllo** :

- Per C#: `ObjectName, dynamic`
- Per Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Il debugger C# non rivaluta automaticamente i valori nella **visualizzazione dinamica** quando si esegue l'istruzione alla riga di codice successiva.
>- Il debugger Visual Basic aggiorna automaticamente le espressioni aggiunte tramite la **visualizzazione dinamica**.
>- La valutazione dei membri di una **visualizzazione dinamica** può avere [effetti collaterali](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Per inserire una nuova variabile Watch che esegue il cast di un oggetto in un oggetto dinamico:**

1. Fare clic con il pulsante destro del mouse su qualsiasi elemento figlio di una **visualizzazione dinamica**.
1. Scegliere **Aggiungi**espressione di controllo. Il `object.name` diventa `((dynamic) object).name` e viene visualizzato in una nuova finestra **espressioni di controllo** .

Il debugger aggiunge anche un nodo figlio **visualizzazione dinamica** dell'oggetto alla finestra **auto** . Per aprire la finestra **auto** , durante il debug selezionare **debug**di  >  **Windows**  >  **auto**.

La **visualizzazione dinamica** migliora anche il debug di oggetti com. Quando il debugger raggiunge un oggetto COM di cui è stato eseguito il wrapper in **System. __ComObject**, aggiunge un nodo della **visualizzazione dinamica** per l'oggetto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Osservare una singola variabile o espressione con controllo immediato

È possibile utilizzare controllo **immediato** per osservare una singola variabile.

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

1. Selezionare la variabile `a` nel codice.

1. Selezionare **Debug**controllo  >  **immediato**debug, premere **MAIUSC** + **F9**oppure fare clic con il pulsante destro del mouse e scegliere controllo **immediato**.

   Viene visualizzata la finestra di dialogo controllo **immediato** . La `a` variabile si trova nella casella **espressione** con un **valore** pari a **1**.

   ![Variabile controllo immediato](../debugger/media/quickwatchvariable.png "Variabile controllo immediato")

1. Per valutare un'espressione usando la variabile, digitare un'espressione come `a + b` nella casella **espressione** e selezionare **Rivaluta**.

   ![Espressione controllo immediato](../debugger/media/quickwatchexpression.png "Espressione controllo immediato")

1. Per aggiungere la variabile o l'espressione da controllo **immediato** alla finestra **espressioni di controllo** , selezionare Aggiungi espressione di **controllo**.

1. Selezionare **Chiudi** per chiudere la finestra controllo **immediato** . (Controllo**immediato** è una finestra di dialogo modale, pertanto non è possibile continuare il debug finché è aperto).

1. Continuare il debug. È possibile osservare la variabile nella finestra **espressioni di controllo** .

## <a name="see-also"></a>Vedere anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
- [Esaminare prima di tutto il debug](../debugger/debugger-feature-tour.md)
- [Finestre del debugger](../debugger/debugger-windows.md)
