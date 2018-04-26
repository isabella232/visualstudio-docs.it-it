---
title: 'Creare un ambiente di sviluppo .NET Core con i contenitori usando Kubernetes nel cloud - Passaggio 4: Eseguire il debug di un contenitore in Kubernetes | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: douge
ms.openlocfilehash: 043052dec78251647a3ef12e0b612355b6334692
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introduzione a Connected Environment con .NET Core
 
Passaggio precedente: [Creare un'app Web ASP.NET Core](get-started-netcore-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Selezionare la configurazione di debug VSCE
1. Per aprire la visualizzazione di debug, fare clic sull'icona Debug nella **barra attività** sul lato di Visual Studio Code.
1. Selezionare **.NET Core Launch (VSCE)** (Avvio .NET Core - VSCE) come configurazione di debug attiva.

![](media/debug-configuration.png)

> [!Note]
> Se non vengono visualizzati comandi di Connected Environment nel riquadro comandi, assicurarsi di aver [installato l'estensione di Visual Studio Code per Connected Environment](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="debug-the-container-in-kubernetes"></a>Eseguire il debug del contenitore in Kubernetes
Premere **F5** per eseguire il debug del codice in Kubernetes.

Come con il comando `up`, il codice viene sincronizzato con l'ambiente di sviluppo e un contenitore viene compilato e distribuito in Kubernetes. Questa volta, naturalmente, il debugger è collegato al contenitore remoto.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Impostare un punto di interruzione in un file di codice sul lato server, ad esempio all'interno della funzione `Index()` nel file di origine `Controllers/HomeController.cs`. Aggiornando la pagina del browser si raggiunge il punto di interruzione.

È possibile accedere in modo completo alle informazioni di debug, proprio come se il codice fosse eseguito in locale, ad esempio stack di chiamate, variabili locali, informazioni sulle eccezioni e così via.

## <a name="edit-code-and-refresh"></a>Modificare il codice e aggiornare
Con il debugger attivo, apportare una modifica al codice. Ad esempio, modificare il messaggio della pagina About in `Controllers/HomeController.cs`. 

```csharp
public IActionResult About()
{
    ViewData["Message"] = "My custom message in the About page.";
    return View();
}
```

Salvare il file e nel **riquadro Azioni di debug** fare clic sul pulsante **Aggiorna**. 

![](media/debug-action-refresh.png)

Invece di ricompilare e ridistribuire una nuova immagine del contenitore ogni volta che vengono apportate modifiche al codice, con un considerevole dispendio di tempo, Connected Environment ricompilerà il codice in modo incrementale all'interno del contenitore esistente per rendere possibile un ciclo di modifica/debug più veloce.

Aggiornare l'app Web nel browser e passare alla pagina About. Il messaggio personalizzato verrà visualizzato nell'interfaccia utente.

**Ora si conosce un metodo per eseguire rapidamente iterazioni e debug del codice direttamente in Kubernetes.** Si vedrà poi come è possibile creare e chiamare un secondo contenitore.

> [!div class="nextstepaction"]
> [Chiamare un servizio in esecuzione in un contenitore separato](get-started-netcore-05.md)
