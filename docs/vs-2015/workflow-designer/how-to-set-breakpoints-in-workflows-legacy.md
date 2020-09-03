---
title: 'Procedura: impostare punti di interruzione nei flussi di lavoro (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 182f28a2b21ae3129ce0d34fae97280ba0a07218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603600"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Procedura: impostare punti di interruzione nei flussi di lavoro (legacy)
In questo argomento viene descritto come impostare punti di interruzione nelle applicazioni [!INCLUDE[wf](../includes/wf-md.md)] usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando l'applicazione [!INCLUDE[wf2](../includes/wf2-md.md)] deve fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Quando si usa la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy in [!INCLUDE[vs2010](../includes/vs2010-md.md)] per compilare un'applicazione [!INCLUDE[wf2](../includes/wf2-md.md)], è possibile impostare punti di interruzione nei codici C# e Visual Basic come in Visual Studio. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.

 Un punto di interruzione ha tre stati: *Pending*, *Bound*ed *Error*. Quando si imposta un punto di interruzione, sarà In sospeso e verrà rappresentato da un icona di colore rosso vuota. Quando il tipo del flusso di lavoro viene caricato dal runtime, diventa Associato e viene rappresentato da un’icona  rossa a tinta unita. Se si specifica un formato non corretto per il punto di interruzione, come avviene quando un nome di attività non è valido, verrà visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.

 È possibile impostare punti di interruzione su un'attività sull'area di progettazione del flusso di lavoro nelle modalità seguenti:

- Fare clic con il pulsante destro del mouse sull'attività e selezionare **breakpoint \ Inserisci**punto di interruzione.

- Selezionare l’attività e premere F9.

- Scegliere **nuovo** punto di interruzione dal menu **debug** .

     È inoltre possibile usare questa opzione per impostare un nuovo punto di interruzione durante l'esecuzione del debug, quando il debugger si arresta in corrispondenza di un punto di interruzione.

    > [!NOTE]
    > L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Per impostare un punto di interruzione usando l'opzione Nuovo punto di interruzione nel menu Debug

1. Scegliere nuovo punto di **interruzione**dal menu **debug** .

2. Fare clic su **Interrompi alla funzione**.

     Verrà visualizzata la finestra di dialogo nuovo punto di **interruzione** .

3. Specificare il nome di un'attività nella casella di testo della **funzione** utilizzando la sintassi seguente: `QualifiedActivityId[:[FullClassName][:InstanceId]]` .

    > [!NOTE]
    > Facoltativamente, anziché utilizzare il nome dell'attività nella casella di testo della **funzione** , è possibile impostare un punto di interruzione specificando il percorso assoluto dell'attività del flusso di lavoro. Si supponga, ad esempio, di disporre di una soluzione flusso di lavoro denominata **WorkflowConsoleApplication1** e di un flusso di lavoro nella soluzione denominata **Workflow1** che usa un'attività denominata **Delay1**. È possibile usare il nome dell'attività **Delay1** o specificare il percorso come **Delay1: WorkflowConsoleApplication1. Workflow1** o **Delay1: WorkflowConsoleApplication1. Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}**.

4. Selezionare la casella di controllo **Usa IntelliSense** per verificare il nome della funzione.

     Se questa casella di controllo non è selezionata, non viene eseguita nessuna verifica del nome del punto di interruzione.

5. Selezionare **flusso di lavoro** nell'elenco **lingua** .

6. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 [Debug di flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md) [richiamando il debugger di Visual Studio per Windows Workflow Foundation (legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)