---
title: 'Procedura: Impostare punti di interruzione nei flussi di lavoro (Legacy) | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cec06813890523e604234ccefdbcd7d1de31653
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444178"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Procedura: Impostare punti di interruzione in flussi di lavoro (legacy)
In questo argomento viene descritto come impostare punti di interruzione nelle applicazioni [!INCLUDE[wf](../includes/wf-md.md)] usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando l'applicazione [!INCLUDE[wf2](../includes/wf2-md.md)] deve fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Quando si usa la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy in [!INCLUDE[vs2010](../includes/vs2010-md.md)] per compilare un'applicazione [!INCLUDE[wf2](../includes/wf2-md.md)], è possibile impostare punti di interruzione nei codici C# e Visual Basic come in Visual Studio. Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.  
  
 Un punto di interruzione ha tre stati: *In sospeso*, *associato*, e *errore*. Quando si imposta un punto di interruzione, sarà In sospeso e verrà rappresentato da un icona di colore rosso vuota. Quando il tipo del flusso di lavoro viene caricato dal runtime, diventa Associato e viene rappresentato da un’icona  rossa a tinta unita. Se si specifica un formato non corretto per il punto di interruzione, come avviene quando un nome di attività non è valido, verrà visualizzata una finestra di errore. Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.  
  
 È possibile impostare punti di interruzione su un'attività sull'area di progettazione del flusso di lavoro nelle modalità seguenti:  
  
- L'attività e scegliere **punto di interruzione \ inserire punto di interruzione**.  
  
- Selezionare l’attività e premere F9.  
  
- Selezionare **nuovo punto di interruzione** dalle **Debug** menu.  
  
     È inoltre possibile usare questa opzione per impostare un nuovo punto di interruzione durante l'esecuzione del debug, quando il debugger si arresta in corrispondenza di un punto di interruzione.  
  
    > [!NOTE]
    > L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Per impostare un punto di interruzione usando l'opzione Nuovo punto di interruzione nel menu Debug  
  
1. Nel **Debug** dal menu **nuovo punto di interruzione**.  
  
2. Fare clic su **Interrompi alla funzione**.  
  
     Il **nuovo punto di interruzione** verrà visualizzata la finestra di dialogo.  
  
3. Specificare il nome di un'attività nella **funzione** casella di testo usando questa sintassi: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    > Facoltativamente, anziché usare il nome dell'attività nel **funzione** casella di testo, è possibile impostare un punto di interruzione specificando il percorso assoluto dell'attività flusso di lavoro. Ad esempio, si supponga di avere una soluzione del flusso di lavoro denominata **WorkflowConsoleApplication1** e un flusso di lavoro nella soluzione denominato **Workflow1** che usa un'attività denominata **Delay1**. È possibile usare il nome dell'attività **Delay1** oppure specificare il percorso come **delay1:workflowconsoleapplication1. Workflow1** o **delay1:workflowconsoleapplication1. Workflow1: { 6614886A-608E-412B-BF98-99FF1559DDDF}**.  
  
4. Selezionare il **usare IntelliSense** casella di controllo per verificare il nome della funzione.  
  
     Se questa casella di controllo non è selezionata, non viene eseguita nessuna verifica del nome del punto di interruzione.  
  
5. Selezionare **flusso di lavoro** dalle **Language** elenco.  
  
6. Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei flussi di lavoro Legacy](../workflow-designer/debugging-legacy-workflows.md)   
 [Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)