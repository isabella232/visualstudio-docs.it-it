---
title: Mappare i metodi sullo stack di chiamate durante il debug
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4597f1352e02033c55fcdced126e184f854b463
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067398"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Mappare i metodi sullo stack di chiamate durante il debug in Visual Studio
Creare una mappa del codice per tracciare visivamente lo stack di chiamate durante il debug. È possibile inserire note sulla mappa per tenere traccia dell'attività del codice e in tal modo concentrarsi sull'individuazione di bug.

 ![Debug con stack di chiamate nelle mappe del codice](../debugger/media/debuggermap_overview.png)

 Sono necessari:

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

- Codice che è possibile eseguire il debug, ad esempio Visual c#, Visual Basic, C++, JavaScript o X + +

  Vedere:

- [Video: Debug visivo con integrazione del debugger della mappa codici (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

- [Eseguire il mapping dello stack di chiamate](#MapStack)

- [Aggiungere appunti sul codice](#MakeNotes)

- [Aggiornare la mappa con lo stack di chiamate successivo](#UpdateMap)

- [Aggiungere il codice correlato alla mappa](#AddRelatedCode)

- [Individuare bug usando la mappa](#FindBugs)

- [DOMANDE E RISPOSTE](#QA)

  Per informazioni dettagliate dei comandi e le azioni è possibile usare quando si lavora con le mappe codici, vedere [cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Eseguire il mapping dello stack di chiamate

1.  Avviare il debug. (Tastiera: **F5**)

2.  Dopo che l'app passa alla modalità di interruzione o si esegue una funzione, scegli **mappa codice**. (Tastiera: **Ctrl** + **MAIUSC** + **`**)

     ![Scegliere la mappa del codice per avviare il mapping dello stack di chiamate](../debugger/media/debuggermap_choosecodemap.png)

     Lo stack di chiamate corrente verrà visualizzato in arancione in una nuova mappa del codice:

     ![Visualizzare lo stack di chiamate nella mappa del codice](../debugger/media/debuggermap_seeundocallstack.png)

     La mappa si aggiornerà automaticamente durante il debug. Visualizzare [aggiornare la mappa con lo stack di chiamate successivo](#UpdateMap).

## <a name="MakeNotes"></a> Aggiungere note sul codice
 Aggiungere commenti per tenere traccia di ciò che avviene nel codice. Per aggiungere una nuova riga in un commento, premere **MAIUSC + INVIO**.

 ![Aggiungere un commento allo stack di chiamate nella mappa del codice](../debugger/media/debuggermap_addcomment.png)

## <a name="UpdateMap"></a> Aggiornare la mappa con lo stack di chiamate successivo
 Eseguire l'app fino al punto di interruzione successivo o eseguire una funzione. La mappa aggiungerà un nuovo stack di chiamate.

 ![Aggiornare la mappa del codice con lo stack di chiamate successivo](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="AddRelatedCode"></a> Aggiungere il codice correlato alla mappa
 Ora hai una mappa - che cosa successivamente? Se si lavora con c# o Visual Basic, aggiungere elementi, ad esempio campi, proprietà e altri metodi, per tenere traccia di ciò che avviene nel codice.

 Fare doppio clic su un metodo per visualizzarne la definizione del codice o usare il menu di scelta rapida del metodo. (Tastiera: selezionare il metodo nella mappa e premere **F12**)

 ![Passare alla definizione del codice per un metodo nella mappa del codice](../debugger/media/debuggermap_gotocodedefinition.png)

 Aggiungere gli elementi di cui si vuole tenere traccia nella mappa.

 ![Visualizzare i campi di un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
>  Per impostazione predefinita, quando si aggiungono gli elementi alla mappa si aggiungono anche i nodi di gruppo padre, ad esempio la classe, spazio dei nomi e l'assembly. Sebbene questo sia utile, è possibile mantenere la mappa semplice disattivando questa funzionalità usando il **Includi padri** pulsante sulla barra degli strumenti della mappa o premendo **CTRL** quando si aggiungono elementi.

 ![Campi correlati a un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_showedfields.png)

 Di seguito è possibile visualizzare i metodi in cui vengono usati gli stessi campi. Gli elementi aggiunti più di recente sono indicati in verde.

 Continuare a compilare la mappa per visualizzare altro codice.

 ![Visualizzare i metodi che usano un campo: mappa del codice dello stack di chiamate](../debugger/media/debuggermap_findallreferences.png)

 ![Metodi che usano un campo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_foundallreferences.png)

## <a name="FindBugs"></a> Individuare bug usando la mappa
 Visualizzando il codice, sarà possibile rilevare i bug più rapidamente. Si supponga, ad esempio, che si sta esaminando un bug in un programma di disegno. Quando si disegna una linea e si tenta di annullare l'operazione, non accadrà nulla finché non si disegnerà un'altra riga.

 Pertanto, impostare punti di interruzione nei metodi `clear`, `undo` e `Repaint`, avviare il debug e compilare una mappa come quella indicata di seguito:

 ![Aggiungere un altro stack di chiamate alla mappa del codice](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Tutte le azioni dell'utente nella mappa chiamano `Repaint`, tranne `undo`. Ciò potrebbe spiegare per quale motivo `undo` non funziona nell'immediato.

 Dopo aver corretto il bug e continuato a eseguire il programma, la mappa aggiungerà la nuova chiamata da `undo` in `Repaint`:

 ![Aggiungere una nuova chiamata di metodo allo stack di chiamate nella mappa del codice](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="QA"></a> Domande e risposte

- **Non tutte le chiamate vengono visualizzate sulla mappa. Perché?**

   Per impostazione predefinita, nella mappa viene visualizzato solo il proprio codice. Per visualizzare il codice esterno, attivarlo nella **Stack di chiamate** finestra:

   ![Visualizzare il codice esterno tramite la finestra Stack di chiamate](../debugger/media/debuggermap_callstackmenu.png)

   oppure disattivare **Abilita Just My Code** nelle opzioni di debug di Visual Studio:

   ![Scegliere Mostra codice esterno nella finestra di dialogo Opzioni](../debugger/media/debuggermap_debugoptions.png)

- **La modifica della mappa influisce il codice?**

   La modifica della mappa non influenza sul codice in alcun modo. È possibile rinominare, spostare o rimuovere qualsiasi elemento nella mappa.

- **Che cosa significa questo messaggio: "il diagramma potrebbe essere basato su una versione precedente del codice"?**

   È possibile che il codice sia stato modificato dopo l'ultimo aggiornamento della mappa. Ad esempio, nel codice potrebbe non essere più disponibile una chiamata alla mappa. Chiudere il messaggio, quindi provare a ricompilare la soluzione prima di aggiornare di nuovo la mappa.

- **Come si controlla il layout della mappa?**

   Aprire il **Layout** menu sulla barra degli strumenti della mappa:

  -   Modificare il layout predefinito.

  -   Per arrestare automaticamente la ridisposizione della mappa, disattivare **Layout automatico durante il debug**.

  -   Per ridisporre la mappa il meno possibile quando si aggiungono elementi, disattivare **Layout incrementale**.

- **È possibile condividere la mappa con altri utenti?**

   È possibile esportare la mappa, inviarla ad altri se si dispone di Microsoft Outlook o salvarla alla soluzione in modo che è possibile archiviarlo nel controllo del codice sorgente.

   ![Condividere la mappa del codice dello stack di chiamate con altri utenti](../debugger/media/debuggermap_sharewithothers.png)

- **Come si interrompono la mappa di aggiungere automaticamente nuovi stack di chiamate?**

   Scegli ![pulsante &#45; Mostra stack di chiamate nella mappa del codice automaticamente](../debugger/media/debuggermap_automaticupdateicon.gif) sulla barra degli strumenti della mappa. Per aggiungere manualmente lo stack di chiamate corrente alla mappa, premere **Ctrl** + **MAIUSC** + **`**.

   La mappa continuerà a evidenziare gli stack di chiamate esistenti sulla mappa durante il debug.

- **Le icone degli elementi e le frecce significato**

   Per ottenere altre informazioni su un elemento, spostare il puntatore del mouse su di esso ed esaminare la descrizione comando. È anche possibile esaminare i **legenda** per informazioni su cosa significa che ogni icona.

   ![Significato delle icone nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_showlegend.png)

  Vedere:

- [Eseguire il mapping dello stack di chiamate](#MapStack)

- [Aggiungere appunti sul codice](#MakeNotes)

- [Aggiornare la mappa con lo stack di chiamate successivo](#UpdateMap)

- [Aggiungere il codice correlato alla mappa](#AddRelatedCode)

- [Individuare bug usando la mappa](#FindBugs)

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
