---
title: 'Procedura: Gestire più thread nel codice gestito | Microsoft Docs'
description: Informazioni su come gestire più thread nel codice se l'estensione VSPackage gestita chiama metodi asincroni o dispone di operazioni Visual Studio thread dell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39319b748dd41c6936e7b70e20243202452fae67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903086"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Procedura: Gestire più thread nel codice gestito
Se si dispone di un'estensione VSPackage gestita che chiama metodi asincroni o dispone di operazioni che vengono eseguite su thread diversi dal thread dell'interfaccia utente di Visual Studio, è necessario seguire le linee guida riportate di seguito. È possibile mantenere reattivo il thread dell'interfaccia utente perché non è necessario attendere il completamento del lavoro in un altro thread. È possibile rendere il codice più efficiente, perché non sono disponibili thread aggiuntivi che prendono spazio nello stack ed è possibile renderlo più affidabile e più facile da sottoporsi a debug perché si evitano deadlock e codice che non risponde.

 In generale, è possibile passare dal thread dell'interfaccia utente a un thread diverso o viceversa. Quando il metodo viene restituito, il thread corrente è il thread da cui è stato chiamato in origine.

> [!IMPORTANT]
> Le linee guida seguenti usano le API nello spazio dei <xref:Microsoft.VisualStudio.Threading> nomi , in particolare la classe <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Le API in questo spazio dei nomi sono nuove in [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . È possibile ottenere un'istanza di <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> dalla <xref:Microsoft.VisualStudio.Shell.ThreadHelper> proprietà `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Passare dal thread dell'interfaccia utente a un thread in background

1. Se si usa il thread dell'interfaccia utente e si vuole eseguire operazioni asincrone su un thread in background, usare `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Se si usa il thread dell'interfaccia utente e si vuole bloccare in modo sincrono mentre si esegue il lavoro su un thread in background, usare <xref:System.Threading.Tasks.TaskScheduler> la proprietà `TaskScheduler.Default` all'interno di <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

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

1. Se si usa un thread in background e si vuole eseguire un'operazione nel thread dell'interfaccia utente, usare <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     È possibile usare il metodo <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> per passare al thread dell'interfaccia utente. Questo metodo invia un messaggio al thread dell'interfaccia utente con la continuazione del metodo asincrono corrente e comunica anche con il resto del framework di threading per impostare la priorità corretta ed evitare deadlock.

     Se il metodo del thread in background non è asincrono e non è possibile renderlo asincrono, è comunque possibile usare la sintassi per passare al thread dell'interfaccia utente tramite il wrapping del lavoro con , come `await` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> in questo esempio:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
