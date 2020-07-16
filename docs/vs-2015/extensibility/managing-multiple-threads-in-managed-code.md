---
title: Gestione di più thread nel codice gestito | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 296ef23bc512a86917920b3c3d5fbb5ec203a21e
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387018"
---
# <a name="managing-multiple-threads-in-managed-code"></a>Gestione di più thread nel codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si dispone di un'estensione VSPackage gestita che chiama metodi asincroni o con operazioni eseguite su thread diversi dal thread dell'interfaccia utente di Visual Studio, è necessario attenersi alle linee guida indicate di seguito. È possibile far rispondere il thread dell'interfaccia utente perché non è necessario attendere il completamento del lavoro in un altro thread. È possibile rendere il codice più efficiente, perché non sono presenti thread aggiuntivi che occupano lo spazio dello stack ed è possibile renderlo più affidabile e più semplice da eseguire il debug perché si evitano deadlock e non rispondono.  
  
 In generale, è possibile passare dal thread dell'interfaccia utente a un thread diverso o viceversa. Quando il metodo viene restituito, il thread corrente è il thread dal quale è stato originariamente chiamato.  
  
> [!IMPORTANT]
> Le linee guida seguenti usano le API nello <xref:Microsoft.VisualStudio.Threading> spazio dei nomi, in particolare la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> classe. Le API in questo spazio dei nomi sono nuove in [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] . È possibile ottenere un'istanza di un oggetto <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> dalla <xref:Microsoft.VisualStudio.Shell.ThreadHelper> proprietà `ThreadHelper.JoinableTaskFactory` .  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Passare dal thread dell'interfaccia utente a un thread in background  
  
1. Se si usa il thread dell'interfaccia utente e si vuole eseguire operazioni asincrone in un thread in background, usare Task. Run ():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2. Se si usa il thread dell'interfaccia utente e si vuole bloccare in modo sincrono mentre si esegue il lavoro in un thread in background, usare la <xref:System.Threading.Tasks.TaskScheduler> proprietà `TaskScheduler.Default` all'interno di <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Passare da un thread in background al thread dell'interfaccia utente  
  
1. Se ci si trova in un thread in background e si vuole eseguire un'operazione nel thread dell'interfaccia utente, usare <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     È possibile utilizzare il <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> metodo per passare al thread dell'interfaccia utente. Questo metodo invia un messaggio al thread dell'interfaccia utente con la continuazione del metodo asincrono corrente e comunica anche con il resto del Framework di threading per impostare la priorità corretta ed evitare i deadlock.  
  
     Se il metodo del thread in background non è asincrono e non è possibile renderlo asincrono, è comunque possibile usare la `await` sintassi per passare al thread dell'interfaccia utente eseguendo il wrapping del lavoro con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , come in questo esempio:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
