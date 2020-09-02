---
title: Gestire le licenze sovrallocate | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 03/03/2020
ms.topic: conceptual
description: Informazioni su come gli amministratori possono risolvere le sottoscrizioni con sovraallocazione
ms.openlocfilehash: b518dc9300862e7c39af0489734734668097ef9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "87453724"
---
# <a name="over-allocated-subscriptions"></a>Sottoscrizioni con allocazione eccessiva
Talvolta gli ordini vengono modificati dopo che sono stati aggiunti dei sottoscrittori, con un conseguente numero di sottoscrizioni assegnate superiore alle licenze detenute dall'azienda. Questa operazione viene definita "overallocazione".  

Per visualizzare le allocazioni di sottoscrizione, fare clic sull'icona in alto a sinistra per aprire il riquadro allocazioni.  

> [!NOTE]
> Le overallocazioni non sono consentite nei programmi di licenza Open.  Inoltre, altri programmi possono visualizzare queste informazioni nel portale in modo diverso.
>
> [!div class="mx-imgBorder"]
> ![Avviso di sottoscrizioni richieste in eccedenza](_img/over-claimed/over-claimed-alert.png "Il numero di allocazioni di eccedenze è elencato in panoramica ed è rappresentato dalla barra con hash nel grafico per ogni tipo di sottoscrizione.")

Si noti che nella visualizzazione viene utilizzata una barra con hash per indicare le sottoscrizioni con overallocazione.  Il numero di sovraallocazioni tra tutti i tipi di sottoscrizione è incluso nella sezione Panoramica nella parte superiore e ogni livello di sottoscrizione Visualizza anche il proprio stato di allocazione.  

## <a name="resolve-over-allocated-subscriptions"></a>Risolvere le sottoscrizioni allocate in eccesso
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

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Altre informazioni sulla [Gestione delle sottoscrizioni di Visual Studio con GitHub Enterprise](assign-github.md).
- Per assistenza in merito a vendite, sottoscrizioni, account e fatturazione per le sottoscrizioni di Visual Studio, contattare il [supporto delle sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/)di Visual Studio.