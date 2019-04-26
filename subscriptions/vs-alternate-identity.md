---
title: Identità per i sottoscrittori di Visual Studio
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Come aggiungere un'identità alternativa per la sottoscrizione di Visual Studio per usare Azure DevOps e Azure
searchscope: vs subscription
ms.openlocfilehash: 63a372d4a0e0e70a008f86a36aae73516bf42458
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428103"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identità per i sottoscrittori di Visual Studio

Quando si attiva la sottoscrizione di Visual Studio, l'identità (o l'account di accesso) usata durante l'attivazione viene collegata alla sottoscrizione di Visual Studio. In questo modo, l'utente verrà riconosciuto nel [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), in Azure DevOps e in Azure.

In Azure DevOps lo stato della sottoscrizione di Visual Studio viene controllato a ogni accesso e vengono concesse automaticamente le funzionalità incluse per ogni organizzazione di cui si è membri.
Poiché queste funzionalità sono incluse come vantaggio per i sottoscrittori, un utente può essere aggiunto gratuitamente come membro di qualsiasi organizzazione di Azure DevOps quando viene usata un'identità collegata alla sottoscrizione di Visual Studio.

In Azure, lo stato della sottoscrizione di Visual Studio viene controllato quando si attiva il [credito di Azure mensile](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) che è un vantaggio dei sottoscrittori.

All'interno del [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) potrebbe essere possibile aggiungere un'**identità alternativa** oltre a quella usata durante l'attivazione. Attualmente l'aggiunta di un'identità alternativa è consentita se è stato usato un account Microsoft per attivare la sottoscrizione. In questo modo è possibile aggiungere anche un account aziendale o dell'istituto di istruzione (usato per l'accesso a Visual Studio, Office 365 o alla rete aziendale o dell'istituto di istruzione), in modo che sia possibile accedere ad Azure DevOps sia tramite l'account personale che tramite l'account aziendale o dell'istituto di istruzione.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Aggiungere un account alternativo alla sottoscrizione di Visual Studio

L'aggiunta di un account alternativo alla sottoscrizione di Visual Studio consente di accedere ai vantaggi della sottoscrizione, tra cui Azure DevOps e Azure, con un'identità diversa rispetto a quella a cui è assegnata la sottoscrizione. In precedenza, questa funzionalità era disponibile solo se la sottoscrizione di Visual Studio (VS) era assegnata a un account Microsoft. Questa funzionalità è stata estesa agli account aziendali o di istituti di istruzione in Azure Active Directory (Azure AD).

Questa funzionalità non fornisce una copia della sottoscrizione all'altro account, ma consente solo di accedere ai due vantaggi con l'account alternativo.

Per tutte le sottoscrizioni, è possibile aggiungere un "account aziendale o dell'istituto di istruzione", in modo da poter usare l'account con i vantaggi che richiedono l'accesso (IDE di Visual Studio, Azure DevOps e Azure).

### <a name="add-the-alternate-account"></a>Aggiungere l'account alternativo

1. Accedere al portale per i sottoscrittori di Visual Studio con il proprio account Microsoft (https://my.visualstudio.com).

2. Passare a **Sottoscrizioni**.

    > [!div class="mx-imgBorder"]
    > ![Aggiungere l'account alternativo. Passare alle sottoscrizioni nel portale di Visual Studio](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Scegliere **Aggiungi un account alternativo**.
    > [!div class="mx-imgBorder"]
    > ![Scegliere Aggiungi un account alternativo](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Aggiungere l'account aziendale o dell'istituto di istruzione.
    > [!div class="mx-imgBorder"]
    > ![Aggiungere l'account aziendale o dell'istituto di istruzione](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Usare l'account aziendale o dell'istituto di istruzione per accedere ad Azure DevOps (https://{account}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![Usare l'account aziendale o dell'istituto di istruzione](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

L'account alternativo viene aggiunto alla sottoscrizione di Visual Studio, consentendo a entrambe le identità di sfruttare i vantaggi della sottoscrizione che richiedono l'accesso con l'account alternativo (IDE, Azure DevOps e Azure).

## <a name="faq"></a>Domande frequenti

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>D:  Perché Azure DevOps non riconosce l'utente come sottoscrittore di Visual Studio?

R: Azure DevOps dovrebbe riconoscere automaticamente la sottoscrizione dell'utente quando questi esegue l'accesso con l'identità primaria o alternativa. In caso contrario, è possibile:

* Controllare di avere una sottoscrizione di Visual Studio attiva che [include Azure DevOps come vantaggio](vs-azure-devops.md).

* Assicurarsi di usare un account di accesso o un'identità che rappresenta l'identità primaria o alternativa per la sottoscrizione di Visual Studio.

* Visitare il [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) almeno una volta prima di accedere ad Azure DevOps.

Se Azure DevOps non riconosce ancora la sottoscrizione, [contattare il supporto tecnico](https://visualstudio.microsoft.com/team-services/support/)
