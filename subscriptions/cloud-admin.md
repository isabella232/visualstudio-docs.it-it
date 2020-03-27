---
title: Impostazione degli amministratori per gli abbonamenti mensili Documenti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/03/2020
ms.topic: conceptual
description: Impostazione degli amministratori per gli abbonamenti mensili
ms.openlocfilehash: c9a1303d4111f0ec4a0c1249a25e49fc40cf26de
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232662"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Configurare gli amministratori per le sottoscrizioni mensili di Visual StudioSet up administrators for Visual Studio monthly subscriptions

Le sottoscrizioni mensili di Visual Studio sono gestite dagli amministratori. Gli amministratori possono assegnare le sottoscrizioni, modificare le assegnazioni, aggiungere o eliminare le sottoscrizioni ed eseguire altre attività di gestione delle sottoscrizioni.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Il proprietario della sottoscrizione di Azure è il primo amministratore

Quando si acquistano sottoscrizioni mensili di Visual Studio, come proprietario della sottoscrizione di Azure usata per effettuare gli acquisti, viene configurata automaticamente come amministratore per tali sottoscrizioni.

È possibile acquistare abbonamenti mensili tramite [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)o contattando un provider di soluzioni cloud. Se si acquista tramite Visual Studio Marketplace, al termine dell'esperienza di acquisto, viene offerta la possibilità di gestire gli utenti. La scelta di questa opzione consente di [https://manage.visualstudio.com](https://manage.visualstudio.com)passare al portale di amministrazione delle sottoscrizioni di Visual Studio - .

Dopo aver acquistato le sottoscrizioni, è possibile visitare il [portale di amministrazione](https://manage.visualstudio.com) in qualsiasi momento. È sufficiente accedere al portale e selezionare la sottoscrizione di Azure appropriata nell'angolo superiore sinistro.

In qualità di proprietario della sottoscrizione di Azure usata per acquistare le sottoscrizioni mensili, è anche possibile assegnare altri amministratori.

## <a name="add-administrators"></a>Aggiungere amministratori

Per aggiungere gli amministratori:

1. Connettersi al portale di Azure all'indirizzo [portal.azure.com](https://portal.azure.com).
2. Accedere con l'account utilizzato per acquistare le sottoscrizioni mensili di Visual Studio.
3. In **Servizi**di Azure scegliere Gestione costi **e fatturazione**.
   > [!div class="mx-imgBorder"]
   > ![Scegliere Gestione costi e fatturazione in Servizi di AzureChoose Cost Management - Billing under Azure services](_img/cloud-admin/azure-cost-billing.png)
4. Nell'elenco **Sottoscrizioni personali** scegliere la sottoscrizione di Azure usata per effettuare l'acquisto.
   > [!div class="mx-imgBorder"]
   > ![Scegliere la sottoscrizione](_img/cloud-admin/subscription-list.png)
5. Fare clic su Controllo di accesso **(IAM)**, che si trova nella parte superiore dell'elenco nel riquadro di spostamento sinistro.
6. Fare clic sulla scheda **Aggiungi** nella parte superiore della pagina.
7. Fare clic su **Aggiungi assegnazione ruolo**.
   > [!div class="mx-imgBorder"]
   > ![Scegliere Controllo di accesso, Aggiungi, Aggiungi assegnazione ruolo](_img/cloud-admin/access-control-add.png)
8. Nel riquadro a destra fare clic sull'elenco a discesa **Ruolo** nella parte superiore del riquadro, scorrere verso il basso e selezionare **Amministratore Accesso utenti**.
9. Nell'elenco di utenti scorrere verso il basso fino all'utente che si vuole impostare come amministratore e selezionarlo. 
   > [!div class="mx-imgBorder"]
   > ![Scegliere Ruolo, Amministratore di accesso utente](_img/cloud-admin/add-role-user-access-admin.png)
10. Fare clic su **Salva**.
11. Fare clic sulla scheda **Assegnazioni ruolo** per verificare che l'utente selezionato sia ora visualizzato come Amministratore Accesso utenti.

Il nuovo amministratore può ora accedere al [portale di amministrazione](https://manage.visualstudio.com), selezionare la stessa sottoscrizione di Azure usata per acquistare le sottoscrizioni mensili dall'elenco nell'angolo superiore sinistro della pagina e iniziare a gestire tali sottoscrizioni.

> [!NOTE]
> Se viene visualizzato utenti con accesso per modificare le sottoscrizioni mensili che non sono state stabilite come amministratori, è possibile che dispongano di ruoli nella sottoscrizione di Azure sottostante che consentono loro di gestire le sottoscrizioni. Tali ruoli includono: proprietario, collaboratore, amministratore del servizio o coamministratore. Per ulteriori informazioni, vedere [Aggiungere responsabili della fatturazione](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Per informazioni sulle sottoscrizioni mensili di Visual Studio, vedere [Panoramica](vscloud-overview.md) in Acquisto di sottoscrizioni. Per acquistare abbonamenti mensili di Visual [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)Studio, visitare Visual Studio Marketplace all'indirizzo .

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione delle sottoscrizioni di Visual Studio.Learn more about managing Visual Studio subscriptions.
- [Assegnare singole sottoscrizioniAssign individual subscriptions](assign-license.md)
- [Assegnare più sottoscrizioniAssign multiple subscriptions](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Determinare l'utilizzo massimoDetermine maximum usage](maximum-usage.md)



