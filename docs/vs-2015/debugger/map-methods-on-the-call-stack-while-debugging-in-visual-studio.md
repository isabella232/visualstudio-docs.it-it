---
title: Mappare i metodi sullo stack di chiamate durante il debug
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 43
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3ddf45a48f6b9d8a5ac8155012f168703c67aa3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300786"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Mappare i metodi sullo stack di chiamate durante il debug in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Creare una mappa del codice per tracciare visivamente lo stack di chiamate durante il debug. È possibile inserire note sulla mappa per tenere traccia dell'attività del codice e in tal modo concentrarsi sull'individuazione di bug.

 ![Debug con stack di chiamate nelle mappe del codice](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Requisiti necessari:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Codice di cui è possibile eseguire il debug, ad esempio Visual C# .NET, Visual Basic .NET., C++, JavaScript o X++.

  Vedere: [video: debug visivo con l'integrazione del debugger con la mappa codici (Channel 9)](https://go.microsoft.com/fwlink/?LinkId=293418) • eseguire il [mapping dello stack di chiamate](#MapStack) • [creare note sul codice](#MakeNotes) • [aggiornare la mappa con lo stack di chiamate successivo](#UpdateMap) • [aggiungere il codice correlato alla mappa](#AddRelatedCode) • [individuare bug usando la mappa](#FindBugs) • [Q & a](#QA)

  Per informazioni dettagliate sui comandi e sulle azioni che è possibile usare quando si usano le mappe codice, vedere [Cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Eseguire il mapping dello stack di chiamate

1. Avviare il debug. (Tastiera: **F5**)

2. Dopo che l'app passa alla modalità di interruzione o si esegue una funzione, scegliere **Mappa codici**. (Tastiera: **Ctrl** + **MAIUSC** +  **`** )

     ![Scegliere la mappa codice per avviare il mapping dello stack di chiamate](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Lo stack di chiamate corrente verrà visualizzato in arancione in una nuova mappa codici:

     ![Vedere stack di chiamate nella mappa codici](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     La mappa si aggiornerà automaticamente durante il debug. Vedere [Aggiornare la mappa con lo stack di chiamate successivo](#UpdateMap).

## <a name="MakeNotes"></a> Aggiungere note sul codice
 Aggiungere commenti per tenere traccia delle operazioni in corso nel codice. Per aggiungere una nuova riga in un commento, premere **MAIUSC + INVIO**.

 ![Aggiungere un commento allo stack di chiamate nella mappa codici](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Aggiornare la mappa con lo stack di chiamate successivo
 Eseguire l'app fino al punto di interruzione successivo o eseguire una funzione. La mappa aggiungerà un nuovo stack di chiamate.

 ![Aggiornare la mappa del codice con lo stack di chiamate successivo](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a> Aggiungere il codice correlato alla mappa
 Ora che si dispone di una mappa, è possibile effettuare diverse operazioni. Se si usa Visual C# .NET o Visual Basic .NET, aggiungere elementi, ad esempio campi, proprietà e altri metodi, per tenere traccia delle operazioni in corso nel codice.

 Fare doppio clic su un metodo per visualizzarne la definizione del codice o usare il menu di scelta rapida del metodo. Tastiera: selezionare il metodo nella mappa e premere **F12**.

 ![Vai alla definizione del codice per un metodo nella mappa del codice](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Aggiungere gli elementi di cui si vuole tenere traccia nella mappa.

 ![Visualizzare i campi di un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Per impostazione predefinita, quando si aggiungono gli elementi alla mappa si aggiungono anche i nodi di gruppo padre, ad esempio la classe, spazio dei nomi e l'assembly. Sebbene ciò sia utile, è possibile mantenere la mappa semplice disattivando questa funzionalità con il pulsante **Includi padri** sulla barra degli strumenti della mappa o premendo **CTRL** quando si aggiungono gli elementi.

 ![Campi correlati a un metodo nella mappa del codice dello stack di chiamate](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Di seguito è possibile visualizzare i metodi in cui vengono usati gli stessi campi. Gli elementi aggiunti più di recente sono indicati in verde.

 Continuare a compilare la mappa per visualizzare altro codice.

 ![Vedere Metodi che usano un campo: mappa del codice dello stack di chiamate](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Metodi che usano un campo nella mappa codici dello stack di chiamate](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Individuare bug usando la mappa
 Visualizzando il codice, sarà possibile rilevare i bug più rapidamente. Ad esempio, si supponga di esaminare un bug in un programma di disegno. Quando si disegna una linea e si tenta di annullare l'operazione, non accadrà nulla finché non si disegnerà un'altra riga.

 Pertanto, impostare punti di interruzione nei metodi `clear`, `undo` e `Repaint`, avviare il debug e compilare una mappa come quella indicata di seguito:

 ![Aggiungere un altro stack di chiamate alla mappa codice](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Tutte le azioni dell'utente nella mappa chiamano `Repaint`, tranne `undo`. Ciò potrebbe spiegare per quale motivo `undo` non funziona nell'immediato.

 Dopo aver corretto il bug e continuato a eseguire il programma, la mappa aggiungerà la nuova chiamata da `undo` in `Repaint`:

 ![Aggiungi nuova chiamata al metodo nello stack di chiamate nella mappa codici](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> Domande e risposte

- **Non tutte le chiamate vengono visualizzate nella mappa. Perché?**

   Per impostazione predefinita, nella mappa viene visualizzato solo il proprio codice. Per visualizzare il codice esterno, attivarlo nella finestra **Stack di chiamate**:

   ![Visualizzare il codice esterno tramite la finestra stack di chiamate](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   oppure disattivare **Abilita Just My Code** nelle opzioni di debug di Visual Studio:

   ![Mostra codice esterno tramite la finestra di dialogo Opzioni](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **La modifica della mappa influisce il codice?**

   La modifica della mappa non influisce in alcun modo sul codice. È possibile rinominare, spostare o rimuovere qualsiasi elemento nella mappa.

- **Cosa significa questo messaggio: "il diagramma può essere basato su una versione precedente del codice"?**

   È possibile che il codice sia stato modificato dopo l'ultimo aggiornamento della mappa. Ad esempio, nel codice potrebbe non essere più disponibile una chiamata alla mappa. Chiudere il messaggio, quindi provare a ricompilare la soluzione prima di aggiornare di nuovo la mappa.

- **Ricerca per categorie controllare il layout della mappa?**

   Aprire il menu **Layout** nella barra degli strumenti della mappa:

  - Modificare il layout predefinito.

  - Per arrestare automaticamente la ridisposizione della mappa, disattivare **Layout automatico durante il debug**.

  - Per ridisporre al minimo la mappa quando si aggiungono elementi, disattivare **Layout incrementale**.

- **È possibile condividere la mappa con altri utenti?**

   È possibile esportare la mappa, inviarla ad altri se è installato Microsoft Outlook o salvarla nella soluzione in modo che sia possibile archiviarla nel controllo della versione di Team Foundation.

   ![Condividi mappa del codice dello stack di chiamate con altri utenti](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **Come si interrompono la mappa di aggiungere automaticamente nuovi stack di chiamate?**

   Scegli ![pulsante &#45; Mostra stack di chiamate nella mappa del codice automaticamente](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") sulla barra degli strumenti della mappa. Per aggiungere manualmente lo stack di chiamate corrente alla mappa, premere **Ctrl** + **MAIUSC** +  **`** .

   La mappa continuerà a evidenziare gli stack di chiamate esistenti sulla mappa durante il debug.

- **Le icone degli elementi e le frecce significato**

   Per ottenere altre informazioni su un elemento, spostare il puntatore del mouse su di esso e vedere la descrizione comando dell'elemento. È anche possibile consultare la **legenda** per conoscere il significato di ciascuna icona.

   ![Cosa significano le icone nella mappa codici dello stack di chiamate?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Vedere: [Eseguire il mapping dello stack di chiamate](#MapStack) • [Aggiungere appunti sul codice](#MakeNotes) • [Aggiornare la mappa con lo stack di chiamate successivo](#UpdateMap) • [Aggiungere il codice correlato alla mappa](#AddRelatedCode) • [Individuare bug utilizzando la mappa](#FindBugs)

## <a name="see-also"></a>Vedere anche
 Eseguire il [mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) [usare le mappe codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md) [trovare problemi potenziali usando gli analizzatori della mappa del codice](../modeling/find-potential-problems-using-code-map-analyzers.md) [esplorare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
