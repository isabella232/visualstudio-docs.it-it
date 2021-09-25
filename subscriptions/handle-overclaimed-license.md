---
title: Gestire le licenze sovraallocato in Visual Studio sottoscrizioni | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 05/18/2021
ms.topic: conceptual
description: Informazioni su come gli amministratori possono risolvere le sottoscrizioni sovra allocate
ms.openlocfilehash: bb545d6bef8f50e1548e31ad6db73a84e6804f53
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429513"
---
# <a name="over-allocated-subscriptions"></a>Sottoscrizioni sovraallocato
Talvolta gli ordini vengono modificati dopo che sono stati aggiunti dei sottoscrittori, con un conseguente numero di sottoscrizioni assegnate superiore alle licenze detenute dall'azienda. Questa operazione è detta "sovraallocazione".  

Per visualizzare le allocazioni delle sottoscrizioni, fare clic sull'icona in alto a sinistra per aprire il riquadro allocazioni.  

> [!NOTE]
> Le sovraallocazione non sono consentite nei programmi Open License.  Inoltre, altri programmi possono visualizzare queste informazioni nel portale in modo diverso.
>
> [!div class="mx-imgBorder"]
> ![Avviso di sottoscrizioni richieste in eccedenza](_img/over-claimed/over-claimed-alert.png "Il numero di sovraallocazione è elencato nella panoramica ed è rappresentato dalla barra con hash nel grafico per ogni tipo di sottoscrizione.")

Si noti che la visualizzazione usa una barra con hash per indicare sottoscrizioni sovraallocate.  Il numero di sovraallocazione in tutti i tipi di sottoscrizione è incluso nella sezione Panoramica nella parte superiore e ogni livello di sottoscrizione visualizza anche il proprio stato di allocazione.  

## <a name="receive-notifications-when-over-allocations-occur"></a>Ricevere notifiche quando si verificano sovraallocazione
È possibile designare un indirizzo di posta elettronica per ricevere notifiche quando si verificano sovrassegnazioni, nonché impostare una soglia che deve essere superata prima dell'invio delle notifiche.  Altre informazioni [sull'impostazione delle preferenze per i contratti](admin-preferences.md) nel portale di amministrazione.

## <a name="resolve-over-allocated-subscriptions"></a>Risolvere le sottoscrizioni sovraallocato
Esistono diversi modi per risolvere le sovraallocazione:
- Contattare il rivenditore per acquistare sottoscrizioni aggiuntive.
- Attendere fino al periodo di completamento annuale e pagare le sottoscrizioni sovra allocate a quel punto. 
- Modificare alcune assegnazioni di sottoscrizioni.  Questa operazione non eliminerà la necessità di pagare in base al periodo di true-up annuale, in quanto il true-up si basa sul numero massimo di sottoscrizioni assegnate in qualsiasi momento durante l'anno.

## <a name="billing-and-true-up"></a>Fatturazione e true-up
Se l'organizzazione dispone di un contratto Enterprise Agreement (EA), gli amministratori hanno la facoltà di assegnare le sottoscrizioni senza acquistarle e di pagarle in un secondo momento attraverso un processo di riconciliazione noto come "true-up".  Quando si esegue l'overalloc, all'organizzazione verrà addebitato il numero massimo di sottoscrizioni assegnate agli utenti durante il "true-up".  Questo accade anche se, al momento del true-up, l'organizzazione non ha più il numero massimo di sottoscrizioni assegnate.  Per altre informazioni su come monitorare l'utilizzo massimo di sottoscrizioni, visitare l'argomento [Utilizzo massimo](maximum-usage.md).


## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Altre informazioni sulla gestione delle [Visual Studio con GitHub Enterprise](assign-github.md).
- Per assistenza su vendite, sottoscrizioni, account e fatturazione Sottoscrizioni di Visual Studio, contattare il supporto Visual Studio [sottoscrizioni.](https://aka.ms/vsadminhelp)