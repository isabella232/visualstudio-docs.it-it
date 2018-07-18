---
title: Impostare un'espressione di controllo sulle variabili in Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/04/2017
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
ms.openlocfilehash: 71a29a5d8961688f710181dce553d0895a4bb475
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057161"
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Impostare un'espressione di controllo per le variabili utilizzando espressioni di controllo e controllo immediato Windows in Visual Studio
Durante il debug, è possibile usare la **Watch** e **controllo immediato** windows per controllare variabili ed espressioni.  La differenza è che la finestra **Espressioni di controllo** può visualizzare più variabili, mentre la finestra **Controllo immediato** visualizza una singola variabile alla volta. 

Le finestre sono disponibili solo durante una sessione di debug. Per aprire la **Watch** finestra, scegliere **Debug > Windows > espressioni di controllo > espressioni di controllo (1, 2, 3, 4)**). Per aprire la **controllo immediato** finestra: pulsante destro del mouse sulla variabile e scegliere **controllo immediato** oppure scegliere **Debug > controllo immediato**.
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Osservazione di una singola variabile con Controllo immediato  
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
  
 È possibile osservare una variabile nella finestra controllo immediato come segue:  
  
1.  Impostare un punto di interruzione nella riga `a = a + b;` .  
  
2.  Avviare il debug. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.  
  
3.  Aprire il **controllo immediato** finestra (fare clic su `a`, quindi scegliere **controllo immediato**, o selezionare `a` , quindi premere **MAIUSC+F9**).

    Dovrebbe essere una variabile nel **valori** finestra, con un valore pari a 1.

    ![Espressione di controllo immediato](../debugger/media/watchexpression.png "QuickWatchExpression")  

    Se si desidera valutare un'espressione che usa la variabile, aggiungere un'espressione, ad esempio `a + b` per il **espressione** finestra e fare clic su **Rivaluta**. 
  
4.  Aggiungere la variabile per il **Watch** finestra da **controllo immediato** facendo **Aggiungi espressione di controllo**. 

    > [!NOTE]
    > Il **controllo immediato** finestra è una finestra di dialogo modale, cui non è possibile continuare il debug finché è aperta.  
  
5.  Chiudere la finestra **Controllo immediato** . È ora possibile continuare il debug osservando il valore nella finestra **Espressioni di controllo** .  
  
## <a name="observing-variables-with-the-watch-window"></a>Osservazione delle variabili con la finestra Espressioni di controllo  
 È possibile osservare più variabili con la finestra **Espressioni di controllo** . Si supponga, ad esempio, di avere il codice seguente:  
  
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
  
 Aggiungere i valori delle tre variabili nella finestra Espressioni di controllo come segue:  
  
1.  Impostare un punto di interruzione nella riga `c = a + b;` .  
  
2.  Avviare i debug (**F5**). L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.  
  
3.  Aprire la finestra Espressioni di controllo (**Debug > Windows > espressione di controllo > espressione di controllo 1**, o **CTRL + ALT + W, 1**).  
  
4.  Aggiungere la variabile `a` nella prima riga, la variabile `b` nella seconda riga e la variabile `c` nella terza riga.

    È possibile aggiungere variabili facendo clic su una riga vuota e digitare il nome della variabile.
  
5.  Continuare il debug (premere **F11** per far avanzare il debugger).  
  
 I valori delle variabili cambieranno durante l'iterazione del ciclo `for` .  
  
 Se si programma in codice nativo, può essere necessario, in certi casi, qualificare il contesto di un nome di variabile o di un'espressione contenente un nome di variabile. Il contesto è rappresentato dalla funzione, il file di origine e il modulo in cui risiede una variabile. Se è necessario qualificare il contesto, è possibile usare la sintassi dell'operatore di contesto. Per altre informazioni, vedere [Context Operator (C++)](../debugger/context-operator-cpp.md).  
  
