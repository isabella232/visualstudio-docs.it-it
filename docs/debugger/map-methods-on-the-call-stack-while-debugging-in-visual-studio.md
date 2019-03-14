---
title: Creare una mappa visiva dello stack di chiamate | Microsoft Docs
ms.date: 11/26/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da49cd81ea309df2d8e2bd0b4c41c28a84564fa8
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526090"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Creare una mappa visiva dello stack di chiamate durante il debug (C#, Visual Basic, C++, JavaScript)

Creare una mappa del codice per tracciare visivamente lo stack di chiamate durante il debug. È possibile inserire note sulla mappa per tenere traccia del codice e concentrarsi sull'individuazione dei bug.

Per informazioni dettagliate, vedere questo video: [Video: Debug visivo con integrazione del debugger della mappa codici (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

Per informazioni dettagliate sui comandi e le azioni è possibile usare con le mappe codici, vedere [cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>È possibile creare solo nelle mappe codici [Visual Studio Enterprise edition](https://visualstudio.microsoft.com/downloads/).

Ecco un rapido controllo di una mappa del codice:

 ![Debug con stack di chiamate in mappe codici](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

##  <a name="MapStack"></a> Eseguire il mapping dello stack di chiamate

1. In Visual Studio Enterprise C#, Visual Basic, C++ o JavaScript del progetto, avviare il debug, selezionando **eseguire il Debug** > **Avvia debug** oppure premendo **F5**.

1. Dopo che l'app passa alla modalità di interruzione o si esegue una funzione, selezionare **Debug** > **Mappa codici**, oppure premere **Ctrl**+**MAIUSC** +**`**.

   Lo stack di chiamate corrente verrà visualizzato in arancione in una nuova mappa codici:

   ![Vedere stack di chiamate nella mappa del codice](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Il codice mappato automaticamente gli aggiornamenti mentre si continua il debug. Modifica gli elementi della mappa o il layout non influenza sul codice in alcun modo. È possibile rinominare, spostare o rimuovere qualsiasi elemento nella mappa.

Per ottenere ulteriori informazioni su un elemento, passare il mouse su di esso ed esaminare la descrizione comando. È anche possibile selezionare **legenda** sulla barra degli strumenti per informazioni su cosa significa che ogni icona.

![Legenda della mappa del codice](../debugger/media/debuggermap_showlegend.png "legenda della mappa del codice")

>[!NOTE]
>Il messaggio **il diagramma potrebbe essere basato su una versione precedente del codice** nella parte superiore del codice di mappa indica che il codice sia stato modificato dopo l'ultimo aggiornamento della mappa. Ad esempio, nel codice potrebbe non essere più disponibile una chiamata alla mappa. Chiudere il messaggio, quindi provare a ricompilare la soluzione prima di aggiornare di nuovo la mappa.

## <a name="map-external-code"></a>Mappa codice esterno

Per impostazione predefinita, nella mappa viene visualizzato solo il proprio codice. Per visualizzare il codice esterno sulla mappa:

- Fare doppio clic nella **Stack di chiamate** finestra e selezionare **Mostra codice esterno**:

  ![Visualizzare il codice esterno tramite la finestra Stack di chiamate](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- O, deselezionare **Abilita Just My Code** in Visual Studio **Tools** (o **Debug**) > **opzioni**  >   **Debug**:

  ![Mostra codice esterno tramite una finestra di dialogo Opzioni](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Controllare il layout della mappa

Modifica il layout della mappa non influenza sul codice in alcun modo.

Per controllare il layout della mappa, selezionare la **Layout** menu sulla barra degli strumenti della mappa.

Nel **Layout** menu, è possibile:

-   Modificare il layout predefinito.
-   Arrestare automaticamente la ridisposizione della mappa deselezionando **Layout automatico durante il debug**.
-   Ridisporre la mappa il meno possibile quando si aggiungono elementi, deselezionando **Layout incrementale**.

##  <a name="MakeNotes"></a> Aggiungere note sul codice

È possibile aggiungere commenti per tenere traccia di ciò che avviene nel codice.

Per aggiungere un commento, fare doppio clic nella mappa del codice e selezionare **Edit** > **nuovo commento**, quindi digitare il commento.

Per aggiungere una nuova riga in un commento, premere **Shift**+**invio**.

 ![Aggiungere un commento allo stack di chiamate nella mappa codici](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

##  <a name="UpdateMap"></a> Aggiornare la mappa con lo stack di chiamate successivo

Quando si esegue l'app per il punto di interruzione successivo o il passaggio in una funzione, la mappa aggiungerà automaticamente nuovi stack di chiamate.

![Aggiornare la mappa codice con stack di chiamate successivo](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Per interrompere la mappa di aggiungere automaticamente nuovi stack di chiamate, selezionare ![Show stack di chiamate nella mappa del codice automaticamente](../debugger/media/debuggermap_automaticupdateicon.gif "Show stack di chiamate nella mappa del codice automaticamente") sulla barra degli strumenti della mappa codice. La mappa continuerà a evidenziare gli stack di chiamate esistenti. Per aggiungere manualmente lo stack di chiamate corrente alla mappa, premere **Ctrl**+**MAIUSC**+**`**.

##  <a name="AddRelatedCode"></a> Aggiungere il codice correlato alla mappa

Ora che disponibile una mappa, in C# o Visual Basic, è possibile aggiungere elementi, ad esempio campi, proprietà e altri metodi, per tenere traccia di ciò che avviene nel codice.

Per passare alla definizione di un metodo nel codice, fare doppio clic sul metodo nella mappa, oppure selezionarlo e premere **F12**, o pulsante destro del mouse e selezionare **Vai a definizione**.

![Passare alla definizione di codice per un metodo nella mappa del codice](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Per aggiungere gli elementi che si vuole tenere traccia per la mappa, fare doppio clic su un metodo e selezionare gli elementi di cui che si vuole tenere traccia. Gli elementi aggiunti più di recente sono indicati in verde.

![Campi correlati a un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Per impostazione predefinita, quando si aggiungono gli elementi alla mappa si aggiungono anche i nodi di gruppo padre, ad esempio la classe, spazio dei nomi e l'assembly. È possibile attivare e disattivare questa funzionalità selezionando il **Includi padri** pulsante sulla barra degli strumenti della mappa codice o premendo **Ctrl** mentre si aggiungono elementi.

![Visualizzare i campi di un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Continuare a compilare la mappa per visualizzare altro codice.

 ![Vedere i metodi che usano un campo: mappa del codice dello stack di chiamate](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![I metodi che usano un campo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

##  <a name="FindBugs"></a> Individuare bug usando la mappa
 Visualizzando il codice, sarà possibile rilevare i bug più rapidamente. Si supponga, ad esempio, che si sta esaminando un bug in un'app di disegno. Quando si disegna una linea e si tenta di annullare l'operazione, non accadrà nulla finché non si disegnerà un'altra riga.

 Pertanto, impostare punti di interruzione nei metodi `clear`, `undo` e `Repaint`, avviare il debug e compilare una mappa come quella indicata di seguito:

 ![Aggiungere un altro stack di chiamate alla mappa codici](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Tutte le azioni dell'utente nella mappa chiamano `Repaint`, tranne `undo`. Ciò potrebbe spiegare per quale motivo `undo` non funziona nell'immediato.

 Dopo la correzione del bug e continuare a eseguire l'app, la mappa aggiungerà la nuova chiamata da `undo` a `Repaint`:

 ![Aggiungere nuovo metodo chiamata allo stack di chiamate nella mappa del codice](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Condividere la mappa con altri utenti

È possibile esportare una mappa, inviarla ad altri utenti con Microsoft Outlook, salvarlo alla soluzione e archiviarlo nel controllo della versione.

Per condividere o salvare la mappa, usare **condividere** sulla barra degli strumenti della mappa codice.

![Mappa del codice dello stack chiamate condivisione con altri utenti](../debugger/media/debuggermap_sharewithothers.png "mappa del codice dello stack chiamate condivisione con altri utenti")

## <a name="see-also"></a>Vedere anche
[Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)

[Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)

[Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
