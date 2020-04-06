---
title: 'Procedura: Gestione di più thread nel codice gestito Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702775"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Procedura: gestire più thread nel codice gestitoHow to: Manage multiple threads in managed code
Se si dispone di un'estensione VSPackage gestita che chiama metodi asincroni o dispone di operazioni che vengono eseguite su thread diversi dal thread dell'interfaccia utente di Visual Studio, è necessario seguire le linee guida fornite di seguito. È possibile mantenere il thread dell'interfaccia utente reattivo perché non è necessario attendere il completamento del lavoro su un altro thread. È possibile rendere il codice più efficiente, perché non si dispone di thread aggiuntivi che occupano spazio dello stack e si può rendere più affidabile e più facile eseguire il debug perché si evitano deadlock e blocchi.

 In generale, è possibile passare dal thread dell'interfaccia utente a un thread diverso o viceversa. Quando il metodo termina, il thread corrente è il thread da cui è stato originariamente chiamato.

> [!IMPORTANT]
> Le linee guida seguenti usano <xref:Microsoft.VisualStudio.Threading> le API nello <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> spazio dei nomi, in particolare la classe. Le API in questo spazio [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]dei nomi sono nuove in . È possibile ottenere un'istanza <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory`di un <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> oggetto dalla proprietà .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Passare dal thread dell'interfaccia utente a un thread in background

1. Se si utilizza il thread dell'interfaccia utente e si `Task.Run()`desidera eseguire operazioni asincrone su un thread in background, usare:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Se ci si trova nel thread dell'interfaccia utente e si desidera bloccare <xref:System.Threading.Tasks.TaskScheduler> `TaskScheduler.Default` in <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>modo sincrono mentre si esegue il lavoro su un thread in background, utilizzare la proprietà all'interno di :

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Passare da un thread in background al thread dell'interfaccia utente

1. Se si utilizza un thread in background e si desidera <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>eseguire un'operazione nel thread dell'interfaccia utente, usare:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     È possibile <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> utilizzare il metodo per passare al thread dell'interfaccia utente. Questo metodo invia un messaggio al thread dell'interfaccia utente con la continuazione del metodo asincrono corrente e comunica anche con il resto del framework di threading per impostare la priorità corretta ed evitare deadlock.

     Se il metodo del thread in background non è asincrono e `await` non è possibile renderlo asincrono, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>è comunque possibile utilizzare la sintassi per passare al thread dell'interfaccia utente eseguendo il wrapping del lavoro con , come in questo esempio:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
