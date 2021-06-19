---
title: Accedere a Windows
description: Informazioni su come accedere a Visual Studio.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b0ed679188cc0a4df9329fdd0adff4ad69667e6
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375760"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Accedere a Visual Studio in Windows

Anche se non è necessario eseguire l'accesso, esistono molti vantaggi a tale scopo. Quando si accede, è possibile personalizzare, ottimizzare e arricchire l'esperienza Visual Studio personalizzata. 

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Accesso a Visual Studio per Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> Per usare le risorse configurate per l'accesso condizionale, eseguire l'aggiornamento a Visual Studio 2019 Update 16.6 o versione successiva. Per altre informazioni, vedere [Come usare i Visual Studio con account che richiedono l'autenticazione a più fattori.](work-with-multi-factor-authentication.md)
> L'Visual Studio 2017 per accedere alle risorse configurate per l'accesso condizionale può attivare un'esperienza di autenticazione degradata, richiedendo più volte la riautenticazione all'interno della stessa Visual Studio sessione. 
> 
::: moniker-end

## <a name="benefits"></a>Vantaggi

Di seguito è riportato un elenco completo dei vantaggi di cui usufruire e delle operazioni che si possono eseguire dopo aver effettuato l'accesso:


#### <a name="extend-the-visual-studio-trial-period"></a>Estendere il periodo Visual Studio di valutazione

È possibile usare Visual Studio Professional o Visual Studio Enterprise per altri 90 giorni, anziché limitarsi al periodo di valutazione di 30 giorni. Per altre informazioni, vedere [Estendere una versione di valutazione o aggiornare una licenza.](../ide/how-to-unlock-visual-studio.md)

#### <a name="synchronize-your-visual-studio-settings"></a>Sincronizzare le Visual Studio predefinite

Le impostazioni personalizzate, ad esempio le associazioni di tasti, il layout della finestra e il tema a colori, vengono applicate immediatamente quando si accede a Visual Studio in qualsiasi dispositivo. Vedere [Sincronizzare le impostazioni in Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

#### <a name="use-visual-studio-community-edition"></a>Usare Visual Studio Community edizione

Se l'installazione dell'edizione Community richiede una licenza, accedere all'IDE per continuare a usare Visual Studio Community **gratuitamente.** 

#### <a name="unlock-visual-studio-visual-studio-subscription-or-an-azure-devops-organization"></a>Sbloccare Visual Studio (Visual Studio o un'organizzazione Azure DevOps locale)

Sbloccare Visual Studio se si usa un account associato a una sottoscrizione di Visual Studio o a un'organizzazione Azure DevOps usando la procedura descritta in Estendere una versione di valutazione o aggiornare [una licenza](../ide/how-to-unlock-visual-studio.md).

#### <a name="the-visual-studio-dev-essentials-program"></a>Programma Visual Studio Dev Essentials

Questo programma include offerte di software gratuito, training, supporto e altro ancora. Per altre informazioni, vedere [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) .

#### <a name="automatically-connect-to-services"></a>Connettersi automaticamente ai servizi

Connettersi ai servizi, ad esempio Azure e Azure DevOps Services, nell'IDE senza richiedere nuovamente le credenziali per lo stesso account.

## <a name="how-to-sign-in"></a>Come effettuare l'accesso 

Quando si apre Visual Studio per la prima volta, viene chiesto di accedere e fornire alcune informazioni di registrazione di base.

![Richiesta di accesso](../ide/media/vs2019_signinpopup.png)

1. Scegliere un account Microsoft o un account aziendale o dell'istituto di istruzione che meglio rappresenta l'utente. Se non si ha uno di questi account, è possibile creare un account Microsoft gratuitamente facendo clic sul collegamento sotto il pulsante di accesso. In caso di problemi, vedere Ricerca per categorie [iscriversi per un account Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Scegliere le impostazioni dell'interfaccia utente e il tema del colore che si vuole usare in Visual Studio. Visual Studio memorizza queste impostazioni e le sincronizza tra tutti gli ambienti Visual Studio a cui si è eseguito l'accesso. Per un elenco delle impostazioni sincronizzate, vedere [Impostazioni sincronizzate](../ide/synchronized-settings-in-visual-studio.md). È possibile modificare le impostazioni in un secondo momento se si apre **il**  >  menu **Opzioni** strumenti in Visual Studio.
   Dopo aver fornito le impostazioni, viene avviato Visual Studio e viene eseguito l'accesso dell'utente in modo da poter subito iniziare a usare l'applicazione. 
   
1. Per verificare se è stato eseguito l'accesso, cercare il nome nell'angolo superiore destro dell'ambiente Visual Studio.

![Utente attualmente connesso in VS2019](../ide/media/vs2019_username.png)

Se si sceglie di non accedere alla prima Visual Studio, sarà facile farlo in un secondo momento. Cercare il **collegamento Accedi** nell'angolo superiore destro dell'Visual Studio locale.

![Utente non connesso](../ide/media/vs2019_usernotsignedin.png)

A meno che non esegua la disconnessione, l'utente viene automaticamente connesso a Visual Studio a ogni avvio e tutte le modifiche apportate alle impostazioni sincronizzate vengono applicate automaticamente. Per disconnettersi, fare clic sull'icona con il nome del profilo nell'angolo superiore destro dell'ambiente Visual Studio, scegliere il **comando Impostazioni** account e quindi scegliere il **collegamento Disconnetto.** Per accedere di nuovo, scegliere il comando **Accedi** nell'angolo superiore destro dell'ambiente Visual Studio.

## <a name="update-your-profile"></a>Aggiornare il profilo

1. Passare a **Impostazioni**  >  **account file e** scegliere il collegamento Gestisci Visual Studio **profilo.**

1. Nella finestra del browser scegliere **Modifica profilo** e modificare le impostazioni desiderate.

1. Al termine, scegliere il pulsante **Salva modifiche**.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Vedere la [pagina Supporto della](https://visualstudio.microsoft.com/subscriptions/support/) sottoscrizione per ottenere assistenza.

## <a name="see-also"></a>Vedi anche

* [Estendere una versione di valutazione o aggiornare una licenza](../ide/how-to-unlock-visual-studio.md)
* [Utilizzare gli account GitHub in Visual Studio](../ide/work-with-github-accounts.md)
* [Panoramica dell'ambiente IDE di Visual Studio](../get-started/visual-studio-ide.md)
