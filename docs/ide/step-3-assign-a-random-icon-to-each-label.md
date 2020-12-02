---
title: "Passaggio 3: Assegnare un'icona casuale a ogni etichetta"
description: Informazioni su come assegnare un'icona casuale a ogni etichetta in modo che le icone non vengano visualizzate nelle stesse celle di ogni gioco.
ms.custom: SEO-VS-2020
ms.date: 03/21/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f3330daeed243f96c44825a4be5516c573bb005
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480629"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Passaggio 3: Assegnare un'icona casuale a ogni etichetta

Non sarebbe particolarmente impegnativo visualizzare le icone sempre nelle stesse celle a ogni gioco. Per evitare questa situazione, assegnare le icone in modo casuale ai controlli Label nel modulo usando un metodo `AssignIconsToSquares()`.

## <a name="to-assign-a-random-icon-to-each-label"></a>Per assegnare un'icona casuale a ogni etichetta

1. Prima di aggiungere il codice seguente, considerare come funziona il metodo. È presente una nuova parola chiave: `foreach` in C# e `For Each` in Visual Basic. Una delle righe è appositamente impostata come commento; la spiegazione è riportata al fondo della procedura.

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > Usare il controllo linguaggio di programmazione nella parte superiore destra della pagina per visualizzare il frammento di codice C# o il frammento di codice Visual Basic.<br><br>![Controllo del linguaggio di programmazione per Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

2. Aggiungere il metodo `AssignIconsToSquares()` come illustrato nel passaggio precedente. È possibile inserirlo immediatamente dopo il codice aggiunto in [Passaggio 2: Aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Come indicato in precedenza, nel metodo è presente qualcosa di nuovo `AssignIconsToSquares()` : un `foreach` ciclo in C# e `For Each` in Visual Basic. È possibile utilizzare un ciclo `For Each` ogni qualvolta si desidera eseguire la stessa azione ripetutamente. In questo caso, si vuole eseguire le stesse istruzioni per ogni etichetta in <xref:System.Windows.Forms.TableLayoutPanel>, come spiegato nel codice seguente. Nella prima riga viene creata una variabile denominata `control` in cui viene archiviato ogni controllo, uno alla volta, mentre sul controllo vengono eseguite le istruzioni incluse nel ciclo.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > I nomi "iconLabel" e "control" vengono utilizzati in quanto nomi descrittivi. È possibile sostituirli con altri nomi senza che il codice ne risulti pregiudicato, a condizione che si modifichi il nome in ogni istruzione all'interno del ciclo.

     Il metodo `AssignIconsToSquares()` scorre ogni controllo etichetta in TableLayoutPanel ed esegue le stesse istruzioni per ognuno di essi. Tali istruzioni prendono un'icona casuale dall'elenco aggiunto in [Passaggio 2: Aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). Come promemoria, ognuna di queste icone è una lettera del tipo di carattere Webdings, motivo per cui viene espressa come testo in questo metodo. Sono state incluse due di ciascuna icona nell'elenco, in modo che sia presente una coppia di icone assegnata ai controlli etichetta casuali.

     Analizzare attentamente il codice eseguito all'interno del ciclo `foreach` o `For Each`. Questo codice viene riprodotto di seguito.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     La prima riga converte la variabile **control** in un'etichetta denominata **iconLabel**. La riga successiva è un'istruzione `if` che verifica se la conversione è stata eseguita correttamente. In caso affermativo, vengono eseguite le istruzioni contenute nell'istruzione `if`. Come è possibile ricordare dalle esercitazioni precedenti, l' `if` istruzione viene usata per valutare qualsiasi condizione specificata. La prima riga nell' `if` istruzione crea una variabile denominata **RandomNumber** che contiene un numero casuale che corrisponde a uno degli elementi nell'elenco icone. A questo scopo, viene utilizzato il metodo <xref:System.Random.Next> dell'oggetto <xref:System.Random> creato precedentemente. Il metodo `Next` restituisce il numero casuale. Questa riga usa anche la proprietà <xref:System.Collections.Generic.List%601.Count> dell'elenco **icons** per determinare l'intervallo da cui scegliere il numero casuale. Nella riga successiva viene assegnato uno degli elementi dell'elenco di icone alla proprietà <xref:System.Windows.Forms.Label.Text> dell'etichetta. La riga impostata come commento viene descritta più avanti in questo argomento. Infine, nell'ultima riga dell'istruzione `if` l'icona aggiunta al form viene rimossa dall'elenco.

     Tenere presente che, in caso di dubbi sulle operazioni eseguite in alcune parti del codice, è possibile posizionare il puntatore del mouse su un elemento di codice ed esaminare la descrizione comando visualizzata. È inoltre possibile scorrere ogni riga di codice mentre il programma è in esecuzione utilizzando il debugger di Visual Studio. Per altre informazioni, vedere [How Do I: Step with The Debugger in Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) (Procedura: Uso del debugger in Visual Studio) o [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md).

3. Per riempire la tavola da gioco con icone, è necessario chiamare il metodo di `AssignIconsToSquares()` non appena il programma viene avviato. Se si usa C#, aggiungere un'istruzione immediatamente dopo la chiamata al `InitializeComponent()` metodo nel _Costruttore_ **Form1** , in modo che il form chiami il nuovo metodo per impostarlo prima che venga visualizzato. I costruttori vengono chiamati quando si crea un nuovo oggetto, ad esempio una classe o uno struct. Per altre informazioni, vedere [Costruttori (Guida per programmatori C#)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) o [Utilizzo di costruttori e distruttori](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) in Visual Basic.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Per Visual Basic, aggiungere la chiamata del metodo `AssignIconsToSquares()` al metodo `Form1_Load` in modo che il codice risulti analogo al seguente:

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Salvare ed eseguire il programma. Dovrebbe visualizzare un form con icone casuali assegnate a ogni etichetta. 

5. Chiudere il programma, quindi eseguirlo nuovamente. Icone diverse sono ora assegnate a ogni etichetta, come mostrato nell'immagine seguente. 

     ![Gioco di abbinamenti con icone casuali](../ide/media/express_tut4step3.png)<br/>
*Gioco di abbinamenti con icone casuali*

     Le icone sono ora visibili, poiché non sono state nascoste. Per nasconderle, è possibile impostare la proprietà **ForeColor** di ciascuna etichetta sullo stesso colore della proprietà **BackColor**.

6. Per nascondere le icone, arrestare il programma e rimuovere i contrassegni di commento per la riga di codice commentata nel ciclo `For Each`.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Nella barra dei menu fare clic sul pulsante **Salva tutto** per salvare il programma, quindi eseguirlo. Le icone sembrano essere scomparse, è presente soltanto uno sfondo blu. Le icone tuttavia sono assegnate casualmente e sono ancora al loro posto. Essendo dello stesso colore dello sfondo, le icone non vengono visualizzate dal giocatore. Dopo tutto, non sarebbe un gioco particolarmente impegnativo se il giocatore potesse visualizzare subito tutte le icone!

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 4: aggiungere un gestore eventi click a ogni etichetta](../ide/step-4-add-a-click-event-handler-to-each-label.md)**.

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 2: Aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
