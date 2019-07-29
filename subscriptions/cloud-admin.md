---
title: Configurazione degli amministratori per le sottoscrizioni cloud | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: lank
ms.date: 07/17/2019
ms.topic: conceptual
description: Configurazione degli amministratori per le sottoscrizioni cloud
ms.openlocfilehash: 62a350e6061444e3c75878dfd89739011c4641d5
ms.sourcegitcommit: 57866dd72fd0e15ce61128df70729b427a2d02eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315210"
---
# <a name="set-up-administrators-for-visual-studio-cloud-subscriptions"></a>Configurare gli amministratori per le sottoscrizioni cloud di Visual Studio

Le sottoscrizioni cloud di Visual Studio sono gestite dagli amministratori. Gli amministratori possono assegnare le sottoscrizioni, modificare le assegnazioni, aggiungere o eliminare le sottoscrizioni ed eseguire altre attività di gestione delle sottoscrizioni.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Il proprietario della sottoscrizione di Azure è il primo amministratore

Quando si acquistano sottoscrizioni cloud di Visual Studio, il proprietario della sottoscrizione di Azure usata per effettuare gli acquisti viene configurato automaticamente come amministratore delle sottoscrizioni.

È possibile acquistare sottoscrizioni cloud tramite [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) o contattando un Cloud Solution Provider. Se si acquista tramite Visual Studio Marketplace, al termine dell'esperienza di acquisto, viene offerta la possibilità di gestire gli utenti. Se si sceglie questa opzione, viene visualizzato il portale di amministrazione delle sottoscrizioni di Visual Studio - [https://manage.visualstudio.com](https://manage.visualstudio.com).

Dopo aver acquistato le sottoscrizioni, è possibile visitare il [portale di amministrazione](https://manage.visualstudio.com) in qualsiasi momento. È sufficiente accedere al portale e selezionare la sottoscrizione di Azure appropriata nell'angolo superiore sinistro.

Il proprietario della sottoscrizione di Azure usata per l'acquisto delle sottoscrizioni cloud può anche assegnare altri amministratori.

## <a name="add-administrators"></a>Aggiungere gli amministratori

Per aggiungere gli amministratori:

1. Connettersi al portale di Azure all'indirizzo [portal.azure.com](https://portal.azure.com).
2. Accedere con l'account usato per acquistare le sottoscrizioni cloud di Visual Studio.
3. Nel riquadro di spostamento di sinistra scorrere verso il basso su **Gestione costi + Fatturazione**.
4. Nell'elenco **Sottoscrizioni personali** scegliere la sottoscrizione di Azure usata per effettuare l'acquisto.
5. Fare clic su **Controllo dell'accesso** nella parte superiore dell'elenco nel riquadro di spostamento di sinistra.
6. Fare clic sulla scheda **Aggiungi** nella parte superiore della pagina.
7. Fare clic su **Aggiungi assegnazione ruolo**.
8. Nel riquadro a destra fare clic sull'elenco a discesa **Ruolo** nella parte superiore del riquadro, scorrere verso il basso e selezionare **Amministratore Accesso utenti**.
9. Nell'elenco di utenti scorrere verso il basso fino all'utente che si vuole impostare come amministratore e selezionarlo. 
10. Fare clic su **Salva**.
11. Fare clic sulla scheda **Assegnazioni ruolo** per verificare che l'utente selezionato sia ora visualizzato come Amministratore Accesso utenti.

Il nuovo amministratore può ora accedere al [portale di amministrazione](https://manage.visualstudio.com), selezionare la stessa sottoscrizione di Azure usata per l'acquisto delle sottoscrizioni cloud dall'elenco nell'angolo superiore sinistro della pagina e iniziare a gestire le sottoscrizioni.

> [!NOTE]
> Se si visualizzano utenti con autorizzazioni per la modifica delle sottoscrizioni cloud dell'utente che l'utente stesso non ha impostato come amministratori, è possibile che tali utenti abbiano ruoli nella sottoscrizione di Azure sottostante che consentono loro la gestione delle sottoscrizioni. Tali ruoli includono: proprietario, collaboratore, amministratore dei servizi o coamministratore. Per altre informazioni, visitare [Billing management](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts) (Gestione della fatturazione).

Per informazioni sulle sottoscrizioni cloud di Visual Studio, vedere [Panoramica](vscloud-overview.md) in Acquisto di sottoscrizioni. Per acquistare sottoscrizioni cloud di Visual Studio, visitare Visual Studio Marketplace all'indirizzo [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).
