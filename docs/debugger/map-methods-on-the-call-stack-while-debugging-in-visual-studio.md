---
title: Creare una mappa visiva dello stack di chiamate | Microsoft Docs
description: Creare una mappa del codice per tracciare visivamente lo stack di chiamate durante il debug. Prendere nota della mappa per tenere traccia delle cose che il codice sta eseguendo, in modo da potersi concentrare sulla ricerca di bug.
ms.custom: SEO-VS-2020
ms.date: 11/26/2018
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a726f73a866fc6b275877f3a457d3b2f6ed08dc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097077"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Creare una mappa visiva dello stack di chiamate durante il debug (C#, Visual Basic, C++, JavaScript)

Creare una mappa del codice per tracciare visivamente lo stack di chiamate durante il debug. È possibile inserire note sulla mappa per tenere traccia del codice e concentrarsi sull'individuazione dei bug.

Per informazioni dettagliate, vedere questo video: [Video: Debug visivo con integrazione del debugger della mappa codici (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

Per informazioni dettagliate sui comandi e sulle azioni che è possibile usare con le mappe codice, vedere [Esplorare e ridisporre le mappe codice.](../modeling/browse-and-rearrange-code-maps.md)

>[!IMPORTANT]
>È possibile creare mappe codice solo in [Visual Studio Enterprise edizione](https://visualstudio.microsoft.com/downloads).

Ecco un rapido sguardo a una mappa del codice:

 ![Debug con stack di chiamate nelle mappe codici](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Eseguire il mapping dello stack di chiamate

1. In un Visual Studio Enterprise C#, Visual Basic, C++ o JavaScript, avviare il debug selezionando **Debug** Avvia debug  >   o premendo **F5.**

1. Dopo che l'app ha attivata la modalità di interruzione o si è attivata una funzione, selezionare Debug Code Map **(Esegui** debug mappa codice)  >  o premere **CTRL** +  + **`** MAIUSC.

   Lo stack di chiamate corrente verrà visualizzato in arancione in una nuova mappa codici:

   ![Visualizzare lo stack di chiamate nella mappa codici](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

La mappa codice viene aggiornata automaticamente quando si continua il debug. La modifica degli elementi della mappa o del layout non influisce in alcun modo sul codice. È possibile rinominare, spostare o rimuovere qualsiasi elemento nella mappa.

Per ottenere altre informazioni su un elemento, passare il mouse su di esso ed esaminare la descrizione comando dell'elemento. È anche possibile selezionare **Legenda** sulla barra degli strumenti per informazioni sul significato di ogni icona.

![Legenda mappa codice](../debugger/media/debuggermap_showlegend.png "Legenda mappa codice")

>[!NOTE]
>Il messaggio **Il diagramma può** essere basato su una versione precedente del codice nella parte superiore della mappa codice significa che il codice potrebbe essere stato modificato dopo l'ultimo aggiornamento della mappa. Ad esempio, nel codice potrebbe non essere più disponibile una chiamata alla mappa. Chiudere il messaggio, quindi provare a ricompilare la soluzione prima di aggiornare di nuovo la mappa.

## <a name="map-external-code"></a>Eseguire il mapping di codice esterno

Per impostazione predefinita, nella mappa viene visualizzato solo il proprio codice. Per visualizzare il codice esterno sulla mappa:

- Fare clic con il pulsante destro **del mouse nella** finestra Stack di chiamate e scegliere Mostra codice **esterno**:

  ![Visualizzare il codice esterno tramite la finestra Stack di chiamate](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- In caso contrario, **deselezionare Enable Just My Code** in Visual Studio **Tools** (o **Debug)**> **Options**  >  **Debugging**:

  ![Scegliere Mostra codice esterno nella finestra di dialogo Opzioni](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Controllare il layout della mappa

La modifica del layout della mappa non influisce in alcun modo sul codice.

Per controllare il layout della mappa, selezionare il menu **Layout** sulla barra degli strumenti della mappa.

Nel menu **Layout** è possibile:

- Modificare il layout predefinito.
- Interrompere la riorganizzazione automatica della mappa deselezionando **Layout automatico durante il debug** di .
- Ridisporre la mappa il meno possibile quando si aggiungono elementi deselezionando **Layout incrementale**.

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Aggiungere note sul codice

È possibile aggiungere commenti per tenere traccia di ciò che accade nel codice.

Per aggiungere un commento, fare clic con il pulsante destro del mouse sulla mappa codice e scegliere **Modifica**  >  **nuovo commento** e quindi digitare il commento.

Per aggiungere una nuova riga in un commento, premere + **MAIUSC+INVIO.**

 ![Aggiungere un commento allo stack di chiamate nella mappa del codice](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Aggiornare la mappa con lo stack di chiamate successivo

Quando si esegue l'app al punto di interruzione successivo o si esegue un'istruzione in una funzione, la mappa aggiunge automaticamente nuovi stack di chiamate.

![Aggiornare la mappa del codice con lo stack di chiamate successivo](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Per impedire alla mappa di aggiungere automaticamente nuovi stack di chiamate, selezionare Mostra automaticamente stack di chiamate sulla mappa ![codice](../debugger/media/debuggermap_automaticupdateicon.gif "Mostra automaticamente lo stack di chiamate sulla mappa codice") sulla barra degli strumenti della mappa codice. La mappa continua a evidenziare gli stack di chiamate esistenti. Per aggiungere manualmente lo stack di chiamate corrente alla mappa, premere **CTRL** + **MAIUSC** + **`** .

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Aggiungere il codice correlato alla mappa

Ora che è disponibile una mappa, in C# o Visual Basic, è possibile aggiungere elementi come campi, proprietà e altri metodi per tenere traccia di ciò che accade nel codice.

Per passare alla definizione di un metodo nel codice, fare doppio clic sul metodo nella mappa oppure selezionarlo e premere **F12** oppure fare clic con il pulsante destro del mouse su di esso e scegliere Vai a **definizione**.

![Passare alla definizione del codice per un metodo nella mappa del codice](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Per aggiungere alla mappa gli elementi di cui si vuole tenere traccia, fare clic con il pulsante destro del mouse su un metodo e selezionare gli elementi di cui si vuole tenere traccia. Gli elementi aggiunti più di recente vengono visualizzati in verde.

![Campi correlati a un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Per impostazione predefinita, quando si aggiungono gli elementi alla mappa si aggiungono anche i nodi di gruppo padre, ad esempio la classe, spazio dei nomi e l'assembly. È possibile disattivare e attivare  questa funzionalità selezionando il pulsante Includi elementi padre sulla barra degli strumenti della mappa codice oppure premendo **CTRL** mentre si aggiungono elementi.

![Visualizzare i campi di un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Continuare a compilare la mappa per visualizzare altro codice.

 ![Visualizzare i metodi che usano un campo: mappa codici dello stack di chiamate](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Metodi che usano un campo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Individuare bug usando la mappa
 Visualizzando il codice, sarà possibile rilevare i bug più rapidamente. Si supponga, ad esempio, di analizzare un bug in un'app di disegno. Quando si disegna una linea e si tenta di annullare l'operazione, non accadrà nulla finché non si disegnerà un'altra riga.

 Pertanto, impostare punti di interruzione nei metodi `clear`, `undo` e `Repaint`, avviare il debug e compilare una mappa come quella indicata di seguito:

 ![Aggiungere un altro stack di chiamate alla mappa codici](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Tutte le azioni dell'utente nella mappa chiamano `Repaint`, tranne `undo`. Ciò potrebbe spiegare per quale motivo `undo` non funziona nell'immediato.

 Dopo aver risolto il bug e aver continuato l'esecuzione dell'app, la mappa aggiunge la nuova chiamata da `undo` a `Repaint` :

 ![Aggiungere una nuova chiamata di metodo allo stack di chiamate nella mappa codici](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Condividere la mappa con altri utenti

È possibile esportare una mappa, inviarla ad altri utenti con Microsoft Outlook, salvarla nella soluzione e archiviarla nel controllo della versione.

Per condividere o salvare la mappa, usare **Condividi nella** barra degli strumenti della mappa codice.

![Condividere la mappa codici dello stack di chiamate con altri utenti](../debugger/media/debuggermap_sharewithothers.png "Condividere la mappa codici dello stack di chiamate con altri utenti")

## <a name="see-also"></a>Vedi anche
[Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)

[Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)

[Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
