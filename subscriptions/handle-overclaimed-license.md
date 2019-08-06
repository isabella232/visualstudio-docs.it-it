---
title: Gestire le licenze sovrallocate | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Informazioni per gli amministratori su come risolvere il problema relativo alle sottoscrizioni sovrallocate
ms.openlocfilehash: 924f6fb2c513d70aefd28c1d4ff18d1af62178c2
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605516"
---
# <a name="overallocated-subscriptions"></a>Sottoscrizioni sovrassegnate
Talvolta gli ordini vengono modificati dopo che sono stati aggiunti dei sottoscrittori, con un conseguente numero di sottoscrizioni assegnate superiore alle licenze detenute dall'azienda. Questo processo è noto come "sovrallocazione".  In questo caso, la scheda Sottoscrittori mostra un avviso e presenta informazioni aggiuntive sul numero di sottoscrizioni sovrallocate.

> [!NOTE]
> La sovrallocazione non è consentita nei programmi Open License.  Inoltre, altri programmi possono visualizzare queste informazioni nel portale in modo diverso.
>
> [!div class="mx-imgBorder"]
> ![Avviso di sottoscrizioni richieste in eccedenza](_img/over-claimed/over-claimed-alert.png)

## <a name="resolve-overallocated-subscriptions"></a>Risolvere il problema di sovrallocazione di sottoscrizioni
Esistono diversi modi per risolvere questo problema:
- Contattare il rivenditore per acquistare sottoscrizioni aggiuntive.
- Attendere fino al periodo di true-up annuale e pagare per le sottoscrizioni sovrallocate nel momento specifico. 
- Modificare alcune assegnazioni di sottoscrizioni.  Questa operazione non eliminerà la necessità di pagare in base al periodo di true-up annuale, in quanto il true-up si basa sul numero massimo di sottoscrizioni assegnate in qualsiasi momento durante l'anno.

## <a name="billing-and-true-up"></a>Fatturazione e true-up
Se l'organizzazione dispone di un contratto Enterprise Agreement (EA), gli amministratori hanno la facoltà di assegnare le sottoscrizioni senza acquistarle e di pagarle in un secondo momento attraverso un processo di riconciliazione noto come "true-up".  In caso di sovrassegnazione, con il processo true-up verrà addebitato all'organizzazione il numero massimo di sottoscrizioni assegnate agli utenti.  Questo accade anche se, al momento del true-up, l'organizzazione non ha più il numero massimo di sottoscrizioni assegnate.  Per altre informazioni su come monitorare l'utilizzo massimo di sottoscrizioni, visitare l'argomento [Utilizzo massimo](maximum-usage.md).

> [!Important]
> Se le sottoscrizioni di Visual Studio con GitHub Enterprise sono assegnate dagli amministratori delle sottoscrizioni di Visual Studio e non ne è mai stata acquistata una, queste non risulteranno visibili agli amministratori di GitHub Enterprise dell'organizzazione. Per fare in modo che le sottoscrizioni di GitHub Enterprise siano visibili, è necessario effettuare un acquisto che includa **almeno una** sottoscrizione di Visual Studio Professional con GitHub Enterprise o di Visual Studio Enterprise con GitHub Enterprise la prima volta che le sottoscrizioni vengono assegnate.
>
> È responsabilità del cliente rimanere conforme ai requisiti di licenza per questa sottoscrizione verificando che per ogni sottoscrizione di GitHub assegnata sia presente una sottoscrizione di Visual Studio con GitHub corrispondente assegnata nel portale di gestione.

## <a name="next-steps"></a>Passaggi successivi
- Altre informazioni sulla [Gestione delle sottoscrizioni di Visual Studio con GitHub Enterprise](assign-github.md).
- Per assistenza per le vendite, le sottoscrizioni, gli account e la fatturazione per le sottoscrizioni di Visual Studio, contattare il [servizio di supporto per le sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/) di Visual Studio.