## <a name="observing-expressions-with-the-watch-window"></a>Osservazione delle espressioni con la finestra Espressioni di controllo  
 A questo punto è possibile provare a usare invece un'espressione. È possibile aggiungere qualsiasi espressione valida riconosciuta dal debugger.  
  
 Prendendo come esempio sempre il codice riportato nella sezione precedente, è possibile calcolare la media dei tre valori come segue:  
  
 ![Espressione di controllo](../debugger/media/watchexpression.png "WatchExpression")  
  
 In generale, le regole per la valutazione delle espressioni nella finestra **Espressioni di controllo** sono le stesse delle regole per la valutazione delle espressioni nel linguaggio di codifica. Se l'espressione contiene un errore di sintassi, è possibile aspettarsi lo stesso errore del compilatore che verrebbe visualizzato nell'editor del codice. Di seguito è riportato un esempio:  
  
 ![Guarda l'errore di espressione](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a> Aggiornamento dei valori delle espressioni di controllo che non sono aggiornati  
 In alcuni casi, si potrebbe essere visualizzata un'icona di aggiornamento (una freccia circolare) quando un'espressione viene valutata nella **Watch** finestra.  Ad esempio, se hai disattivata la valutazione delle proprietà (**strumenti > Opzioni > Debug > Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**), e di avere il codice seguente:  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Se si imposta un'espressione di controllo nella proprietà `Count` dell'elenco, verrà visualizzato un output simile al seguente:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 La figura precedente mostra un errore o un valore che non è aggiornato. In genere, è possibile aggiornare il valore facendo clic sull'icona, ma in alcuni casi potrebbe essere preferibile non aggiornarlo. È necessario sapere prima di tutto perché il valore non è stato valutato.  
  
 Se si punta all'icona, una descrizione comando fornisce informazioni sul motivo per cui l'espressione non è stata valutata.  Se vengono visualizzate le frecce che girano in cerchio, l'espressione non è stata valutata per uno dei seguenti motivi:  
  
-   Si è verificato un errore durante la valutazione dell'espressione. Ad esempio, è possibile che si sia verificato un timeout o che una variabile fosse esterna all'ambito.  
  
-   L'espressione contiene una chiamata di funzione, che potrebbe attivare un effetto collaterale dell'applicazione (vedere [effetti collaterali ed espressioni](#bkmk_sideEffects)).  
  
-   La valutazione automatica delle proprietà e chiamate di funzioni implicite da parte del debugger è disattivata (**strumenti > Opzioni > Debug > Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**), e quindi l'espressione non può essere viene valutata automaticamente.  
  
 Per aggiornare il valore, fare clic sull'icona di aggiornamento o premere la barra spaziatrice. Il debugger tenta di rivalutare l'espressione. Se l'icona di aggiornamento è stata visualizzata perché la valutazione automatica delle proprietà e altre chiamate di funzione implicite è disattivata, l'espressione può essere valutata.  
  
 Se viene visualizzata un'icona rappresentata da un cerchio con due linee ondulate che assomigliano a dei fili, l'espressione non è stata valutata a causa di una potenziale dipendenza cross-thread. In altre parole, la valutazione del codice richiede l'esecuzione temporanea di altri thread nell'applicazione. Quando ci si trova in modalità di interruzione, in genere tutti i thread nell'applicazione vengono arrestati. L'esecuzione temporanea di altri thread può avere effetti imprevisti sullo stato del programma e può far sì che il debugger ignori alcuni eventi quali i punti di interruzione e le eccezioni generate in tali thread.  
  
##  <a name="bkmk_sideEffects"></a> Side Effects and Expressions  
 La valutazione di alcune espressioni può comportare la modifica del valore di una variabile o altri effetti sullo stato del programma. La valutazione della seguente espressione, ad esempio, comporta la modifica del valore di `var1`:  
  
```csharp
var1 = var2  
```  
  
 Questo codice può causare una [effetto collaterale](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Gli effetti collaterali possono rendere più difficile il debug modificando la modalità di funzionamento del programma.  
  
 È noto a effetti collaterali che un'espressione viene valutata una sola volta, quando della prima immissione. Le successive valutazioni vengono disabilitate. È possibile eseguire manualmente l'override di questo comportamento facendo clic sull'icona di aggiornamento visualizzata accanto al valore.  
  
 Un modo per evitare gli effetti collaterali consiste nel disattivare la valutazione automatica della funzione (**strumenti > Opzioni > Debug > Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**).  
  
 Quando la valutazione delle proprietà o delle chiamate di funzione implicite è disattivata, è possibile forzarla con il modificatore di formato **ac** (solo per C#). Vedere [Format Specifiers in C#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="bkmk_objectIds"></a> Uso degli ID oggetto nella finestra Espressioni di controllo (C# e Visual Basic)  

 Esistono situazioni quando si vuole osservare il comportamento di un oggetto specifico. Ad esempio, è possibile tenere traccia di un oggetto a cui fa riferimento una variabile locale dopo la variabile esce dall'ambito. In C# e Visual Basic è possibile creare ID oggetto per istanze specifiche dei tipi di riferimento e usarle nella finestra Espressioni di controllo e nelle condizioni del punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.  
  
> [!NOTE]
>  Gli ID oggetto creano riferimenti deboli e non impediscono all'oggetto di essere sottoposto a Garbage Collection. Sono validi solo per la sessione di debug corrente.  
  
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
    List<Person> _people = new List<Person>();  
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
  
1.  Impostare un punto di interruzione nel codice dopo la creazione dell'oggetto.  
  
2.  Avviare il debug e quando l'esecuzione si arresta nel punto di interruzione, trovare la variabile nella finestra **Variabili locali** , fare clic con il pulsante destro del mouse sulla variabile e scegliere **Crea ID oggetto**.  
  
3.  Dovrebbe essere un **$** insieme a un numero il **variabili locali** finestra, che rappresenta l'ID oggetto.  
  
4.  Aggiungere l'ID oggetto nella finestra Espressioni di controllo.  
  
5.  Impostare un punto di interruzione in cui si vuole osservare il comportamento dell'oggetto.  Nel codice precedente, che sarebbe nel `DoSomething()` (metodo).  
  
6.  Continuare il debug e quando l'esecuzione viene arrestata nel metodo `DoSomething()` , nella finestra **Espressioni di controllo** viene visualizzato l'oggetto `Person` .  
  
> [!NOTE]
>  Se si desidera visualizzare le proprietà dell'oggetto, ad esempio `Person.Name` nell'esempio precedente, è necessario aver abilitato la valutazione delle proprietà.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Uso di registri nella finestra Espressioni di controllo (solo C++)  
 Se si esegue il debug codice nativo, è possibile aggiungere i nomi di registro, nonché i nomi delle variabili usando  **$ \<registrare nome >** oppure  **@ \<registrare nome >**.  Per altre informazioni, vedere [Pseudovariables](../debugger/pseudovariables.md).  
  
## <a name="dynamic-view-and-the-watch-window"></a>Visualizzazione dinamica e la finestra Espressioni di controllo  
 Alcuni linguaggi di script (ad esempio, JavaScript o Python) usano dinamico oppure [Duck Typing digitando](https://en.wikipedia.org/wiki/Duck_typing), e i linguaggi .NET (nella versione 4.0 e versioni successive) supportano gli oggetti che sono difficili da osservare con le normali finestre di debug, poiché sono possono contenere proprietà runtime e i metodi che non possono essere visualizzati.  
  
 Quando la finestra Espressioni di controllo viene visualizzato un oggetto creato da un tipo che implementa il [IDynamicMetaObjectProvider Interface](/dotnet/api/system.dynamic.idynamicmetaobjectprovider?view=netframework-4.7), il debugger aggiunge una speciale **visualizzazione dinamica** nodo per il **Auto**  visualizzare. Questo nodo mostra i membri dinamici dell'oggetto dinamico, ma non consente la modifica dei valori dei membri.  
  
 Se si fa clic con il pulsante destro del mouse su un oggetto figlio di una **Visualizzazione dinamica** e si sceglie **Aggiungi espressione di controllo**, il debugger inserisce una nuova variabile di controllo che esegue il cast di un oggetto in un oggetto dinamico. In altre parole, **object Name** diventa (**(dynamic)object).Name**.  
  
 La valutazione dei membri di una **Visualizzazione dinamica** può avere degli effetti collaterali. Per una spiegazione degli effetti collaterali, vedere [Side Effects and Expressions](#bkmk_sideEffects). Per C# il debugger non rivaluta automaticamente i valori mostrati nella **Visualizzazione dinamica** quando si passa a una nuova riga di codice. Per Visual Basic le espressioni aggiunte tramite la **Visualizzazione dinamica** vengono aggiornate automaticamente.  
  
 Per istruzioni su come aggiornare i valori della Visualizzazione dinamica, vedere [Aggiornamento dei valori delle espressioni di controllo che non sono aggiornati](#bkmk_refreshWatch).  
  
 Se si vuole visualizzare solo la **Visualizzazione dinamica** per un oggetto, è possibile usare l'identificatore di formato **dynamic** :  
  
-   C#: **ObjectName, dynamic**  
  
-   Visual Basic:: **$dynamic, ObjectName**  
  
 La **Visualizzazione dinamica** migliora anche l'esperienza di debug per gli oggetti COM. Quando il debugger rileva un oggetto COM di cui è stato eseguito il wrapping in **System.__ComObject**, aggiunge il nodo **Visualizzazione dinamica** per l'oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre del debugger](../debugger/debugger-windows.md)
