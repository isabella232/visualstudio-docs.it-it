---
title: Mappare i metodi sullo stack di chiamate durante il debug
ms.date: 11/04/2016
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 736b203feb5b1a640d7865b92a6d3ad191397d26
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985039"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Mappare i metodi sullo stack di chiamate durante il debug in Visual Studio

Creare una mappa del codice per tracciare visivamente lo stack di chiamate durante il debug. È possibile inserire note sulla mappa per tenere traccia dell'attività del codice e in tal modo concentrarsi sull'individuazione di bug.

 ![Debug con stack di chiamate nelle mappe codici](../debugger/media/debuggermap_overview.png)

 Sono necessari:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Codice di cui è possibile eseguire il debug, C#ad esempio Visual C++, Visual Basic,, JavaScript o X + +

  Vedere:

- [Video: debug visivo con l'integrazione del debugger con la mappa codici (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [Eseguire il mapping dello stack di chiamate](#MapStack)

- [Prendere nota del codice](#MakeNotes)

- [Aggiornare la mappa con lo stack di chiamate successivo](#UpdateMap)

- [Aggiungere il codice correlato alla mappa](#AddRelatedCode)

- [Individuare i bug usando la mappa](#FindBugs)

- [d & A](#QA)

  Per informazioni dettagliate sui comandi e sulle azioni che è possibile usare quando si usano le mappe codice, vedere [esplorare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Eseguire il mapping dello stack di chiamate

1. Avviare il debug. (Tastiera: **F5**)

2. Quando l'app entra in modalità di interruzioni o si esegue una funzione, scegliere **mappa codici**. (Tastiera: **Ctrl**  + **MAIUSC**  +  **`** )

     ![Scegliere la mappa del codice per avviare il mapping dello stack di chiamate](../debugger/media/debuggermap_choosecodemap.png)

     Lo stack di chiamate corrente verrà visualizzato in arancione in una nuova mappa codici:

     ![Visualizzare lo stack di chiamate nella mappa codici](../debugger/media/debuggermap_seeundocallstack.png)

     La mappa si aggiornerà automaticamente durante il debug. Vedere [aggiornare la mappa con lo stack di chiamate successivo](#UpdateMap).

## <a name="MakeNotes"></a> Aggiungere note sul codice

 Aggiungere commenti per tenere traccia di ciò che accade nel codice. Per aggiungere una nuova riga in un commento, premere **MAIUSC + INVIO**.

 ![Aggiungere un commento allo stack di chiamate nella mappa del codice](../debugger/media/debuggermap_addcomment.png)

## <a name="UpdateMap"></a> Aggiornare la mappa con lo stack di chiamate successivo

 Eseguire l'app fino al punto di interruzione successivo o eseguire una funzione. La mappa aggiungerà un nuovo stack di chiamate.

 ![Aggiornare la mappa del codice con lo stack di chiamate successivo](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="AddRelatedCode"></a> Aggiungere il codice correlato alla mappa

 A questo punto è disponibile una mappa: cosa succede? Se si usa C# o Visual Basic, aggiungere elementi, ad esempio campi, proprietà e altri metodi, per tenere traccia di ciò che accade nel codice.

 Fare doppio clic su un metodo per visualizzarne la definizione del codice o usare il menu di scelta rapida del metodo. (Tastiera: selezionare il metodo nella mappa e premere **F12**)

 ![Passare alla definizione del codice per un metodo nella mappa del codice](../debugger/media/debuggermap_gotocodedefinition.png)

 Aggiungere gli elementi di cui si vuole tenere traccia nella mappa.

 ![Visualizzare i campi di un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Per impostazione predefinita, quando si aggiungono gli elementi alla mappa si aggiungono anche i nodi di gruppo padre, ad esempio la classe, spazio dei nomi e l'assembly. Sebbene sia utile, è possibile tenere la mappa semplicemente disattivando questa funzionalità usando il pulsante **Includi padri** sulla barra degli strumenti della mappa oppure premendo **CTRL** quando si aggiungono elementi.

 ![Campi correlati a un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_showedfields.png)

 Di seguito è possibile visualizzare i metodi in cui vengono usati gli stessi campi. Gli elementi aggiunti più di recente sono indicati in verde.

 Continuare a compilare la mappa per visualizzare altro codice.

 ![Visualizzare i metodi che usano un campo: mappa codici dello stack di chiamate](../debugger/media/debuggermap_findallreferences.png)

 ![Metodi che usano un campo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_foundallreferences.png)

## <a name="FindBugs"></a> Individuare bug usando la mappa

 Visualizzando il codice, sarà possibile rilevare i bug più rapidamente. Si supponga, ad esempio, di esaminare un bug in un programma di disegno. Quando si disegna una linea e si tenta di annullare l'operazione, non accadrà nulla finché non si disegnerà un'altra riga.

 Pertanto, impostare punti di interruzione nei metodi `clear`, `undo` e `Repaint`, avviare il debug e compilare una mappa come quella indicata di seguito:

 ![Aggiungere un altro stack di chiamate alla mappa codici](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Tutte le azioni dell'utente nella mappa chiamano `Repaint`, tranne `undo`. Ciò potrebbe spiegare per quale motivo `undo` non funziona nell'immediato.

 Dopo aver corretto il bug e continuato a eseguire il programma, la mappa aggiungerà la nuova chiamata da `undo` in `Repaint`:

 ![Aggiungere una nuova chiamata di metodo allo stack di chiamate nella mappa codici](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="QA"></a> Domande e risposte

- **Non tutte le chiamate vengono visualizzate nella mappa. Perché?**

   Per impostazione predefinita, nella mappa viene visualizzato solo il proprio codice. Per visualizzare il codice esterno, attivarlo nella finestra **stack di chiamate** :

   ![Visualizzare il codice esterno tramite la finestra Stack di chiamate](../debugger/media/debuggermap_callstackmenu.png)

   in alternativa, disattivare **abilita Just My Code** nelle opzioni di debug di Visual Studio:

   ![Scegliere Mostra codice esterno nella finestra di dialogo Opzioni](../debugger/media/debuggermap_debugoptions.png)

- **La modifica della mappa influisce sul codice?**

   La modifica della mappa non influisce in alcun modo sul codice. È possibile rinominare, spostare o rimuovere qualsiasi elemento nella mappa.

- **Cosa significa questo messaggio: "il diagramma può essere basato su una versione precedente del codice"?**

   È possibile che il codice sia stato modificato dopo l'ultimo aggiornamento della mappa. Ad esempio, nel codice potrebbe non essere più disponibile una chiamata alla mappa. Chiudere il messaggio, quindi provare a ricompilare la soluzione prima di aggiornare di nuovo la mappa.

- **Ricerca per categorie controllare il layout della mappa?**

   Aprire il menu **layout** sulla barra degli strumenti della mappa:

  - Modificare il layout predefinito.

  - Per arrestare automaticamente la ridisposizione della mappa, disattivare **layout automatico durante il debug**.

  - Per ridisporre la mappa il meno possibile quando si aggiungono elementi, disattivare il **Layout incrementale**.

- **È possibile condividere la mappa con altri utenti?**

   È possibile esportare la mappa, inviarla ad altri se si dispone di Microsoft Outlook o salvarla nella soluzione in modo che sia possibile archiviarla nel controllo del codice sorgente.

   ![Condividere la mappa codici dello stack di chiamate con altri utenti](../debugger/media/debuggermap_sharewithothers.png)

- **Ricerca per categorie arrestare la mappa aggiungendo automaticamente nuovi stack di chiamate?**

   Scegliere ![pulsante &#45; Mostra stack di chiamate nella mappa del codice](../debugger/media/debuggermap_automaticupdateicon.gif)automaticamente sulla barra degli strumenti della mappa. Per aggiungere manualmente lo stack di chiamate corrente alla mappa, premere **Ctrl**  + **MAIUSC**  +  **`** .

   La mappa continuerà a evidenziare gli stack di chiamate esistenti sulla mappa durante il debug.

- **Cosa significano le icone e le frecce degli elementi?**

   Per ottenere altre informazioni su un elemento, spostare il puntatore del mouse su di esso ed esaminare la descrizione comando dell'elemento. È anche possibile esaminare la **Legenda** per informazioni sul significato di ogni icona.

   ![Significato delle icone nella mappa codici dello stack di chiamate](../debugger/media/debuggermap_showlegend.png)

  Vedere:

- [Eseguire il mapping dello stack di chiamate](#MapStack)

- [Prendere nota del codice](#MakeNotes)

- [Aggiornare la mappa con lo stack di chiamate successivo](#UpdateMap)

- [Aggiungere il codice correlato alla mappa](#AddRelatedCode)

- [Individuare i bug usando la mappa](#FindBugs)

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
