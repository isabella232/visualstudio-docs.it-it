---
title: Gestire le licenze sovraallocate nelle sottoscrizioni di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 12/02/2020
ms.topic: conceptual
description: Informazioni su come gli amministratori possono risolvere le sottoscrizioni con sovraallocazione
ms.openlocfilehash: c2876223d2aa4f8da5f267595a193a2fecc3ace2
ms.sourcegitcommit: 29099741fcf94a5aef2655ee16605728b8b9a0ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96537747"
---
# <a name="over-allocated-subscriptions"></a>Sottoscrizioni con allocazione eccessiva
Talvolta gli ordini vengono modificati dopo che sono stati aggiunti dei sottoscrittori, con un conseguente numero di sottoscrizioni assegnate superiore alle licenze detenute dall'azienda. Questa operazione viene definita "overallocazione".  

Per visualizzare le allocazioni delle sottoscrizioni, fare clic sull'icona in alto a sinistra per aprire il riquadro allocazioni.  

> [!NOTE]
> Le overallocazioni non sono consentite nei programmi di licenza Open.  Inoltre, altri programmi possono visualizzare queste informazioni nel portale in modo diverso.
>
> [!div class="mx-imgBorder"]
> ![Avviso di sottoscrizioni richieste in eccedenza](_img/over-claimed/over-claimed-alert.png "Il numero di allocazioni di eccedenze è elencato in panoramica ed è rappresentato dalla barra con hash nel grafico per ogni tipo di sottoscrizione.")

Si noti che nella visualizzazione viene utilizzata una barra con hash per indicare le sottoscrizioni con overallocazione.  Il numero di sovraallocazioni tra tutti i tipi di sottoscrizione è incluso nella sezione Panoramica nella parte superiore e ogni livello di sottoscrizione Visualizza anche il proprio stato di allocazione.  

## <a name="resolve-over-allocated-subscriptions"></a>Risolvere le sottoscrizioni allocate in eccesso
Esistono diversi modi per risolvere le eccedenze di allocazione:
- Contattare il rivenditore per acquistare sottoscrizioni aggiuntive.
- Attendere fino al periodo di tempo reale annuale e pagare per le sottoscrizioni in eccesso in quel momento. 
- Modificare alcune assegnazioni di sottoscrizioni.  Questa operazione non eliminerà la necessità di pagare in base al periodo di true-up annuale, in quanto il true-up si basa sul numero massimo di sottoscrizioni assegnate in qualsiasi momento durante l'anno.

## <a name="billing-and-true-up"></a>Fatturazione e true-up
Se l'organizzazione dispone di un contratto Enterprise Agreement (EA), gli amministratori hanno la facoltà di assegnare le sottoscrizioni senza acquistarle e di pagarle in un secondo momento attraverso un processo di riconciliazione noto come "true-up".  Quando si esegue l'overallocazione, all'organizzazione viene addebitato il numero massimo di sottoscrizioni assegnate agli utenti durante il "vero".  Questo accade anche se, al momento del true-up, l'organizzazione non ha più il numero massimo di sottoscrizioni assegnate.  Per altre informazioni su come monitorare l'utilizzo massimo di sottoscrizioni, visitare l'argomento [Utilizzo massimo](maximum-usage.md).


## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Altre informazioni sulla gestione delle [sottoscrizioni di Visual Studio con GitHub Enterprise](assign-github.md).
- Per assistenza in merito a vendite, sottoscrizioni, account e fatturazione per le sottoscrizioni di Visual Studio, contattare il [supporto delle sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/)di Visual Studio.