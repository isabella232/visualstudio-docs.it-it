---
title: 'Passaggio 6: Aggiungere un problema di sottrazione'
description: Informazioni su come aggiungere un problema di sottrazione e su come eseguire attività.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e959a1ef4e813510a7a5963c144022748a4b85c9
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398242"
---
# <a name="step-6-add-a-subtraction-problem"></a>Passaggio 6: Aggiungere un problema di sottrazione
Nella sesta parte di questa esercitazione si aggiungerà un problema di sottrazione e si apprenderà come eseguire le attività seguenti:

- Archiviare i valori della sottrazione.

- Generare numeri casuali per il problema e verificare che la risposta sia compresa tra 0 e 100.

- Aggiornare il metodo che controlla le risposte in modo che verifichi anche il nuovo problema di sottrazione.

- Aggiornare il gestore dell'evento <xref:System.Windows.Forms.Timer.Tick> del timer in modo che inserisca la risposta corretta quando il tempo scade.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico](../ide/tutorial-2-create-a-timed-math-quiz.md)a tempo.

## <a name="to-add-a-subtraction-problem"></a>Per aggiungere un problema di sottrazione

1. Aggiungere al form due variabili Integer per il problema di sottrazione, tra le variabili Integer per il problema di addizione e il timer. Il codice dovrebbe essere analogo al seguente.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet12":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     I nomi delle nuove variabili Integer, **minuendo** e **sottraendo**, non sono termini di programmazione. Si tratta dei nomi tradizionali in aritmetica per il numero che si sta sottraendo (il sottraendo) e il numero da cui si sottrae (il minuendo). La differenza è il minuendo meno il sottraendo. È possibile utilizzare altri nomi, perché il programma non richiede nomi specifici per variabili, controlli, componenti o metodi. È necessario attenersi alle regole, ad esempio i nomi non devono iniziare con una cifra, ma è in genere possibile utilizzare nomi quali x1, x2, x3 e x4. Tuttavia, i nomi generici rendono il codice difficile da leggere e complicano il rilevamento dei problemi. Per mantenere univoci e significativi i nomi delle variabili, più avanti in questa esercitazione si useranno i nomi tradizionali per la moltiplicazione (moltiplicando × moltiplicatore = prodotto) e di divisione (dividendo ÷ divisore = quoziente).

     A questo punto, verrà modificato il metodo `StartTheQuiz()` per fornire valori casuali per il problema di sottrazione.

2. Aggiungere il codice seguente dopo il commento "Completare il problema di sottrazione".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet13":::

     Per evitare risposte negative per il problema di sottrazione, nel codice il metodo <xref:System.Random.Next> della classe <xref:System.Random> viene utilizzato in modo diverso rispetto al problema di addizione. Quando si assegnano due valori al metodo `Next()`, viene scelto un numero casuale maggiore o uguale al primo valore e minore del secondo. Nel codice seguente viene scelto un numero casuale da 1 a 100, che viene archiviato nella variabile minuendo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet21":::

     È possibile chiamare in più modi il metodo `Next()` della classe Random, a cui in precedenza in questa esercitazione è stato assegnato il nome "randomizer". I metodi che è possibile chiamare in più modi sono denominati metodi di overload ed è possibile utilizzare IntelliSense per esplorarli. Esaminare nuovamente la descrizione comando della finestra di IntelliSense per il metodo `Next()`.

     ![Descrizione comando della finestra intelliSense](../ide/media/express_overloads.png)<br/>
***IntelliSense** _ _window comando*

     La dicitura **(+ 2 overload(s))** della descrizione comando indica che è possibile chiamare il metodo `Next()` in altri due modi. Gli overload contengono numeri o tipi di argomenti diversi, pertanto funzionano in modo leggermente diverso l'uno dall'altro. Ad esempio, un metodo potrebbe accettare un singolo argomento Integer, mentre uno degli overload potrebbe accettare un Integer e una stringa. Scegliere l'overload corretto in base all'operazione da eseguire. Quando si aggiunge codice al metodo `StartTheQuiz()`, nella finestra di IntelliSense vengono visualizzate altre informazioni non appena si immette `randomizer.Next(`. Per scorrere gli overload, usare i tasti **freccia SU** e **freccia GIÙ**, come illustrato nella figura seguente:

     ![Overload per il metodo Next&#40;&#41; in IntelliSense](../ide/media/express_nextoverload.png)<br/>
*Overload per*  * **Next()** _ _method in* ***IntelliSense***

     In questo caso, si desidera scegliere l'ultimo overload, perché consente di specificare i valori minimo e massimo.

3. Modificare il metodo `CheckTheAnswer()` per verificare la risposta corretta per la sottrazione.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet14":::

     In C# è `&&` `logical and` l'operatore . In Visual Basic l'operatore equivalente è `AndAlso`. Questi operatori indicano "Se la somma di addendo1 e addendo2 è uguale al valore NumericUpDown della somma e se minuendo meno sottraendo è uguale al valore NumericUpDown della differenza". Il metodo `CheckTheAnswer()` restituisce `true` solo se le risposte ai problemi dell'addizione e della sottrazione sono corrette.

4. Sostituire l'ultima parte del gestore eventi Tick del timer con il codice seguente in modo che inserisca la risposta corretta alla scadenza del tempo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet22":::

5. Salvare ed eseguire il codice.

     Il programma include un problema di sottrazione, come illustrato nella figura seguente:

     ![Quiz matematico con sottrazione](../ide/media/express_addsubtract.png)<br/>
***Quiz matematico** _ _with problema di sottrazione*

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 7: Aggiungere problemi di moltiplicazione e divisione](../ide/step-7-add-multiplication-and-division-problems.md)**.

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 5: Aggiungere gestori dell'evento Enter per i controlli NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
