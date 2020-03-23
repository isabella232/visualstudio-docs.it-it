---
title: Impostare un orologio sulle variabili . Documenti Microsoft
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
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302007"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Espressioni di controllo con le finestre Espressioni di controllo e Controllo immediato

Durante il debug, è possibile utilizzare le finestre **Espressioni** di controllo e **controllo immediato** per controllare variabili ed espressioni. Le finestre sono disponibili solo durante una sessione di debug.

**Le** finestre di espressioni di controllo possono visualizzare diverse variabili alla volta durante il debug. La finestra di dialogo **Controllo informazioni rapide** visualizza una singola variabile alla volta e deve essere chiusa prima di continuare il debug.

Se questa è la prima volta che si tenta di eseguire il debug del codice, si consiglia di leggere [Debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) e [tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md) prima di passare attraverso questo articolo.

## <a name="observe-variables-with-a-watch-window"></a>Osservare le variabili con una finestra Espressioni di controlloObserve variables with a Watch window

È possibile aprire più di una finestra **Espressioni di controllo** e osservare più di una variabile in una finestra Espressioni di **controllo.**

Ad esempio, per impostare un `a` `b`controllo `c` sui valori di , , e nel codice seguente:

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

1. Impostare un `c = a + b;` punto di interruzione sulla riga facendo clic sul margine sinistro, selezionando **Debug** > **Toggle Breakpoint**o premendo **F9**.

1. Avviare il debug selezionando la freccia verde **Start** o **Debug debug** > **Start Debugging**oppure premere **F5.** L'esecuzione viene sospesa in corrispondenza del punto di interruzione.

1. Aprire una finestra **Espressioni di controllo** selezionando Esegui **debug** > espressioni di**controllo** > **di Windows** > **o**premendo **CTRL**+**Alt**+**W** > **1**.

   È possibile aprire altre finestre **Espressioni di controllo** selezionando le finestre **2**, **3**o **4**.

1. Nella finestra **Espressioni di controllo** selezionare `a`una riga vuota e digitare variabile . Fare lo `b` stesso `c`per e .

   ![Variabili di controllo](../debugger/media/watchvariables.png "WatchVariables")

1. Continuare il debug selezionando **Esegui debug** > **in** o premendo **F11** in base alle esigenze per avanzare. I valori delle variabili nella finestra Espressioni `for` di **controllo** cambiano durante l'iterazione del ciclo.

