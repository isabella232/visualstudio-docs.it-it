---
title: Rinominare il Refactoring (c#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 40e13682b6ff22a0052adc7db9f9db9f18d36cc9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967353"
---
# <a name="rename-refactoring-c"></a>Refactoring di ridenominazione (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Rinominare** è una funzionalità di refactoring nell'ambiente di sviluppo integrato (IDE) di Visual Studio che fornisce un modo semplice per rinominare gli identificatori per i simboli del codice, ad esempio campi, le variabili locali, metodi, gli spazi dei nomi, proprietà e i tipi. **Rinominare** può essere utilizzato per modificare i nomi nei commenti e nelle stringhe e modificare le dichiarazioni e le chiamate di un identificatore.  
  
> [!NOTE]
>  Quando si utilizza controllo del codice sorgente per Visual Studio, ottenere la versione più recente delle origini prima di provare a eseguire il refactoring di ridenominazione.  
  
 Refactoring di ridenominazione è disponibile tramite le funzionalità di Visual Studio seguenti:  
  
|Funzionalità|Comportamento di Refactoring nell'IDE|  
|-------------|----------------------------------------|  
|Editor di codice|Nell'Editor di codice, il refactoring di ridenominazione è disponibile quando si posiziona il cursore su determinati tipi di simboli del codice. Quando il cursore si trova in questa posizione, è possibile richiamare il **rinominare** comando digitando il tasto di scelta rapida (CTRL + R, CTRL + R) o selezionando la **rinominare** da uno smart tag, menu di scelta rapida o le  **Effettuare il refactoring** menu.|  
|Visualizzazione classi|Quando si seleziona un identificatore in visualizzazione classi, il refactoring di ridenominazione è disponibile dal menu di scelta rapida e **refactoring** menu.|  
|Visualizzatore oggetti|Quando si seleziona un identificatore nel Visualizzatore oggetti, il refactoring di ridenominazione è disponibile solo il **refactoring** menu.|  
|Griglia delle proprietà della finestra di progettazione Windows Form|Nel **griglia delle proprietà** della finestra di progettazione Windows Form, la modifica del nome di un controllo avvierà un'operazione di ridenominazione per tale controllo. Il **Rinomina** non verrà visualizzata la finestra di dialogo.|  
|Esplora soluzioni|Nelle **Esplora soluzioni**, un **rinominare** comando è disponibile nel menu di scelta rapida. Se il file di origine selezionato contiene una classe il cui nome è lo stesso nome del file, è possibile usare questo comando Rinomina il file di origine e di eseguire il refactoring di ridenominazione simultaneamente.<br /><br /> Ad esempio, se si crea un'applicazione basata su Windows predefinito e quindi rinominare Form1.cs TestForm.cs, il nome di file di origine Form1.cs cambierà da TestForm.cs e la classe Form1 e tutti i riferimenti a che classe verrà rinominata in TestForm. **Nota:**  Il **annullare** comandi (CTRL + Z) verranno solo annullare il refactoring di ridenominazione nel codice e verrà non tornare il nome del file con il nome originale. <br /><br /> Se il file di origine selezionato non contiene una classe il cui nome corrisponde al nome del file, il **rinominare** comando **Esplora soluzioni** verranno rinominati solo il file di origine e non eseguirà la ridenominazione il refactoring.|  
  
## <a name="rename-operations"></a>Operazioni di ridenominazione  
 Quando si esegue **Rinomina**, il motore di refactoring consente di eseguire un'operazione di ridenominazione specifica per ogni simbolo del codice, come descritto nella tabella seguente.  
  
|Simbolo del codice|Operazione di ridenominazione|  
|-----------------|----------------------|  
|Campo|Modifica la dichiarazione e gli utilizzi del campo per il nuovo nome.|  
|variabile locale|Modifica la dichiarazione e gli utilizzi della variabile per il nuovo nome.|  
|Metodo|Modifica il nome del metodo e tutti i riferimenti a tale metodo per il nuovo nome. **Nota:**  Quando si rinomina un metodo di estensione, l'operazione di ridenominazione verrà propagata a tutte le istanze del metodo che rientrano nell'ambito, indipendentemente dal fatto se il metodo di estensione viene usato come metodo statico o un metodo di istanza. Per altre informazioni, vedere [Metodi di estensione](http://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|  
|Spazio dei nomi|Modifica il nome dello spazio dei nomi per il nuovo nome nella dichiarazione, tutte le `using` istruzioni e i nomi completi. **Nota:**  Quando si rinomina uno spazio dei nomi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aggiorna anche il **Default Namespace** proprietà il **applicazione** pagina del **Progettazione progetti**. Questa proprietà non può essere reimpostata selezionando **Undo** dalle **modificare** menu. Per reimpostare il **Namespace predefinito** valore della proprietà, è necessario modificare la proprietà nel **creazione progetti**. Per altre informazioni, vedere [pagina dell'applicazione](../ide/reference/application-page-project-designer-csharp.md).|  
|Proprietà|Modifica la dichiarazione e gli utilizzi della proprietà per il nuovo nome.|  
|Tipo|Modifica tutte le dichiarazioni e tutti gli utilizzi del tipo per il nuovo nome, inclusi costruttori e distruttori. Per i tipi parziali, l'operazione di ridenominazione verrà propagate a tutte le parti.|  
  
#### <a name="to-rename-an-identifier"></a>Per rinominare un identificatore  
  
1.  Creare un'applicazione console denominata `RenameIdentifier` quindi sostituire `Program` con il codice di esempio seguente.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Posizionare il cursore sulla `MethodB`, nella dichiarazione del metodo o la chiamata al metodo.  
  
3.  Dal **refactoring** dal menu **rinominare**. Il **Rinomina** verrà visualizzata la finestra di dialogo.  
  
     È anche possibile fare doppio clic sul cursore, scegliere **refactoring** nel menu di scelta rapida, quindi **rinominare** per visualizzare il **rinominare** nella finestra di dialogo.  
  
4.  Nel **nuovo nome** digitare `MethodC`.  
  
5.  Selezionare il **ricerca nei commenti** casella di controllo.  
  
6.  Fare clic su **OK**.  
  
7.  Nel **Anteprima modifiche** finestra di dialogo, fare clic su **applica**.  
  
#### <a name="to-rename-an-identifier-using-smart-tags"></a>Per rinominare un identificatore usando gli smart tag  
  
1.  Creare un'applicazione console denominata `RenameIdentifier` quindi sostituire `Program` con il codice di esempio seguente.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Nella dichiarazione per `MethodB`digitare o backspace l'identificatore del metodo. Verrà visualizzato un messaggio di smart tag di sotto di questo identificatore.  
  
    > [!NOTE]
    >  È possibile richiamare solo il refactoring di ridenominazione usando gli smart tag in una dichiarazione di un identificatore.  
  
3.  Digitare il tasto di scelta rapida MAIUSC + ALT + F10 e quindi premere la freccia giù per visualizzare il menu smart tag.  
  
     -oppure-  
  
     Spostare il puntatore del mouse su prompt dei comandi di smart tag per visualizzare lo smart tag. Quindi spostare il puntatore del mouse sullo smart tag e fare clic sulla freccia verso il basso per visualizzare il menu smart tag.  
  
4.  Selezionare il **rinominare '\<identifer1 >' a '\<identifier2 >'** voce di menu per richiamare il refactoring di ridenominazione senza un'anteprima delle modifiche al codice. Tutti i riferimenti a  **\<identifer1 >** verrà automaticamente aggiornato a  **\<identifier2 >**.  
  
     -oppure-  
  
     Selezionare il **Rinomina con anteprima** voce di menu per richiamare il refactoring di ridenominazione con una versione di anteprima delle modifiche al codice. Il **Anteprima modifiche** verrà visualizzata la finestra di dialogo.  
  
## <a name="remarks"></a>Note  
  
## <a name="renaming-implemented-or-overridden-members"></a>Ridenominazione di membri implementati o sottoposti a override  
 Quando si **rinominare** un membro che implementa o esegue l'override o che è implementata/sottoposto a override dai membri in altri tipi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualizza una finestra di dialogo che afferma che l'operazione di ridenominazione causerà gli aggiornamenti a catena. Se si sceglie **continuazione**, il refactoring in modo ricorsivo motore rileva e consente di rinominare tutti i membri di base e i tipi derivati che hanno implementa/sostituzioni relazioni con il membro che viene rinominata.  
  
 Esempio di codice seguente contiene i membri con relazioni implementa o esegue l'override.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 Nell'esempio precedente, la ridenominazione `C.Method()` consente inoltre di rinominare `Ibase.Method()` poiché `C.Method()` implementa `Ibase.Method()`. Successivamente, il motore di refactoring in modo ricorsivo vede che `Ibase.Method()` implementata da `Derived.Method()` e Rinomina `Derived.Method()`. Il motore di refactoring non comporta la ridenominazione `Base.Method()`, in quanto `Derived.Method()` non esegue l'override `Base.Method()`. Il motore di refactoring si interrompe se non si dispone **rinominare gli overload** Check-nelle **rinominare** nella finestra di dialogo.  
  
 Se **rinominare gli overload** è selezionata, il motore di refactoring di ridenominazione `Derived.Method(int i)` perché esegue l'overload `Derived.Method()`, `Base.Method(int i)` perché vengono sostituiti da `Derived.Method(int i)`, e `Base.Method()` perché è un overload di `Base.Method(int i)`.  
  
> [!NOTE]
>  Quando si rinomina un membro che è stato definito in un assembly di riferimento, una finestra di dialogo viene illustrato che l'operazione di ridenominazione causerà errori di compilazione.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Ridenominazione di proprietà di tipi anonimi  
 Quando si rinomina una proprietà in tipi anonimi, l'operazione di ridenominazione verrà propagato alle proprietà di altri tipi anonimi che hanno le stesse proprietà. Gli esempi seguenti illustrano questo comportamento.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 Nel codice precedente, la ridenominazione `ID` cambierà `ID` in entrambe le istruzioni perché hanno lo stesso tipo anonimo sottostante.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 Nel codice precedente, la ridenominazione `ID` verranno rinominati solo un'istanza di `ID` poiché `companyIDs` e `orderIDs` non ha le stesse proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)   
 [Tipi anonimi](http://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)