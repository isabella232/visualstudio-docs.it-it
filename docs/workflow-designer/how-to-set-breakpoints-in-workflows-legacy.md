---
title: 'Finestra di progettazione del flusso di lavoro - procedura: impostare punti di interruzione nei flussi di lavoro (Legacy)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0c70b630404830fa8c733a7310e4700da8f08b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975195"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Procedura: impostare punti di interruzione nei flussi di lavoro (legacy)

In questo argomento viene descritto come impostare punti di interruzione in Windows Workflow Foundation (WF) le applicazioni compilate utilizzando Progettazione flussi di lavoro Windows legacy. Utilizzare la finestra di progettazione del flusso di lavoro legacy quando l'applicazione di Windows Workflow Foundation deve avere come destinazione .NET Framework versione 3.5 o la WinFX.

 Quando si utilizza la finestra di progettazione del flusso di lavoro legacy in Visual Studio 2010 per compilare un'applicazione Windows Workflow Foundation, è possibile impostare i punti di interruzione nel codice c# e Visual Basic come in Visual Studio. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.

 Un punto di interruzione ha tre stati: *in sospeso*, *associato*, e *errore*. Quando si imposta un punto di interruzione, sarà In sospeso e verrà rappresentato da un icona di colore rosso vuota. Quando il tipo del flusso di lavoro viene caricato dal runtime, diventa Associato e viene rappresentato da un’icona  rossa a tinta unita. Se si specifica un formato non corretto per il punto di interruzione, come avviene quando un nome di attività non è valido, verrà visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.

 È possibile impostare punti di interruzione su un'attività sull'area di progettazione del flusso di lavoro nelle modalità seguenti:

-   L'attività di mouse e scegliere **punto di interruzione \ inserire punto di interruzione**.

-   Selezionare l’attività e premere F9.

-   Selezionare **nuovo punto di interruzione** dal **Debug** menu.

     È inoltre possibile usare questa opzione per impostare un nuovo punto di interruzione durante l'esecuzione del debug, quando il debugger si arresta in corrispondenza di un punto di interruzione.

    > [!NOTE]
    > L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Per impostare un punto di interruzione usando l'opzione Nuovo punto di interruzione nel menu Debug

1.  Nel **Debug** dal menu **nuovo punto di interruzione**.

2.  Fare clic su **Interrompi alla funzione**.

     Il **nuovo punto di interruzione** verrà visualizzata la finestra di dialogo.

3.  Specificare il nome di un'attività nel **funzione** casella di testo utilizzando questa sintassi: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.

    > [!NOTE]
    > Facoltativamente, anziché usare il nome dell'attività nel **funzione** casella di testo, è possibile impostare un punto di interruzione specificando il percorso assoluto dell'attività flusso di lavoro. Ad esempio, si supponga che si dispone di una soluzione del flusso di lavoro denominata **WorkflowConsoleApplication1** e un flusso di lavoro nella soluzione denominato **Workflow1** che utilizza un'attività denominata **Delay1**. È possibile utilizzare il nome dell'attività **Delay1** o specificare il percorso come **Delay1:WorkflowConsoleApplication1.Workflow1** o **Delay1:WorkflowConsoleApplication1.Workflow1: { 6614886A-608E-412B-BF98-99FF1559DDDF}**.

4.  Selezionare il **Usa IntelliSense** casella di controllo per verificare il nome della funzione.

     Se questa casella di controllo non è selezionata, non viene eseguita nessuna verifica del nome del punto di interruzione.

5.  Selezionare **flusso di lavoro** dal **Language** elenco.

6.  Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)
- [Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)