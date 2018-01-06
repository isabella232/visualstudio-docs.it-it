---
redirect_url: /visualstudio/csharp-ide/refactoring/rename
title: Rinominare il Refactoring (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 42c5f99b3bf5ba95bc279cd5e117745ccc8e02c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="rename-refactoring-c"></a>Refactoring di ridenominazione (C#)
**Rinominare** è una funzionalità dell'ambiente di sviluppo integrato (IDE) di Visual Studio che fornisce un modo semplice per rinominare gli identificatori per i simboli del codice, ad esempio campi, le variabili locali, metodi, gli spazi dei nomi, proprietà e tipi di refactoring. **Rinominare** può essere utilizzato per modificare i nomi nei commenti e nelle stringhe e modificare le dichiarazioni e le chiamate di un identificatore.  
  
> [!NOTE]
>  Quando si utilizza controllo del codice sorgente per Visual Studio, ottenere la versione più recente delle origini prima di provare a eseguire il refactoring di ridenominazione.  
  
 Il refactoring di ridenominazione in è disponibile le seguenti funzionalità di Visual Studio:  
  
|Funzionalità|Comportamento di Refactoring nell'IDE|  
|-------------|----------------------------------------|  
|Editor di codice|Nell'Editor di codice, il refactoring di ridenominazione è disponibile quando si posiziona il cursore su determinati tipi di simboli del codice. Quando il cursore si trova in questa posizione, è possibile richiamare il **rinominare** comando digitando il tasto di scelta rapida (Ctrl + R, Ctrl + R) o selezionando la **rinominare** comando azioni rapide, menu di scelta rapida o **Refactoring** menu.|  
|Visualizzazione classi|Quando si seleziona un identificatore in visualizzazione classi, il refactoring di ridenominazione è disponibile dal menu di scelta rapida e **refactoring** menu.|  
|Visualizzatore oggetti|Quando si seleziona un identificatore in Visualizzatore oggetti, il refactoring di ridenominazione è disponibile solo dal **refactoring** menu.|  
|Griglia delle proprietà di progettazione Windows Form|Nel **griglia delle proprietà** della finestra di progettazione Windows Form, la modifica del nome di un controllo verrà avviata un'operazione di ridenominazione per tale controllo. Il **rinominare** non verrà visualizzata la finestra di dialogo.|  
|Esplora soluzioni|In **Esplora**, **rinominare** comando è disponibile nel menu di scelta rapida. Se il file di origine selezionato contiene una classe il cui nome è identico al nome di file, è possibile utilizzare questo comando Rinomina il file di origine e di eseguire il refactoring di ridenominazione simultaneamente.<br /><br /> Ad esempio, se si crea un'applicazione basata su Windows predefinita e si rinomina Form1. cs in TestForm.cs, il nome del file di origine Form1. cs verrà modificato in TestForm.cs e della classe Form1 e tutti i riferimenti a essa verranno rinominati in TestForm. **Nota:** il **Annulla** comando (CTRL + Z) solo per annullare il refactoring di ridenominazione nel codice e verrà non riportare il nome del file con il nome originale. <br /><br /> Se il file di origine selezionato non contiene una classe il cui nome è identico al nome di file, il **rinominare** comando **Esplora** consentirà solo di rinominare il file di origine e non verrà eseguito Rinomina il refactoring.|  
  
## <a name="rename-operations"></a>Operazioni di ridenominazione  
 Quando si esegue **rinominare**, il motore di refactoring effettua un'operazione di ridenominazione specifica per ogni simbolo di codice, come descritto nella tabella seguente.  
  
|Simbolo del codice|Operazione di ridenominazione|  
|-----------------|----------------------|  
|Campo|Modifica la dichiarazione e l'utilizzo del campo per il nuovo nome.|  
|variabile locale|Modifica la dichiarazione e utilizzo della variabile per il nuovo nome.|  
|Metodo|Modifica il nome del metodo e tutti i riferimenti a tale metodo per il nuovo nome. **Nota:** quando si rinomina un metodo di estensione, l'operazione di ridenominazione verrà propagato a tutte le istanze del metodo che rientrano nell'ambito, indipendentemente dal fatto se il metodo di estensione è usato come un metodo statico o un metodo di istanza. Per altre informazioni, vedere [Metodi di estensione](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).|  
|Spazio dei nomi|Modifica il nome dello spazio dei nomi per il nuovo nome nella dichiarazione, tutte `using` istruzioni e i nomi completi. **Nota:** quando si rinomina uno spazio dei nomi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aggiorna anche il **Default Namespace** proprietà il **applicazione** pagina del **progettazione**. Questa proprietà non può essere reimpostata selezionando **Annulla** dal **modifica** menu. Per reimpostare il **Default Namespace** valore della proprietà, è necessario modificare la proprietà nel **progettazione**. Per ulteriori informazioni, vedere [pagina applicazione](../ide/reference/application-page-project-designer-csharp.md).|  
|Proprietà|Modifica la dichiarazione e utilizzo della proprietà per il nuovo nome.|  
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
  
2.  Posizionare il cursore su `MethodB`, nella dichiarazione di metodo o la chiamata al metodo.  
  
3.  Dal **refactoring** dal menu **rinominare**. Il **rinominare** viene visualizzata la finestra di dialogo.  
  
     È anche possibile fare doppio clic sul cursore, scegliere **refactoring** dal menu di scelta rapida, quindi **rinominare** per visualizzare il **rinominare** la finestra di dialogo.  
  
4.  Nel **nuovo nome** digitare `MethodC`.  
  
5.  Selezionare il **ricerca nei commenti** casella di controllo.  
  
6.  Fare clic su **OK**.  
  
7.  Nel **Anteprima modifiche** la finestra di dialogo, fare clic su **applica**.  
  
#### <a name="to-rename-an-identifier-using-quick-actions"></a>Per rinominare un identificatore con azioni rapide  
  
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
  
2.  Nella dichiarazione `MethodB`digitare o backspace sull'identificatore del metodo. Nel margine, verrà visualizzata una lampadina azioni rapide.  
  
    > [!NOTE]
    >  È possibile richiamare solo il refactoring di ridenominazione con azioni rapide nella dichiarazione di un identificatore.  
  
3.  Digitare il tasto di scelta rapida **Maiusc + Alt + F10** per visualizzare il menu di azioni rapide.  
  
     oppure  
  
     Fare clic sul triangolo nero accanto la lampadina per visualizzare il menu di azioni rapide.  
  
4.  Selezionare il **rinominare '\<identifer1 >' a '\<identificatore2 >'** voce di menu per richiamare il refactoring di ridenominazione. Tutti i riferimenti a  **\<identifer1 >** verranno automaticamente aggiornati al  **\<identificatore2 >**.  
  
## <a name="remarks"></a>Note  
  
## <a name="renaming-implemented-or-overridden-members"></a>Ridenominazione di membri implementati o sottoposti a override  
 Quando si **rinominare** un membro che implementa esegue l'override o implementati sottoposto a override dai membri in altri tipi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualizza una finestra di dialogo indicante l'operazione di ridenominazione causerà gli aggiornamenti a catena. Se si fa clic **continua**, in modo ricorsivo il refactoring motore rileva e rinomina tutti i membri di base e tipi derivati che hanno implementa/sostituzioni relazioni con il membro viene rinominato.  
  
 Esempio di codice seguente contiene membri con relazioni implementa esegue l'override.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 Nell'esempio precedente, la ridenominazione `C.Method()` anche Rinomina `Ibase.Method()` perché `C.Method()` implementa `Ibase.Method()`. Quindi, in modo ricorsivo il motore di refactoring rileva che `Ibase.Method()` viene implementata da `Derived.Method()` e Rinomina `Derived.Method()`. Il motore di refactoring non comporta la ridenominazione `Base.Method()`perché `Derived.Method()` non esegue l'override `Base.Method()`. Il motore di refactoring si arresta a meno che non si dispone **Rinomina overload** archiviato il **rinominare** la finestra di dialogo.  
  
 Se **Rinomina overload** è selezionata, il motore di refactoring rinomina `Derived.Method(int i)` perché esegue l'overload `Derived.Method()`, `Base.Method(int i)` perché è sottoposto a override da `Derived.Method(int i)`, e `Base.Method()` perché è un overload di `Base.Method(int i)`.  
  
> [!NOTE]
>  Quando si rinomina un membro che è stato definito in un assembly di riferimento, una finestra di dialogo viene illustrato che l'operazione di ridenominazione causerà errori di compilazione.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Ridenominazione di proprietà di tipi anonimi  
 Quando si rinomina una proprietà in tipi anonimi, l'operazione di ridenominazione verrà propagata alle proprietà in altri tipi anonimi che hanno le stesse proprietà. Gli esempi seguenti illustrano questo comportamento.  
  
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
  
 Nel codice precedente, la ridenominazione `ID` verranno rinominati solo un'istanza di `ID` perché `companyIDs` e `orderIDs` non ha le stesse proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](refactoring-csharp.md)   
 [Tipi anonimi](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)