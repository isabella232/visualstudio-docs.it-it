---
title: "Passaggio 3: Assegnare un'icona casuale a ogni etichetta | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4382a450051b7626a5eb5e29bf2ce4e78f6eceda
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671835"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Passaggio 3: assegnare un'icona casuale a ogni etichetta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Non sarebbe particolarmente impegnativo visualizzare le icone sempre nelle stesse celle a ogni gioco. Per evitare questa situazione, assegnare casualmente le icone a controlli etichetta nel form tramite un metodo `AssignIconsToSquares()`.

### <a name="to-assign-a-random-icon-to-each-label"></a>Per assegnare un'icona casuale a ogni etichetta

1. Prima di aggiungere il codice seguente, considerare come funziona il metodo. È presente una nuova parola chiave: `foreach` in Visual C# e `For Each` in Visual Basic. Una delle righe è appositamente impostata come commento; la spiegazione è riportata al fondo della procedura.

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]

2. Aggiungere il metodo `AssignIconsToSquares()` come illustrato nel passaggio precedente. È possibile inserirlo immediatamente dopo il codice aggiunto durante il [Passaggio 2: aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Come enunciato in precedenza, nel metodo `AssignIconsToSquares()` è presente una novità: un ciclo `foreach` in Visual C# e `For Each` in Visual Basic. È possibile utilizzare un ciclo `For Each` ogni qualvolta si desidera eseguire la stessa azione ripetutamente. In questo caso, eseguire le stesse istruzioni per ogni etichetta in TableLayoutPanel, come spiegato tramite il codice seguente. Nella prima riga viene creata una variabile denominata `control` in cui viene archiviato ogni controllo, uno alla volta, mentre sul controllo vengono eseguite le istruzioni incluse nel ciclo.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]

    > [!NOTE]
    > I nomi "iconLabel" e "control" vengono utilizzati in quanto nomi descrittivi. È possibile sostituirli con altri nomi senza che il codice ne risulti pregiudicato, a condizione che si modifichi il nome in ogni istruzione all'interno del ciclo.

     Il metodo `AssignIconsToSquares()` scorre ogni controllo etichetta in TableLayoutPanel ed esegue le stesse istruzioni per ognuno di essi. Tali istruzioni prendono un'icona casuale dall'elenco aggiunto durante il [Passaggio 2: aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). Nell'elenco sono state incluse coppie di icone, in modo tale da poter assegnare una coppia di icone ai controlli etichetta casuali.

     Analizzare attentamente il codice eseguito all'interno del ciclo `foreach` o `For Each`. Questo codice viene riprodotto di seguito.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]

     Nella prima riga viene convertita la variabile `control` in un'etichetta denominata `iconLabel`. La riga successiva è un'istruzione `if` che verifica se la conversione è stata eseguita correttamente. In caso affermativo, vengono eseguite le istruzioni contenute nell'istruzione `if`. Come è possibile ricordare dalle esercitazioni precedenti, l'istruzione `if` viene utilizzata per valutare qualsiasi condizione specificata. La prima riga nell'istruzione `if` crea una variabile denominata `randomNumber` contenente un numero casuale che corrisponde a uno degli elementi nell'elenco di icone. A questo scopo, viene utilizzato il metodo `Next` dell'oggetto `Random` creato precedentemente. Il metodo `Next` restituisce il numero casuale. In questa riga viene inoltre utilizzata la proprietà `Count` dell'elenco `icons` per determinare l'intervallo da cui scegliere il numero casuale. Nella riga successiva viene assegnato uno degli elementi dell'elenco di icone alla proprietà `Text` dell'etichetta. La riga impostata come commento viene descritta più avanti in questo argomento. Infine, nell'ultima riga dell'istruzione `if` l'icona aggiunta al form viene rimossa dall'elenco.

     Tenere presente che, in caso di dubbi sulle operazioni eseguite in alcune parti del codice, è possibile posizionare il puntatore del mouse su un elemento di codice ed esaminare la descrizione comando visualizzata. È inoltre possibile scorrere ogni riga di codice mentre il programma è in esecuzione utilizzando il debugger di Visual Studio. Per altre informazioni, vedere [How Do I: Step with The Debugger in Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) (Procedura: Uso del debugger in Visual Studio) o [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md).

3. Per riempire la tavola da gioco con icone, è necessario chiamare il metodo di `AssignIconsToSquares()` non appena il programma viene avviato. Se si usa Visual C#, aggiungere un'istruzione immediatamente dopo la chiamata al metodo `InitializeComponent()` nel *costruttore*`Form1`, in modo che il form chiami il nuovo metodo e questo venga configurato prima di essere visualizzato. I costruttori vengono chiamati quando si crea un nuovo oggetto, ad esempio una classe o uno struct. Per altre informazioni, vedere [Costruttori (Guida per programmatori C#)](https://msdn.microsoft.com/library/ace5hbzh.aspx) o [Utilizzo di costruttori e distruttori](https://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) in Visual Basic.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]

     Per Visual Basic, aggiungere la chiamata del metodo `AssignIconsToSquares()` al metodo `Form1_Load` in modo che il codice risulti analogo al seguente:

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Salvare ed eseguire il programma. Dovrebbe visualizzare un form con icone casuali assegnate a ogni etichetta.

5. Chiudere il programma, quindi eseguirlo nuovamente. Icone diverse sono ora assegnate a ogni etichetta, come mostrato nell'immagine seguente.

     ![Gioco di abbinamenti con icone casuali](../ide/media/express-tut4step3.png "Express_Tut4Step3") Gioco di abbinamenti con icone casuali

     Le icone sono ora visibili, poiché non sono state nascoste. Per nasconderle, è possibile impostare la proprietà `Forecolor` di ciascuna etichetta sullo stesso colore della proprietà `BackColor`.

    > [!TIP]
    > Un altro modo per nascondere controlli quali le etichette consiste nell'impostare la relativa proprietà **Visible** su `False`.

6. Per nascondere le icone, arrestare il programma e rimuovere i contrassegni di commento per la riga di codice commentata nel ciclo `For Each`.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]

7. Nella barra dei menu fare clic sul pulsante **Salva tutto** per salvare il programma, quindi eseguirlo. Le icone sembrano essere scomparse, è presente soltanto uno sfondo blu. Le icone tuttavia sono assegnate casualmente e sono ancora al loro posto. Essendo dello stesso colore dello sfondo, le icone non vengono visualizzate dal giocatore. Dopo tutto, non sarebbe un gioco particolarmente impegnativo se il giocatore potesse visualizzare subito tutte le icone!

### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 4: Aggiungere un gestore degli eventi Click a ogni etichetta](../ide/step-4-add-a-click-event-handler-to-each-label.md).

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 2: aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
