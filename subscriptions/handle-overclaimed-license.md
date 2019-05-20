---
title: Gestione delle licenze richieste in eccedenza | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 02/13/2018
ms.topic: conceptual
description: Informazioni su come gli amministratori possono risolvere il problema delle sottoscrizioni richieste in eccedenza
searchscope: VS Subscription
ms.openlocfilehash: 6217dcd3cef9a65db3e45ba76f57167f47535671
ms.sourcegitcommit: bd519d1da375e374016f94a44c295d3253f61a8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945131"
---
# <a name="overallocated-subscriptions"></a>Sottoscrizioni sovrassegnate

Talvolta gli ordini vengono modificati dopo che sono stati aggiunti dei sottoscrittori, con un conseguente numero di sottoscrizioni assegnate superiore alle licenze detenute dall'azienda. In questo caso, la scheda Sottoscrittori mostra un avviso e presenta informazioni aggiuntive.

> [!NOTE]
> Gli scenari con richieste in eccedenza non sono consentiti nei programmi Open License.  Inoltre, altri programmi possono visualizzare queste informazioni nel portale in modo diverso.
>
> [!div class="mx-imgBorder"]
> ![Avviso di sottoscrizioni richieste in eccedenza](_img/over-claimed/over-claimed-alert.png)

## <a name="resolving-overallocated-subscriptions"></a>Risoluzione delle sottoscrizioni sovrassegnate

Per risolvere le licenze sovrassegnate:

1. Fare clic sul testo dell'avviso. Verrà visualizzato un elenco filtrato dei sottoscrittori assegnati al livello di sottoscrizione e la data di scadenza di ciò che è stato richiesto in eccedenza. 

2. Rimuovere i sottoscrittori in base alle esigenze per correggere le licenze richieste in eccedenza. 

3. La panoramica sul lato sinistro della pagina verrà aggiornata per mostrare la conformità raggiunta e tutte le notifiche per le richieste in eccedenza non saranno più visualizzate. 

## <a name="billing-and-true-up"></a>Fatturazione e true-up

Se l'organizzazione dispone di un contratto Enterprise Agreement (EA), gli amministratori hanno la facoltà di assegnare le sottoscrizioni senza acquistarle e di pagarle in un secondo momento attraverso un processo di riconciliazione noto come "true-up".  In caso di sovrassegnazione, con il processo true-up verrà addebitato all'organizzazione il numero massimo di sottoscrizioni assegnate agli utenti.  Questo accade anche se, al momento del true-up, l'organizzazione non ha più il numero massimo di sottoscrizioni assegnate.  Per altre informazioni su come monitorare l'utilizzo massimo di sottoscrizioni, visitare l'argomento [Utilizzo massimo](maximum-usage.md).

> [!Important]
> Se le sottoscrizioni di Visual Studio con GitHub Enterprise sono assegnate dagli amministratori delle sottoscrizioni di Visual Studio e non ne è mai stata acquistata una, queste non risulteranno visibili agli amministratori di GitHub Enterprise dell'organizzazione. Per fare in modo che le sottoscrizioni di GitHub Enterprise siano visibili, è necessario effettuare un acquisto che includa **almeno una** sottoscrizione di Visual Studio Professional con GitHub Enterprise o di Visual Studio Enterprise con GitHub Enterprise la prima volta che le sottoscrizioni vengono assegnate.  
>
> È responsabilità del cliente rimanere conforme ai requisiti di licenza per questa sottoscrizione verificando che per ogni sottoscrizione di GitHub assegnata sia presente una sottoscrizione di Visual Studio con GitHub corrispondente assegnata nel portale di gestione.


Altre informazioni sulla [Gestione delle sottoscrizioni di Visual Studio con GitHub Enterprise](assign-github.md).

## <a name="support-resources"></a>Risorse di supporto
-  Per assistenza per le vendite, le sottoscrizioni, gli account e la fatturazione per le sottoscrizioni di Visual Studio, contattare il [servizio di supporto per le sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/) di Visual Studio.