>[!NOTE]
>Solo per il sistema Di tipo C,
>- Potrebbe essere necessario qualificare il contesto di un nome di variabile o di un'espressione che utilizza un nome di variabile. Il contesto è la funzione, il file di origine o il modulo in cui si trova una variabile. Se è necessario qualificare il contesto, utilizzare la sintassi dell'operatore di [contesto (C)](../debugger/context-operator-cpp.md) nel **nome** nella finestra **Espressioni di controllo.**
>
>- È possibile aggiungere nomi di registro e nomi di **Name** variabili utilizzando ** $ \<il nome&nbsp;** del registro>o ** @ \<&nbsp;** il nome del registro>al nome nella finestra **Espressioni di controllo.** Per altre informazioni, vedere [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Usare espressioni in una finestra Espressioni di controlloUse expressions in a Watch window

È possibile osservare qualsiasi espressione valida riconosciuta dal debugger in una finestra **Espressioni di controllo.**

Ad esempio, per il codice nella sezione precedente, è possibile ottenere `(a + b + c) / 3` la media dei tre valori immettendo nella finestra **Espressioni** di controllo:

![Espressione di controllo](../debugger/media/watchexpression.png "Espressione di controllo")

Le regole per la valutazione delle espressioni nella finestra Espressioni di **controllo** sono in genere le stesse delle regole per la valutazione delle espressioni nel linguaggio del codice. Se un'espressione presenta un errore di sintassi, si prevede lo stesso errore del compilatore come nell'editor di codice. Ad esempio, un errore di battitura nell'espressione precedente genera questo errore nella finestra Espressioni di controllo:For example, a **typo** in the preceding expression produces this error in the Watch window:

![Errore dell'espressione di controllo](../debugger/media/watchexpressionerror.png "Errore dell'espressione di controllo")

Nella finestra **Espressioni di controllo** potrebbe essere visualizzato un cerchio con due linee ondulate. Questa icona indica che il debugger non valuta l'espressione a causa di una potenziale dipendenza cross-thread. La valutazione del codice richiede l'esecuzione temporanea di altri thread nell'app, ma poiché è attiva la modalità di interruzione, tutti i thread dell'app vengono in genere arrestati. Consentire l'esecuzione temporanea di altri thread può avere effetti imprevisti sullo stato dell'app e il debugger può ignorare eventi quali punti di interruzione ed eccezioni su tali thread.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Ricerca nella finestra Espressioni di controllo

È possibile cercare le parole chiave nelle colonne Nome, Valore e Tipo della finestra Espressioni di **controllo** utilizzando la barra di ricerca sopra ogni finestra. Premere INVIO o selezionare una delle frecce per eseguire una ricerca. Per annullare una ricerca in corso, seleziona l'icona "x" nella barra di ricerca.

Utilizzate le frecce sinistra e destra (rispettivamente Maiusc-F3 e F3) per navigare tra le corrispondenze trovate.

![Cerca nella finestra Espressioni di controllo](../debugger/media/ee-search-watch.png "Cerca nella finestra Espressioni di controllo")

Per rendere la ricerca più o meno approfondita, utilizzare il menu a discesa **Cerca più profondo** nella parte superiore della finestra Espressioni di **controllo** per selezionare il numero di livelli di profondità da cercare negli oggetti nidificati. 

## <a name="pin-properties-in-the-watch-window"></a>Aggiungere proprietà nella finestra Espressioni di controllo

>[!NOTE]
> Questa funzionalità è supportata in .NET Core 3.0 o versione successiva.

È possibile esaminare rapidamente gli oggetti in base alle relative proprietà nella finestra Espressioni di controllo con lo strumento **Proprietà Pinnable.**  Per utilizzare questo strumento, passare il mouse su una proprietà e selezionare l'icona a forma di puntina visualizzata o fare clic con il pulsante destro del mouse e selezionare l'opzione **Aggiungi membro come preferito** nel menu di scelta rapida risultante.  In questo modo tale proprietà viene propagata all'inizio dell'elenco delle proprietà dell'oggetto e il nome e il valore della proprietà vengono visualizzati nella colonna **Valore.**  Per sbloccare una proprietà, selezionare nuovamente l'icona a forma di puntina o selezionare l'opzione **Rimuovi membro come preferito** nel menu di scelta rapida.

![Aggiungere proprietà nella finestra Espressioni di controllo](../debugger/media/basic-pin-watch.gif "Aggiungere proprietà nella finestra Espressioni di controllo")

È inoltre possibile attivare o disattivare i nomi delle proprietà e filtrare le proprietà non bloccate quando si visualizza l'elenco delle proprietà dell'oggetto nella finestra Espressioni di controllo.  È possibile accedere a entrambe le opzioni selezionando i pulsanti nella barra degli strumenti sopra la finestra di controllo.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>Aggiornare i valori dell'orologio

Quando viene valutata un'espressione, è possibile che nella finestra **Espressioni di controllo** venga visualizzata un'icona di aggiornamento (freccia circolare). L'icona di aggiornamento indica un errore o un valore non aggiornato.

Per aggiornare il valore, selezionare l'icona di aggiornamento o premere la barra spaziatrice. Il debugger tenta di rivalutare l'espressione. Tuttavia, potrebbe non essere necessario o essere in grado di rivalutare l'espressione, a seconda del motivo per cui il valore non è stato valutato.

Passare il puntatore del mouse sull'icona di aggiornamento o visualizzare la colonna **Valore** per il motivo per cui l'espressione non è stata valutata. I motivi includono:

- Si è verificato un errore durante la valutazione dell'espressione, come nell'esempio precedente. Potrebbe verificarsi un timeout o una variabile potrebbe essere esterno all'ambito.

- L'espressione ha una chiamata di funzione che potrebbe attivare un effetto collaterale nell'app. Consultate [Effetti collaterali espressione.](#bkmk_sideEffects)

- La valutazione automatica delle proprietà e delle chiamate di funzione implicite è disabilitata.

Se l'icona di aggiornamento viene visualizzata perché la valutazione automatica delle proprietà e delle chiamate di funzione implicite è disabilitata, è possibile attivarla selezionando Abilita valutazione proprietà e altre chiamate di **funzione implicite** in **Strumenti** > **Opzioni** > **debug** > **generale**.

Per illustrare l'utilizzo dell'icona di aggiornamento:

1. In **Tools** > **Strumenti Opzioni** > **debug** > **Generale**deselezionare la casella di controllo Abilita valutazione proprietà e altre chiamate di funzione **implicite** .

1. Immettere il codice seguente e nella finestra Espressioni `list.Count` di **controllo** impostare un controllo sulla proprietà.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Avviare il debug. La finestra **Espressioni di controllo** mostra qualcosa di simile al seguente:

   ![Aggiorna orologio](../debugger/media/refreshwatch.png "Aggiorna orologio")

1. Per aggiornare il valore, selezionare l'icona di aggiornamento o premere la barra spaziatrice. Il debugger rivaluta l'espressione.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>Effetti collaterali dell'espressione

La valutazione di alcune espressioni può modificare il valore di una variabile o influire in altro modo sullo stato dell'app. La valutazione della seguente espressione, ad esempio, comporta la modifica del valore di `var1`:

```csharp
var1 = var2
```

Questo codice può causare un [effetto collaterale](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Gli effetti collaterali possono rendere più difficile il debug modificando il funzionamento dell'app.

Un'espressione con effetti collaterali viene valutata una sola volta, quando viene immessa per la prima volta. Successivamente, l'espressione viene visualizzata in grigio nella finestra **Espressioni di controllo** e ulteriori valutazioni sono disabilitate. La descrizione comando o la colonna **Valore** spiega che l'espressione causa un effetto collaterale. È possibile forzare la rivalutazione selezionando l'icona di aggiornamento visualizzata accanto al valore.

Un modo per impedire la designazione degli effetti collaterali consiste nel disattivare la valutazione automatica della funzione. In **Tools** > **Strumenti Opzioni** > **debug** > **Generale**deselezionare Abilita valutazione proprietà e altre chiamate di funzione **implicite**.

Solo per il linguaggio C, quando la valutazione delle proprietà o delle chiamate di funzione implicite è disattivata, è possibile forzare la valutazione aggiungendo il modificatore di formato **ac** a una variabile **Name** nella finestra **Espressioni di controllo.** Vedere [Identificatori di formato in C .](../debugger/format-specifiers-in-csharp.md)

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>Utilizzare gli ID oggetto nella finestra Espressioni di controllo (C

A volte si desidera osservare il comportamento di un oggetto specifico. Ad esempio, è possibile tenere traccia di un oggetto a cui fa riferimento una variabile locale dopo che tale variabile è uscita dall'ambito. In Visual Basic e Visual Basic è possibile creare ID oggetto per istanze specifiche di tipi di riferimento e utilizzarli nella finestra **Espressioni di** controllo e nelle condizioni dei punti di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.

> [!NOTE]
> Gli ID oggetto creano riferimenti deboli che non impediscono la garbage collection dell'oggetto. Sono validi solo per la sessione di debug corrente.

Nel codice seguente, `MakePerson()` il `Person` metodo crea un using una variabile locale:In the following code, the method creates a using a local variable:

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

Per scoprire il nome `Person` del `DoSomething()` nel metodo, è possibile `Person` aggiungere un riferimento all'ID oggetto nella finestra **Espressioni di controllo.**

1. Impostare un punto di `Person` interruzione nel codice dopo la creazione dell'oggetto.

1. Avviare il debug.

1. Quando l'esecuzione viene sospesa in corrispondenza del punto di interruzione, aprire la finestra **Variabili locali** scegliendo **Debug** > variabili**locali**di**Windows** > .

1. Nella finestra **Variabili locali,** fare `Person` clic con il pulsante destro del mouse sulla variabile e selezionare **Crea ID oggetto**.

   Verrà visualizzato un simbolo**$** del dollaro ( ) più un numero nella finestra **Variabili locali,** ovvero l'ID oggetto.

1. Aggiungere l'ID oggetto alla finestra **Espressioni di controllo** facendo clic con il pulsante destro del mouse sull'ID oggetto e scegliendo Aggiungi **controllo**.

1. Impostare un `DoSomething()` altro punto di interruzione nel metodo .

1. Continuare il debug. Quando l'esecuzione `DoSomething()` viene sospesa nel `Person` metodo, nella finestra Espressioni di **controllo** viene visualizzato l'oggetto .

   > [!NOTE]
   > Se si desidera visualizzare le proprietà dell'oggetto, `Person.Name`ad esempio , è necessario abilitare la valutazione delle proprietà selezionando **Strumenti** > **opzioni** > di**debug** > **Generale** > Abilita valutazione proprietà e altre chiamate di funzione**implicite**.

## <a name="dynamic-view-and-the-watch-window"></a>Visualizzazione dinamica e finestra Espressioni di controllo

Alcuni linguaggi di script (ad esempio, JavaScript o Python) usano la tipizzazione dinamica o [anatra](https://en.wikipedia.org/wiki/Duck_typing) e .NET versione 4.0 e successive supportano oggetti difficili da osservare nelle normali finestre di debug.

Nella finestra **Espressioni di** controllo questi oggetti vengono visualizzati <xref:System.Dynamic.IDynamicMetaObjectProvider> come oggetti dinamici, creati da tipi che implementano l'interfaccia. I nodi di oggetti dinamici mostrano i membri dinamici degli oggetti dinamici, ma non consentono la modifica dei valori dei membri.

Per aggiornare i valori di **Visualizzazione dinamica,** selezionare l'icona di [aggiornamento](#bkmk_refreshWatch) accanto al nodo dell'oggetto dinamico.

Per visualizzare solo la **visualizzazione dinamica** per un oggetto, aggiungere un identificatore di formato **dinamico** dopo il nome dell'oggetto dinamico nella finestra **Espressioni di controllo:**

- Per C#: `ObjectName, dynamic`
- Per Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Quando si passa alla riga di codice successiva, il debugger di Cè non rivaluta automaticamente i valori in **Visualizzazione dinamica.**
>- Il debugger di Visual Basic aggiorna automaticamente le espressioni aggiunte tramite la **visualizzazione dinamica**.
>- La valutazione dei membri di una **visualizzazione dinamica** può avere [effetti collaterali.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))

**Per inserire una nuova variabile di controllo che esegue il cast di un oggetto in un oggetto dinamico:**

1. Fare clic con il pulsante destro del mouse su un elemento figlio di una **visualizzazione dinamica**.
1. Scegliere **Aggiungi orologio**. Diventa `object.name` `((dynamic) object).name` e viene visualizzato in una nuova finestra **Espressioni di controllo.**

Il debugger aggiunge anche un nodo figlio **Visualizzazione dinamica** dell'oggetto per il **Auto** finestra. Per aprire la finestra **Auto,** durante il debug selezionare **Debug** > **auto di****Windows** > .

**Visualizzazione dinamica** migliora anche il debug per gli oggetti COM. Quando il debugger arriva a un oggetto COM di cui è stato eseguito il wrapping in **System.__ComObject**, aggiunge un nodo **Visualizzazione dinamica** per l'oggetto.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Osservare una singola variabile o espressione con Controllo rapido immagine rapidaObserve a single variable or expression with QuickWatch

È possibile utilizzare **Controllo veloce** per osservare una singola variabile.

Ad esempio, per il codice seguente:For example, for the following code:

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

1. Selezionare `a` la variabile nel codice.

1. Selezionare **Debug** > **QuickWatch**, premere **Maiusc**+**F9**oppure fare clic con il pulsante destro del mouse e scegliere Controllo **veloce**.

   Viene visualizzata la finestra di dialogo **Controllo rapido.** La `a` variabile si trova nella casella **Espressione** con **valore** **1**.

   ![Variabile QuickWatch](../debugger/media/quickwatchvariable.png "Variabile QuickWatch")

1. Per valutare un'espressione utilizzando la variabile, digitare un'espressione, ad `a + b` esempio nella casella **Espressione,** quindi selezionare **Rivaluta**.

   ![Espressione di Controllo rapido](../debugger/media/quickwatchexpression.png "Espressione di Controllo rapido")

1. Per aggiungere la variabile o l'espressione da **Controllo rapido** alla finestra Espressioni **di controllo,** selezionare **Aggiungi espressione di controllo**.

1. Selezionare **Chiudi** per chiudere la finestra **Controllo rapido.** (Controllo**rapido** è una finestra di dialogo modale, pertanto non è possibile continuare il debug finché è aperto.)

1. Continuare il debug. È possibile osservare la variabile nella finestra **Espressioni di controllo.**

## <a name="see-also"></a>Vedere anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
- [Primo sguardo al debug](../debugger/debugger-feature-tour.md)
- [Finestre del debugger](../debugger/debugger-windows.md)
