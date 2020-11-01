---
title: Configurazione degli amministratori per le sottoscrizioni mensili | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/03/2020
ms.topic: how-to
description: Configurazione degli amministratori per le sottoscrizioni mensili
ms.openlocfilehash: 8e102cb19d4f34c93392d89f9778c88460446666
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2020
ms.locfileid: "92904239"
---
# <a name="set-up-admins-for-visual-studio-monthly-subscriptions"></a>Configurare gli amministratori per le sottoscrizioni mensili di Visual Studio

Le sottoscrizioni mensili di Visual Studio sono gestite dagli amministratori. Gli amministratori possono assegnare le sottoscrizioni, modificare le assegnazioni, aggiungere o eliminare le sottoscrizioni ed eseguire altre attività di gestione delle sottoscrizioni.

## <a name="the-azure-subscription-owner-is-the-first-admin"></a>Il proprietario della sottoscrizione di Azure è il primo amministratore

Quando si acquistano sottoscrizioni mensili di Visual Studio, in qualità di proprietario della sottoscrizione di Azure usata per effettuare gli acquisti, viene automaticamente configurato come amministratore per tali sottoscrizioni.

È possibile acquistare sottoscrizioni mensili tramite il [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)o contattando un provider di soluzioni cloud. Se si acquista tramite Visual Studio Marketplace, al termine dell'esperienza di acquisto, viene offerta la possibilità di gestire gli utenti. La scelta di questa opzione consente di passare al portale di amministrazione delle sottoscrizioni di Visual Studio [https://manage.visualstudio.com](https://manage.visualstudio.com) .

Dopo aver acquistato le sottoscrizioni, è possibile visitare il [portale di amministrazione](https://manage.visualstudio.com) in qualsiasi momento. È sufficiente accedere al portale e selezionare la sottoscrizione di Azure appropriata nell'angolo superiore sinistro.

Il proprietario della sottoscrizione di Azure usato per acquistare le sottoscrizioni mensili può anche assegnare altri amministratori.

## <a name="add-admins"></a>Aggiungi amministratori

Per aggiungere amministratori:

1. Connettersi al portale di Azure all'indirizzo [Portal.Azure.com](https://portal.azure.com).
2. Accedere con l'account usato per acquistare le sottoscrizioni mensili di Visual Studio.
3. In **servizi di Azure** scegliere **Gestione costi e fatturazione** .
   > [!div class="mx-imgBorder"]
   > ![Scegli gestione costi e fatturazione in servizi di Azure](_img/cloud-admin/azure-cost-billing.png "Scegliere Gestione costi dal gruppo di servizi di Azure")
4. Nell'elenco **sottoscrizioni personali** scegliere la sottoscrizione di Azure usata per effettuare l'acquisto.
   > [!div class="mx-imgBorder"]
   > ![Scegliere la sottoscrizione](_img/cloud-admin/subscription-list.png "Scegliere la sottoscrizione di Azure che si vuole usare per effettuare l'acquisto.")
5. Fare clic su **controllo di accesso (IAM)** , che si trova nella parte superiore dell'elenco nel riquadro di spostamento a sinistra.
6. Fare clic sulla scheda **Aggiungi** nella parte superiore della pagina.
7. Fare clic su **Aggiungi assegnazione ruolo** .
   > [!div class="mx-imgBorder"]
   > ![Scegliere controllo di accesso, Aggiungi, Aggiungi assegnazione di ruolo](_img/cloud-admin/access-control-add.png "Scegliere controllo di accesso dall'elenco a sinistra, quindi scegliere Aggiungi.")
8. Nel riquadro a destra fare clic sull'elenco a discesa **Ruolo** nella parte superiore del riquadro, scorrere verso il basso e selezionare **Amministratore Accesso utenti** .
9. Nell'elenco di utenti scorrere verso il basso fino all'utente che si vuole impostare come amministratore e selezionarlo. 
   > [!div class="mx-imgBorder"]
   > ![Scegliere un ruolo, amministratore accesso utenti](_img/cloud-admin/add-role-user-access-admin.png "Scegliere ruolo, selezionare amministratore accesso utenti, quindi selezionare il nome dell'utente per impostarlo come amministratore.")
10. Fare clic su **Salva** .
11. Fare clic sulla scheda **Assegnazioni ruolo** per verificare che l'utente selezionato sia ora visualizzato come Amministratore Accesso utenti.

Il nuovo amministratore può ora accedere al portale di [Amministrazione](https://manage.visualstudio.com), selezionare la stessa sottoscrizione di Azure usata per acquistare le sottoscrizioni mensili dall'elenco nell'angolo superiore sinistro della pagina e iniziare a gestire tali sottoscrizioni.

> [!NOTE]
> Se gli utenti con accesso per modificare le sottoscrizioni mensili non sono state stabilite come amministratori, possono avere ruoli nella sottoscrizione di Azure sottostante che consentono loro di gestire le sottoscrizioni. Questi ruoli includono: proprietario, collaboratore, amministratore del servizio o coamministratore. Per ulteriori informazioni, vedere [Add Billing managers](/azure/devops/organizations/billing/add-backup-billing-managers).

Per informazioni sulle sottoscrizioni mensili di Visual Studio, vedere la [Panoramica](vscloud-overview.md) su come acquistare sottoscrizioni. Per acquistare sottoscrizioni mensili di Visual Studio, visitare la Visual Studio Marketplace all'indirizzo [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription) .

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione delle sottoscrizioni di Visual Studio.
- [Assegna singole sottoscrizioni](assign-license.md)
- [Assegna più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)