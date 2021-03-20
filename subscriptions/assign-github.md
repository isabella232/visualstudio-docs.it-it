---
title: Assegnare le sottoscrizioni di Visual Studio con GitHub Enterprise | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: Gestione delle sottoscrizioni nelle sottoscrizioni di Visual Studio con GitHub Enterprise
ms.openlocfilehash: c66932d9f0da5e7dbca6dccb8efc911b1453bb8e
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757659"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Gestire le sottoscrizioni di Visual Studio con GitHub Enterprise
I clienti con contratto Enterprise Agreement (EA) con Microsoft sono idonei per acquistare una nuova offerta di sottoscrizione che riunisce le sottoscrizioni di Visual Studio standard e GitHub Enterprise. Per i sottoscrittori di Visual Studio, si tratta di un modo semplice ed economico per acquisire GitHub Enterprise. 

Quando l'organizzazione acquista le sottoscrizioni di Visual Studio con GitHub Enterprise, ne viene effettuato il provisioning e la gestione in due parti.

## <a name="manage-visual-studio-subscriptions"></a>Gestire le sottoscrizioni di Visual Studio
Quando l'organizzazione acquista le sottoscrizioni di Visual Studio con GitHub Enterprise, viene eseguito immediatamente il provisioning della parte di Visual Studio delle sottoscrizioni e le sottoscrizioni sono disponibili per l'assegnazione e la gestione nel portale di [amministrazione delle sottoscrizioni](https://manage.visualstudio.com) di Visual Studio. Dopo aver assegnato una sottoscrizione di Visual Studio con GitHub Enterprise, il sottoscrittore riceverà un messaggio di posta elettronica che informa che può accedere alla sottoscrizione di Visual Studio all'indirizzo <https://my.visualstudio.com/subscriptions> .

Per ulteriori informazioni sulla gestione delle sottoscrizioni di Visual Studio, consultare gli argomenti seguenti:
- [Uso del portale di amministrazione](using-admin-portal.md)
- [Assegna sottoscrizioni](assign-license.md)
- [Modifica sottoscrizioni](edit-license.md)
- [Elimina sottoscrizioni](delete-license.md)
- [Sovrassegnazioni](handle-overclaimed-license.md)

> [!Important]
> Se le sottoscrizioni di Visual Studio con GitHub Enterprise vengono assegnate dagli amministratori delle sottoscrizioni di Visual Studio senza prima acquistare, GitHub non riceverà alcuna notifica che si vuole creare un account di GitHub Enterprise.  **Un acquisto di almeno un** È necessario effettuare la sottoscrizione di Visual Studio con GitHub Enterprise prima di assegnare le sottoscrizioni.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>Passaggio a Visual Studio con GitHub Enterprise
Se l'organizzazione acquista le sottoscrizioni di Visual Studio con GitHub Enterprise Bundle dopo l'assegnazione delle sottoscrizioni standard Visual Studio Enterprise e Visual Studio Professional, il portale di amministrazione contiene una funzionalità che consente di spostare i sottoscrittori esistenti nei Visual Studio Enterprise corrispondenti con GitHub Enterprise e/o Visual Studio Professional con le sottoscrizioni di GitHub Enterprise.  Ad esempio, i sottoscrittori con Visual Studio Professional sottoscrizioni si sposteranno Visual Studio Professional con le sottoscrizioni di GitHub Enterprise. Nel pannello "panoramica" della barra a sinistra viene visualizzato il riquadro seguente:

   > [!div class="mx-imgBorder"]
   > ![Pulsante Sposta ora](_img/assign-github/move-now.png "Fare clic su' sposta ora ' per aggiornare le sottoscrizioni di Visual Studio con le sottoscrizioni di GitHub Enterprise")

> [!IMPORTANT]
> Come indicato in precedenza, verranno mantenuti i dati del Sottoscrittore, la cronologia e l'ID sottoscrizione esistenti e tutti i vantaggi che hanno attivato non verranno interrotti a causa di questo spostamento.  
>
> Questa funzionalità viene distribuita in fasi e potrebbe non essere immediatamente disponibile nei contratti.

Quando si fa clic sul pulsante **sposta ora** , un pannello a comparsa presenta suggerimenti per lo spostamento delle sottoscrizioni aziendali e/o professionali:

   > [!div class="mx-imgBorder"]
   > ![Pannello di volo](_img/assign-github/fly-out.png)

In questo riquadro è possibile esaminare i sottoscrittori interessati e specificare se si desidera notificare loro la ricezione di una notifica di posta elettronica al termine dello spostamento.  Questo messaggio di posta elettronica informa gli abbonati che i loro vantaggi restano invariati e incoraggiano l'inizio della configurazione di una presenza in GitHub.  

Dopo aver fatto clic sul pulsante **Sposta tutti i sottoscrittori** , sarà possibile confermare le selezioni e attendere alcuni secondi per il completamento dello spostamento della sottoscrizione.  Se applicabile, sarà necessario eseguire questi passaggi per Professional ed Enterprise separatamente.  


## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>Come funziona il processo di configurazione di Visual Studio con GitHub Enterprise?
GitHub Enterprise viene configurato e gestito separatamente dalle sottoscrizioni di Visual Studio. In seguito a una sottoscrizione di Visual Studio con l'acquisto di GitHub Enterprise, viene avviato un processo di configurazione dell'account aziendale GitHub in parallelo con (ma separato da) la definizione di un accordo in [Manage.VisualStudio.com](https://manage.visualstudio.com). La creazione di questo account di GitHub Enterprise può richiedere del tempo. 

Dopo che l'azienda ha configurato un account di GitHub Enterprise, i sottoscrittori a cui sono state assegnate sottoscrizioni di Visual Studio con GitHub Enterprise riceveranno un messaggio di posta elettronica da GitHub che informa che le sottoscrizioni di Visual Studio sono state collegate. Quando i sottoscrittori ricevono questo messaggio di posta elettronica, possono rivolgersi all'amministratore dell'organizzazione GitHub per ricevere un invito all'organizzazione appropriata.

Per informazioni dettagliate sulla configurazione di GitHub Enterprise, fare riferimento alla [documentazione del Sottoscrittore](access-github.md).   

## <a name="manage-github-enterprise-subscriptions"></a>Gestire le sottoscrizioni di GitHub Enterprise
Quando si acquistano le sottoscrizioni di GitHub Enterprise, i partner GitHub con i clienti possono contribuire a creare e configurare le organizzazioni che accedono a GitHub e identificano gli amministratori.  Questi amministratori ricevono quindi una notifica che sono stati configurati come amministratori.  

Poiché questo processo è più complesso, potrebbe essere necessario diversi giorni dopo l'acquisto delle sottoscrizioni per l'installazione completa delle organizzazioni e degli amministratori.

GitHub è disponibile come GitHub.com basato su cloud o in versione locale come GitHub Enterprise Server.  I processi per la gestione delle due versioni variano.  GitHub offre diversi argomenti della guida e guide di amministrazione che consentono di gestire le sottoscrizioni di GitHub Enterprise.  Segue un elenco di collegamenti ad argomenti selezionati.  

## <a name="support-resources"></a>Risorse di supporto
- Altre informazioni sull'assegnazione di GitHub in [GitHub docs](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle)
- Trovare le risposte alle domande su un'ampia gamma di argomenti su GitHub nella [Guida di GitHub](https://help.github.com/en).
- Ottenere assistenza da altri utenti di GitHub nel [GitHub Community Forum](https://github.community/) (forum della Community GitHub).
- Per assistenza sull'amministrazione delle sottoscrizioni di Visual Studio, contattare il [supporto delle sottoscrizioni di Visual Studio](https://aka.ms/vsadminhelp).
- Per domande sull'IDE di Visual Studio, Azure DevOps Services o altri prodotti e servizi Visual Studio,  Visita il [supporto tecnico di Visual Studio](https://visualstudio.microsoft.com/support/).
- Ottenere [supporto tecnico](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) per GitHub Enterprise.   

## <a name="see-also"></a>Vedi anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione delle sottoscrizioni di Visual Studio.
- [Assegna singole sottoscrizioni](assign-license.md)
- [Assegna più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)

Per altre informazioni sulla gestione delle sottoscrizioni di Visual Studio con GitHub Enterprise, vedere il [portale di amministrazione delle sottoscrizioni](https://visualstudio.microsoft.com/subscriptions-administration/)di Visual Studio.