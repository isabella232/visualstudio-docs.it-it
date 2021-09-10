---
title: Identità per i sottoscrittori di Visual Studio
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 02/19/2021
ms.topic: conceptual
description: Come aggiungere un'identità alternativa per la sottoscrizione di Visual Studio per usare Azure DevOps e Azure
ms.openlocfilehash: 4d00e6808a71522f95d8580056556f5a502ecbde
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123965535"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identità per i sottoscrittori di Visual Studio
Quando si attiva la sottoscrizione di Visual Studio, l'identità (o l'account di accesso) usata durante l'attivazione viene collegata alla sottoscrizione di Visual Studio. In questo modo, l'utente verrà riconosciuto nel [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), in Azure DevOps e in Azure.

In Azure DevOps lo stato della sottoscrizione di Visual Studio viene controllato a ogni accesso e vengono concesse automaticamente le funzionalità incluse per ogni organizzazione di cui si è membri.
Poiché queste funzionalità sono incluse come vantaggio per i sottoscrittori, un utente può essere aggiunto gratuitamente come membro di qualsiasi organizzazione di Azure DevOps quando viene usata un'identità collegata alla sottoscrizione di Visual Studio.

In Azure, lo stato della sottoscrizione Visual Studio quando si attiva il credito individuale [Azure DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) mensile che rappresenta un vantaggio sottoscrittore.

All'interno del [portale per i sottoscrittori di Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) potrebbe essere possibile aggiungere un'**identità alternativa** oltre a quella usata durante l'attivazione. L'aggiunta di un'identità alternativa è consentita se è stato usato un account Microsoft per attivare la sottoscrizione. In questo modo è anche possibile aggiungere un account aziendale o dell'istituto di istruzione (che si usa quando si accede a Visual Studio, Microsoft 365 o alla rete aziendale o dell'istituto di istruzione), consentendo di accedere a Azure DevOps usando sia l'account personale che l'account aziendale o dell'istituto di istruzione.

## <a name="add-an-alternate-account-to-your-subscription"></a>Aggiungere un account alternativo alla sottoscrizione
L'aggiunta di un account alternativo alla sottoscrizione Visual Studio consente di accedere a determinati vantaggi della sottoscrizione, ad esempio Azure DevOps e Azure, o di accedere all'IDE di Visual Studio con un'identità diversa da quella a cui è assegnata la sottoscrizione. In precedenza, questa funzionalità era disponibile solo se la sottoscrizione di Visual Studio (VS) era assegnata a un account Microsoft. Questa funzionalità è stata estesa agli account aziendali o di istituti di istruzione in Azure Active Directory (Azure AD).

> [!NOTE]
> Un ID alternativo consente solo di usare il secondo ID per attivare crediti e Azure DevOps Azure e per accedere all'IDE Visual Studio.  Non può essere usato per accedere al portale delle sottoscrizioni all'indirizzo <https://my.visualstudio.com> .  È comunque necessario usare l'ID a cui è assegnata la sottoscrizione per accedere al portale. 

Per tutte le sottoscrizioni, è possibile aggiungere un "account aziendale o dell'istituto di istruzione", in modo da poter usare l'account con i vantaggi che richiedono l'accesso (IDE di Visual Studio, Azure DevOps e Azure).

### <a name="add-the-alternate-account"></a>Aggiungere l'account alternativo
1. Accedere al portale per i sottoscrittori di Visual Studio con il proprio account Microsoft (https://my.visualstudio.com).
2. Selezionare la scheda **Sottoscrizioni** .
3. Scegliere **Aggiungi account alternativo**.
4. Aggiungere l'account aziendale o dell'istituto di istruzione.
    > [!div class="mx-imgBorder"]
    > ![Aggiungere l'account aziendale o dell'istituto di istruzione](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png "Aggiunta di un account aziendale o dell'istituto di istruzione come account alternativo nella sottoscrizione.")

5. Usare l'account aziendale o dell'istituto di istruzione per accedere ad Azure DevOps (https://{account}.visualstudio.com).

L'account alternativo viene aggiunto alla sottoscrizione di Visual Studio, consentendo a entrambe le identità di sfruttare i vantaggi della sottoscrizione che richiedono l'accesso con l'account alternativo (IDE, Azure DevOps e Azure).

## <a name="faq"></a>Domande frequenti

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>D: Perché Azure DevOps non riconosce un utente come sottoscrittore di Visual Studio?

R: Azure DevOps dovrebbe riconoscere automaticamente la sottoscrizione quando si esegue l'accesso con l'identità primaria o alternativa. In caso contrario, è possibile:

* Verificare di avere una sottoscrizione Visual Studio che [include](vs-azure-devops.md#eligibility) Azure DevOps come vantaggio.

* Assicurarsi di usare un account di accesso o un'identità che rappresenta l'identità primaria o alternativa per la sottoscrizione di Visual Studio.

* Visitare il [portale Visual Studio sottoscrittori](https://my.visualstudio.com?wt.mc_id=o~msft~docs) almeno una volta prima di accedere a Azure DevOps.

Se Azure DevOps non riconosce ancora la sottoscrizione, contattare il [supporto tecnico di Azure DevOps](https://azure.microsoft.com/support/devops/).

## <a name="resources"></a>Risorse
[Visual Studio sottoscrizioni](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi 
Per altre informazioni sull'uso di Azure, Azure DevOps o Visual Studio IDE, vedere queste risorse:
- [Azure](vs-azure.md)
- [Azure DevOps](vs-azure-devops.md)
- [Visual Studio](vs-ide-benefit.md)