---
title: 'Passaggio 6: aggiungere un problema di sottrazione | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 793204bf4a08d09d7ce6e48e37254dd311ac6a08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229242"
---
# <a name="step-6-add-a-subtraction-problem"></a>Passaggio 6: aggiungere un problema di sottrazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella sesta parte di questa esercitazione si aggiungerà un problema di sottrazione e si apprenderà come eseguire le attività seguenti:  
  
-   Archiviare i valori della sottrazione.  
  
-   Generare numeri casuali per il problema e verificare che la risposta sia compresa tra 0 e 100.  
  
-   Aggiornare il metodo che controlla le risposte in modo che verifichi anche il nuovo problema di sottrazione.  
  
-   Aggiornare il gestore dell'evento Tick del timer in modo che fornisca la risposta corretta quando il tempo scade.  
  
### <a name="to-add-a-subtraction-problem"></a>Per aggiungere un problema di sottrazione  
  
1.  Aggiungere al form due variabili Integer per il problema di sottrazione, tra le variabili Integer per il problema di addizione e il timer. Il codice dovrebbe essere analogo al seguente.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]  
  
     I nomi delle nuove variabili Integer, **minuendo** e **sottraendo**, non sono termini di programmazione. Si tratta dei nomi tradizionali in aritmetica per il numero che si sta sottraendo (il sottraendo) e il numero da cui si sottrae (il minuendo). La differenza è il minuendo meno il sottraendo. È possibile utilizzare altri nomi, perché il programma non richiede nomi specifici per variabili, controlli, componenti o metodi. È necessario attenersi alle regole, ad esempio i nomi non devono iniziare con una cifra, ma è in genere possibile utilizzare nomi quali x1, x2, x3 e x4. Tuttavia, i nomi generici rendono il codice difficile da leggere e complicano il rilevamento dei problemi. Per mantenere univoci e significativi i nomi delle variabili, più avanti in questa esercitazione si useranno i nomi tradizionali per la moltiplicazione (moltiplicando × moltiplicatore = prodotto) e di divisione (dividendo ÷ divisore = quoziente).  
  
     A questo punto, verrà modificato il metodo `StartTheQuiz()` per fornire valori casuali per il problema di sottrazione.  
  
2.  Aggiungere il codice seguente dopo il commento "Completare il problema di sottrazione".  
  
     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]  
  
     Per evitare risposte negative per il problema di sottrazione, nel codice il metodo `Next()` della classe `Random` viene utilizzato in modo diverso rispetto al problema di addizione. Quando si assegnano due valori al metodo `Next()`, viene scelto un numero casuale maggiore o uguale al primo valore e minore del secondo. Nel codice seguente viene scelto un numero casuale da 1 a 100, che viene archiviato nella variabile minuendo.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]  
  
     È possibile chiamare in più modi il metodo `Next()` della classe `Random`, denominato "randomizer" in questa esercitazione. I metodi che è possibile chiamare in più modi sono denominati metodi di overload ed è possibile utilizzare IntelliSense per esplorarli. Esaminare nuovamente la descrizione comando della finestra di IntelliSense per il metodo `Next()`.  
  
     ![Descrizione comando della finestra di IntelliSense](../ide/media/express-overloads.png "Express_Overloads")  
Descrizione comando della finestra di IntelliSense  
  
     La dicitura **(+ 2 overload(s))** della descrizione comando indica che è possibile chiamare il metodo `Next()` in altri due modi. Gli overload contengono numeri o tipi di argomenti diversi, pertanto funzionano in modo leggermente diverso l'uno dall'altro. Ad esempio, un metodo potrebbe accettare un argomento Integer singolo, mentre uno degli overload potrebbe accettare un Integer e una stringa. Scegliere l'overload corretto in base all'operazione da eseguire. Quando si aggiunge codice al metodo `StartTheQuiz()`, nella finestra di Intellisense vengono visualizzate più informazioni non appena si immette `randomizer.Next(`. Premere i tasti freccia SU e GIÙ per scorrere gli overload, come illustrato nell'immagine seguente.  
  
     ![Overload per il metodo Next&#40;&#41; in IntelliSense](../ide/media/express-nextoverload.png "Express_NextOverload")  
Overload per il metodo Next() in IntelliSense  
  
     In questo caso, si desidera scegliere l'ultimo overload, perché consente di specificare i valori minimo e massimo.  
  
3.  Modificare il metodo `CheckTheAnswer()` per verificare la risposta corretta per la sottrazione.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]  
  
     In Visual C# `&&` corrisponde all'operatore `logical and`. In Visual Basic l'operatore equivalente è `AndAlso`. Questi operatori indicano "Se la somma di addendo1 e addendo2 è uguale al valore NumericUpDown della somma e se minuendo meno sottraendo è uguale al valore NumericUpDown della differenza". Il metodo `CheckTheAnswer()` restituisce `true` solo se le risposte ai problemi dell'addizione e della sottrazione sono corrette.  
  
4.  Sostituire l'ultima parte del gestore eventi Tick del timer con il codice seguente in modo che inserisca la risposta corretta alla scadenza del tempo.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]  
  
5.  Salvare ed eseguire il codice.  
  
     Il programma include un problema di sottrazione, come illustrato nella figura seguente.  
  
     ![Quiz matematico con sottrazione](../ide/media/express-addsubtract.png "Express_AddSubtract")  
Quiz matematico con sottrazione  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 7: aggiungere problemi di moltiplicazione e divisione](../ide/step-7-add-multiplication-and-division-problems.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 5: aggiungere gestori di eventi Enter per i controlli NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).



