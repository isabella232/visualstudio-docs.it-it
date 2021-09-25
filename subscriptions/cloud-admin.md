---
title: Configurazione degli amministratori per le sottoscrizioni Visual Studio mensili | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/21/2021
ms.topic: how-to
description: Configurazione degli amministratori per le sottoscrizioni mensili
ms.openlocfilehash: aaa847aab4b56591d2fdd070192d14c62c33d96c
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427575"
---
# <a name="set-up-admins-for-visual-studio-monthly-subscriptions"></a>Configurare gli amministratori per le Visual Studio mensili

Visual Studio le sottoscrizioni mensili vengono gestite dagli amministratori. Gli amministratori possono assegnare le sottoscrizioni, modificare le assegnazioni, aggiungere o eliminare le sottoscrizioni ed eseguire altre attività di gestione delle sottoscrizioni.

## <a name="the-azure-subscription-owner-is-the-first-admin"></a>Il proprietario della sottoscrizione di Azure è il primo amministratore

Quando si acquistano Visual Studio mensili, il proprietario della sottoscrizione di Azure usata per effettuare gli acquisti viene automaticamente configurato come amministratore per tali sottoscrizioni.

È possibile acquistare sottoscrizioni mensili [tramite Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)o contattando un Cloud Solution Provider. Se si acquista tramite Visual Studio Marketplace, al termine dell'esperienza di acquisto, viene offerta la possibilità di gestire gli utenti. Se si sceglie questa opzione, verrà visualizzato il portale Sottoscrizioni di Visual Studio administration - [https://manage.visualstudio.com](https://manage.visualstudio.com) .

Dopo aver acquistato le sottoscrizioni, è possibile visitare il [portale di amministrazione](https://manage.visualstudio.com) in qualsiasi momento. È sufficiente accedere al portale e selezionare la sottoscrizione di Azure appropriata nell'angolo in alto a sinistra.

In quanto proprietario della sottoscrizione di Azure usata per acquistare le sottoscrizioni mensili, è anche possibile assegnare altri amministratori.

## <a name="add-admins"></a>Aggiungi amministratori

Per aggiungere amministratori:

1. Connessione alla portale di Azure in [portal.azure.com](https://portal.azure.com).
2. Accedere con l'account usato per acquistare le sottoscrizioni Visual Studio mensili.
3. In **Servizi di Azure** scegliere Gestione dei costi e **fatturazione.**
   > [!div class="mx-imgBorder"]
   > ![Scegliere Gestione dei costi e fatturazione in Servizi di Azure](_img/cloud-admin/azure-cost-billing.png "Scegliere Gestione costi dal gruppo Servizi di Azure")
4. **Nell'elenco Sottoscrizioni** personali scegliere la sottoscrizione di Azure usata per effettuare l'acquisto.
   > [!div class="mx-imgBorder"]
   > ![Scegliere la sottoscrizione](_img/cloud-admin/subscription-list.png "Scegliere la sottoscrizione di Azure da usare per effettuare l'acquisto.")
5. Fare **clic su Controllo di accesso (IAM)**, che si trova nella parte superiore dell'elenco nel riquadro di spostamento sinistro.
6. Fare clic **sulla** scheda Aggiungi nella parte superiore della pagina.
7. Fare clic **su Aggiungi assegnazione di ruolo**.
   > [!div class="mx-imgBorder"]
   > ![Scegliere Controllo di accesso, Aggiungi, Aggiungi assegnazione di ruolo](_img/cloud-admin/access-control-add.png "Scegliere Controllo di accesso dall'elenco a sinistra, quindi scegliere Aggiungi.")
8. Nel riquadro a destra fare clic sull'elenco a discesa **Ruolo** nella parte superiore del riquadro, scorrere verso il basso e selezionare **Amministratore Accesso utenti**.
9. Nell'elenco di utenti scorrere verso il basso fino all'utente che si vuole impostare come amministratore e selezionarlo. 
   > [!div class="mx-imgBorder"]
   > ![Scegliere Ruolo, Amministratore Accesso utenti](_img/cloud-admin/add-role-user-access-admin.png "Scegliere Ruolo, selezionare Amministratore Accesso utenti e quindi selezionare il nome dell'utente per renderlo amministratore.")
10. Fare clic su **Save** (Salva).
11. Fare clic sulla scheda **Assegnazioni ruolo** per verificare che l'utente selezionato sia ora visualizzato come Amministratore Accesso utenti.

Il nuovo amministratore può ora accedere al portale di [amministrazione,](https://manage.visualstudio.com)selezionare la stessa sottoscrizione di Azure usata per acquistare le sottoscrizioni mensili dall'elenco nell'angolo superiore sinistro della pagina e iniziare a gestire tali sottoscrizioni.

> [!NOTE]
> Se vengono visualizzati utenti con accesso per modificare le sottoscrizioni mensili che non sono state stabilite come amministratori, potrebbero avere ruoli nella sottoscrizione di Azure sottostante che consentono loro di gestire le sottoscrizioni. Questi ruoli includono: proprietario, collaboratore, amministratore del servizio o co-amministratore. Per altre informazioni, vedere Aggiungere [responsabili della fatturazione.](/azure/devops/organizations/billing/add-backup-billing-managers)

Per informazioni sulle sottoscrizioni Visual Studio mensili, vedere Panoramica [in](vscloud-overview.md) Acquisto di sottoscrizioni. Per acquistare Visual Studio sottoscrizioni mensili, visitare Visual Studio Marketplace all'indirizzo [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription) .

## <a name="resources"></a>Risorse
- [Supporto delle sottoscrizioni](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulla gestione Visual Studio sottoscrizioni.
- [Assegnare sottoscrizioni singole](assign-license.md)
- [Assegnare più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)