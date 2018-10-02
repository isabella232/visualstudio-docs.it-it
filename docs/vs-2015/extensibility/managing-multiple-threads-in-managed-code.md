---
title: Gestione di più thread in codice gestito | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7be5763081da023742f53c3b2d22e0d0f4aad167
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520010"
---
# <a name="managing-multiple-threads-in-managed-code"></a>Gestione di più thread nel codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: gestione di più thread in codice gestito](https://docs.microsoft.com/visualstudio/extensibility/managing-multiple-threads-in-managed-code).  
  
Se si dispone di un'estensione VSPackage gestita che chiama i metodi asincroni che abbia le operazioni eseguite su thread diversi dal thread dell'interfaccia utente di Visual Studio, è necessario seguire le linee guida indicate di seguito. È possibile mantenere reattivo il thread dell'interfaccia utente perché non è necessario attendere per il lavoro in un altro thread per il completamento. È possibile rendere il codice più efficiente, perché non si dispone di un thread aggiuntivo che occupano lo spazio dello stack e si può rendere più affidabili e facili da eseguire il debug perché è evitare blocchi e deadlock.  
  
 In generale, è possibile passare dal thread dell'interfaccia utente a un altro thread, o viceversa. Quando il metodo termina, il thread corrente è il thread da cui è stato originariamente denominato.  
  
> [!IMPORTANT]
>  Le linee guida seguenti usano le API nel <xref:Microsoft.VisualStudio.Threading> spazio dei nomi, in particolare, il <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> classe. Le API in questo spazio dei nomi sono una novità [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. È possibile ottenere un'istanza di un <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> dal <xref:Microsoft.VisualStudio.Shell.ThreadHelper> proprietà `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Il passaggio da Thread dell'interfaccia utente a un Thread in Background  
  
1.  Se si è sul thread UI e si desidera eseguire le attività asincrone in un thread in background, usare Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  Se si è sul thread UI e si vuole bloccare in modo sincrono durante le operazioni di lavoro in un thread in background, usare il <xref:System.Threading.Tasks.TaskScheduler> proprietà `TaskScheduler.Default` all'interno di <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Il passaggio da un Thread in Background nel thread dell'interfaccia utente  
  
1.  Se si usa un thread in background e si desidera eseguire un'operazione sul thread dell'interfaccia utente, usare <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     È possibile usare il <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> metodo da passare al thread dell'interfaccia utente. Questo metodo invia un messaggio al thread UI con la continuazione del metodo asincrono corrente e comunica anche con il resto del framework threading per impostare la priorità corretta ed evitare i deadlock.  
  
     Se il metodo di thread in background non è asincrono e non riesci ad asincrona, è comunque possibile usare la `await` sintassi per passare al thread dell'interfaccia utente eseguendo il wrapping il lavoro con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, come in questo esempio:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```

