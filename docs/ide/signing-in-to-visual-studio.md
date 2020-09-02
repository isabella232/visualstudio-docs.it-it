---
title: Accedi a Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 07/24/2020
ms.topic: conceptual
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d6bf69050348cbe078cfdf7ae2d419f1dd13745
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235199"
---
# <a name="sign-in-to-visual-studio"></a>Accedi a Visual Studio

È possibile personalizzare e ottimizzare l'esperienza di sviluppo in Visual Studio effettuando l'accesso all'account di personalizzazione.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Accesso a Visual Studio per Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [! AVVISO: se si usa Visual Studio 2017 per accedere alle risorse configurate per l'accesso condizionale, è possibile che venga generata un'esperienza di autenticazione ridotta, richiedendo la riautenticazione più volte all'interno della stessa sessione di Visual Studio. 
> Per usare le risorse configurate per l'accesso condizionale, eseguire l'aggiornamento a Visual Studio 2019 Update 16,6 o versione successiva. Per altre informazioni, vedere [come usare Visual Studio con gli account che richiedono l'autenticazione a più fattori](work-with-multi-factor-authentication.md).

::: moniker-end

## <a name="why-should-i-sign-in-to-visual-studio"></a>Perché accedere a Visual Studio?

Quando si accede si migliorano le proprie esperienze di Visual Studio. Ad esempio, dopo aver eseguito l'accesso, è possibile [sincronizzare le impostazioni tra i](synchronized-settings-in-visual-studio.md) dispositivi, estendere una versione di valutazione e connettersi automaticamente a un servizio di Azure, per citarne alcuni.

Di seguito è riportato un elenco completo dei vantaggi di cui usufruire e delle operazioni che si possono eseguire dopo aver effettuato l'accesso:
- **Estendere il periodo di valutazione per Visual Studio**: è possibile usare Visual Studio Professional o Visual Studio Enterprise per 90 giorni, anziché essere vincolati al periodo di valutazione di 30 giorni. Per altre informazioni, vedere [estendere una versione di valutazione o aggiornare una licenza](../ide/how-to-unlock-visual-studio.md).

- **Continuare a usare Visual Studio Community Edition** : se l'installazione dell'edizione community richiede una licenza, accedere all'IDE per continuare a usare **gratuitamente**Visual Studio community. 

- **Sbloccare Visual Studio se si utilizza un account associato a una sottoscrizione di Visual Studio o a un'organizzazione di Azure DevOps**. Per istruzioni dettagliate, vedere [estendere una versione di valutazione o aggiornare una licenza](../ide/how-to-unlock-visual-studio.md).

- **Accedere al programma Visual Studio Dev Essentials**: il programma comprende un software gratuito, formazione, supporto e altro ancora. Per altre informazioni, vedere [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) .

- **Sincronizzare le impostazioni di Visual Studio**: le impostazioni personalizzate, ad esempio le combinazioni di tasti, il layout della finestra e il tema colori, vengono applicate immediatamente quando si accede a Visual Studio da qualsiasi dispositivo. Vedere [sincronizzare le impostazioni in Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

- **Collegarsi automaticamente a servizi come Azure e Azure DevOps Services** nell'IDE senza richiedere di nuovo le credenziali per lo stesso account.

## <a name="how-to-sign-in-to-visual-studio"></a>Come accedere a Visual Studio

Quando si apre Visual Studio per la prima volta, viene richiesto di accedere e fornire alcune informazioni di registrazione di base. 

![Richiesta di accesso](../ide/media/vs2019_signinpopup.png)

Si deve scegliere un account Microsoft o un account aziendale o dell'istituto di istruzione che è più rappresentativo. Se non si dispone di questi account, è possibile creare una account Microsoft gratuitamente facendo clic sul collegamento sotto il pulsante Accedi. In caso di problemi, vedere [ricerca per categorie iscriversi per ottenere un account Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

Selezionare quindi le impostazioni dell'interfaccia utente e il tema colori che si desidera usare in Visual Studio. Visual Studio memorizza queste impostazioni e le sincronizza tra tutti gli ambienti Visual Studio a cui si è eseguito l'accesso. Per un elenco delle impostazioni sincronizzate, vedere [Impostazioni sincronizzate](../ide/synchronized-settings-in-visual-studio.md). È possibile modificare le impostazioni in un secondo momento se si apre il menu **strumenti**  >  **Opzioni** in Visual Studio.

Dopo aver fornito le impostazioni, viene avviato Visual Studio e viene eseguito l'accesso dell'utente in modo da poter subito iniziare a usare l'applicazione. Per verificare se è stato eseguito l'accesso, cercare il nome nell'angolo superiore destro dell'ambiente Visual Studio.

![Utente attualmente connesso in VS2019](../ide/media/vs2019_username.png)

Se si sceglie di non accedere alla prima apertura di Visual Studio, è facile eseguire questa operazione in un secondo momento. Cercare il collegamento **Accedi** nell'angolo superiore destro dell'ambiente Visual Studio. 

![Utente non connesso](../ide/media/vs2019_usernotsignedin.png)

A meno che non esegua la disconnessione, l'utente viene automaticamente connesso a Visual Studio a ogni avvio e tutte le modifiche apportate alle impostazioni sincronizzate vengono applicate automaticamente. Per disconnettersi, fare clic sull'icona con il nome del profilo nell'angolo superiore destro dell'ambiente Visual Studio, scegliere il comando **Impostazioni account** , quindi scegliere il collegamento per la **disconnessione** . Per accedere di nuovo, scegliere il comando **Accedi** nell'angolo superiore destro dell'ambiente Visual Studio.

## <a name="to-change-your-profile-information"></a>Per modificare le informazioni sul profilo

1. Passare a **file**  >  **Impostazioni account** e scegliere il collegamento **Gestisci profilo di Visual Studio** .

1. Nella finestra del browser scegliere **Modifica profilo** e modificare le impostazioni desiderate.

1. Al termine, scegliere il pulsante **Salva modifiche**.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verificano problemi durante l'accesso, vedere la pagina relativa al supporto per le [sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/) per ottenere assistenza.

## <a name="see-also"></a>Vedere anche

* [Estendere una versione di valutazione o aggiornare una licenza](../ide/how-to-unlock-visual-studio.md)
* [Panoramica dell'ambiente IDE di Visual Studio](../get-started/visual-studio-ide.md)
* [Accesso (Visual Studio per Mac)](/visualstudio/mac/signing-in)
* [Attivazione (Visual Studio per Mac)](/visualstudio/mac/activation)
