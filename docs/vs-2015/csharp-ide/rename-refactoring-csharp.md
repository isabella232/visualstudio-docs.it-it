---
title: Refactoring di ridenominazione (C#) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667484"
---
# <a name="rename-refactoring-c"></a>Refactoring di ridenominazione (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Rinominare** è una funzionalità di refactoring di Visual Studio Integrated Development Environment (IDE) che offre un modo semplice per rinominare gli identificatori per i simboli del codice, ad esempio campi, variabili locali, metodi, spazi dei nomi, proprietà e tipi. **Rinominare** può essere usato per modificare i nomi nei commenti e nelle stringhe e per modificare le dichiarazioni e le chiamate di un identificatore.

> [!NOTE]
> Quando si usa il controllo del codice sorgente per Visual Studio, ottenere la versione più recente delle origini prima di provare a eseguire il refactoring di ridenominazione.

 Il refactoring di ridenominazione è disponibile dalle seguenti funzionalità di Visual Studio:

|Feature|Comportamento del refactoring nell'IDE|
|-------------|----------------------------------------|
|Editor di codice|Nell'editor di codice, il refactoring di ridenominazione è disponibile quando si posiziona il cursore su determinati tipi di simboli di codice. Quando il cursore si trova in questa posizione, è possibile richiamare il comando **Rinomina** digitando il tasto di scelta rapida (Ctrl + r, CTRL + r) oppure selezionando il comando **Rinomina** da uno smart tag, dal menu di scelta rapida o dal menu **refactoring** .|
|Visualizzazione classi|Quando si seleziona un identificatore in Visualizzazione classi, il refactoring di ridenominazione è disponibile dal menu di scelta rapida e dal menu **refactoring** .|
|Visualizzatore oggetti|Quando si seleziona un identificatore in Visualizzatore oggetti, il refactoring di ridenominazione è disponibile solo dal menu **refactoring** .|
|Griglia delle proprietà della Progettazione Windows Form|Nella **griglia delle proprietà** della progettazione Windows Form, la modifica del nome di un controllo avvierà un'operazione di ridenominazione per quel controllo. La finestra di dialogo **Rinomina** non verrà visualizzata.|
|Esplora soluzioni|In **Esplora soluzioni**, un comando **Rinomina** è disponibile nel menu di scelta rapida. Se il file di origine selezionato contiene una classe il cui nome di classe corrisponde al nome del file, è possibile usare questo comando per rinominare contemporaneamente il file di origine ed eseguire il refactoring di ridenominazione.<br /><br /> Se, ad esempio, si crea un'applicazione predefinita basata su Windows e quindi si rinomina Form1.cs in TestForm.cs, il nome del file di origine Form1.cs cambierà in TestForm.cs e la classe Form1 e tutti i riferimenti a tale classe verranno rinominati in TestForm. **Nota:**  Il comando **Annulla** (CTRL + Z) Annulla solo il refactoring di ridenominazione nel codice e non modifica il nome del file con il nome originale. <br /><br /> Se il file di origine selezionato non contiene una classe il cui nome corrisponde al nome del file, il comando **Rename** in **Esplora soluzioni** rinominerà solo il file di origine e non eseguirà il refactoring di ridenominazione.|

## <a name="rename-operations"></a>Rinominare le operazioni
 Quando si esegue **Rename**, il motore di refactoring esegue un'operazione di ridenominazione specifica per ogni simbolo di codice, come descritto nella tabella seguente.

|Simbolo del codice|Operazione di ridenominazione|
|-----------------|----------------------|
|Campo|Modifica la dichiarazione e gli utilizzi del campo con il nuovo nome.|
|Variabile locale|Modifica la dichiarazione e gli utilizzi della variabile nel nuovo nome.|
|Metodo|Modifica il nome del metodo e tutti i riferimenti a tale metodo con il nuovo nome. **Nota:**  Quando si rinomina un metodo di estensione, l'operazione di ridenominazione viene propagata a tutte le istanze del metodo che si trovano nell'ambito, indipendentemente dal fatto che il metodo di estensione venga utilizzato come metodo statico o come metodo di istanza. Per altre informazioni, vedere [Metodi di estensione](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|
|Spazio dei nomi|Modifica il nome dello spazio dei nomi con il nuovo nome nella dichiarazione, in tutte le `using` istruzioni e nei nomi completi. **Nota:**  Quando si rinomina uno spazio dei nomi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Aggiorna anche la proprietà **spazio dei nomi predefinito** nella pagina **applicazione** di **Progettazione progetti**. Non è possibile reimpostare questa proprietà selezionando **Annulla** dal menu **modifica** . Per reimpostare il valore predefinito della proprietà **dello spazio dei nomi** , è necessario modificare la proprietà in **Progettazione progetti**. Per ulteriori informazioni, vedere la [pagina dell'applicazione](../ide/reference/application-page-project-designer-csharp.md).|
|Proprietà|Modifica la dichiarazione e gli utilizzi della proprietà con il nuovo nome.|
|Type|Modifica tutte le dichiarazioni e tutti gli utilizzi del tipo nel nuovo nome, inclusi i costruttori e i distruttori. Per i tipi parziali, l'operazione di ridenominazione viene propagata a tutte le parti.|

#### <a name="to-rename-an-identifier"></a>Per rinominare un identificatore

1. Creare un'applicazione console denominata `RenameIdentifier` quindi sostituire `Program` con il codice di esempio seguente.

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

2. Posizionare il cursore su `MethodB` , nella dichiarazione del metodo o nella chiamata al metodo.

3. Dal menu **refactoring** selezionare **Rinomina**. Verrà visualizzata la finestra di dialogo **Rinomina** .

     È inoltre possibile fare clic con il pulsante destro del mouse sul cursore, scegliere **refactoring** dal menu di scelta rapida, quindi fare clic su **Rinomina** per visualizzare la finestra di dialogo **Rinomina** .

4. Nel campo **nuovo nome** Digitare `MethodC` .

5. Selezionare la casella **di controllo Cerca nei commenti** .

6. Fare clic su **OK**.

7. Nella finestra di dialogo **Anteprima modifiche** fare clic su **applica**.

#### <a name="to-rename-an-identifier-using-smart-tags"></a>Per rinominare un identificatore usando gli smart tag

1. Creare un'applicazione console denominata `RenameIdentifier` quindi sostituire `Program` con il codice di esempio seguente.

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

2. Nella dichiarazione per `MethodB` , digitare o Backspace sull'identificatore del metodo. Al di sotto di questo identificatore verrà visualizzato un prompt smart tag.

    > [!NOTE]
    > È possibile richiamare solo il refactoring di ridenominazione usando gli smart tag in corrispondenza della dichiarazione di un identificatore.

3. Digitare il tasto di scelta rapida MAIUSC + ALT + F10, quindi premere la freccia giù per visualizzare il menu smart tag.

     -oppure-

     Spostare il puntatore del mouse sul prompt smart tag per visualizzare lo smart tag. Spostare quindi il puntatore del mouse sullo smart tag e fare clic sulla freccia verso il basso per visualizzare il menu smart tag.

4. Selezionare la voce di menu **Rinomina ' \<identifer1> ' in ' \<identifier2> '** per richiamare il refactoring di ridenominazione senza visualizzare un'anteprima delle modifiche apportate al codice. Tutti i riferimenti a **\<identifer1>** verranno aggiornati automaticamente a **\<identifier2>** .

     -oppure-

     Selezionare la voce di menu **Rinomina con anteprima** per richiamare il refactoring di ridenominazione con un'anteprima delle modifiche apportate al codice. Verrà visualizzata la finestra di dialogo **Anteprima modifiche** .

## <a name="remarks"></a>Osservazioni

## <a name="renaming-implemented-or-overridden-members"></a>Ridenominazione di membri implementati o sottoposti a override
 Quando si **Rinomina** un membro che implementa/sostituisce o viene implementato o sottoposto a override da membri di altri tipi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualizza una finestra di dialogo che indica che l'operazione di ridenominazione provocherà aggiornamenti a catena. Se si fa clic su **continua**, il motore di refactoring rileva e Rinomina in modo ricorsivo tutti i membri nei tipi di base e derivati che dispongono di relazioni Implements/override con il membro rinominato.

 L'esempio di codice seguente contiene membri con relazioni Implements/Overrides.

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 Nell'esempio precedente, la ridenominazione anche viene rinominata `C.Method()` `Ibase.Method()` perché `C.Method()` implementa `Ibase.Method()` . Successivamente, il motore di refactoring rileva in modo ricorsivo che `Ibase.Method()` viene implementato da `Derived.Method()` e rinominato `Derived.Method()` . Il motore di refactoring non viene rinominato `Base.Method()` , perché non `Derived.Method()` esegue l'override di `Base.Method()` . Il motore di refactoring si interrompe qui, a meno che non siano stati **rinominati gli overload** selezionati nella finestra di dialogo **Rinomina** .

 Se si seleziona **Rinomina Overloads** , il motore di refactoring viene rinominato `Derived.Method(int i)` perché `Derived.Method()` esegue l' `Base.Method(int i)` Overload, perché viene sottoposto a override da `Derived.Method(int i)` e perché è `Base.Method()` un overload di `Base.Method(int i)` .

> [!NOTE]
> Quando si rinomina un membro definito in un assembly a cui viene fatto riferimento, viene visualizzata una finestra di dialogo che indica che la ridenominazione provocherà errori di compilazione.

## <a name="renaming-properties-of-anonymous-types"></a>Ridenominazione di proprietà di tipi anonimi
 Quando si rinomina una proprietà in tipi anonimi, l'operazione di ridenominazione viene propagata alle proprietà in altri tipi anonimi con le stesse proprietà. Negli esempi seguenti viene illustrato questo comportamento.

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 Nel codice precedente, la ridenominazione cambierà `ID` `ID` in entrambe le istruzioni perché hanno lo stesso tipo anonimo sottostante.

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 Nel codice precedente, la ridenominazione `ID` rinominerà solo un'istanza di `ID` perché `companyIDs` e `orderIDs` non hanno le stesse proprietà.

## <a name="see-also"></a>Vedere anche
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md) [tipi anonimi](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)